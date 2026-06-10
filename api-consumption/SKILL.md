---
name: api-consumption
description: "Integrate with third-party APIs, webhooks, and external services. Handle authentication, rate limiting, retries, and error handling for robust integration."
---

# API Consumption Skill

Build robust integrations with third-party APIs and external services.

## When to Use

Use this skill when the user wants to:
- Integrate with third-party APIs (REST, GraphQL, SOAP)
- Implement OAuth 2.0, API Keys, or JWT-based authentication flows
- Handle webhook integrations and secure webhooks
- Build API clients and SDKs
- Implement rate limiting, backoff strategies, and circuit breakers
- Work with payment gateways (Stripe, PayPal)
- Integrate with SaaS platforms (Salesforce, HubSpot, Slack)
- Implement API retry logic

## Authentication Methods

### 1. API Keys
```python
import requests

headers = {
    'Authorization': f'Bearer {API_KEY}',
    'Content-Type': 'application/json'
}

response = requests.get('https://api.example.com/data', headers=headers)
```

### 2. OAuth 2.0
```python
from requests_oauthlib import OAuth2Session

# Authorization flow
oauth = OAuth2Session(client_id, redirect_uri=redirect_uri, scope=scope)
authorization_url, state = oauth.authorization_url('https://provider.com/oauth/authorize')

# Token exchange
token = oauth.fetch_token(
    'https://provider.com/oauth/token',
    client_secret=client_secret,
    authorization_response=callback_url
)

# API calls with token
response = oauth.get('https://api.provider.com/user')
```

### 3. JWT (JSON Web Tokens)
```python
import jwt
import time

def create_jwt_token(api_key, secret_key):
    payload = {
        'iss': api_key,
        'iat': int(time.time()),
        'exp': int(time.time()) + 3600
    }
    return jwt.encode(payload, secret_key, algorithm='HS256')

headers = {'Authorization': f'Bearer {create_jwt_token(API_KEY, SECRET)}'}
```

## Robust Client Implementation

### API Client with Retry and Error Handling
```python
import requests
from typing import Optional, Dict, Any
import time
from functools import wraps

class APIClient:
    def __init__(self, base_url: str, api_key: str, timeout: int = 30):
        self.base_url = base_url.rstrip('/')
        self.api_key = api_key
        self.timeout = timeout
        self.session = requests.Session()
        self.session.headers.update({
            'Authorization': f'Bearer {api_key}',
            'User-Agent': 'MyApp/1.0',
            'Accept': 'application/json'
        })

    def _retry_with_backoff(self, max_retries=3):
        def decorator(func):
            @wraps(func)
            def wrapper(*args, **kwargs):
                for attempt in range(max_retries):
                    try:
                        return func(*args, **kwargs)
                    except requests.exceptions.RequestException as e:
                        if attempt == max_retries - 1:
                            raise
                        wait_time = 2 ** attempt
                        time.sleep(wait_time)
            return wrapper
        return decorator

    @_retry_with_backoff(max_retries=3)
    def _request(self, method: str, endpoint: str, **kwargs) -> Dict[Any, Any]:
        url = f"{self.base_url}/{endpoint.lstrip('/')}"
        try:
            response = self.session.request(method, url, timeout=self.timeout, **kwargs)
            response.raise_for_status()
            return response.json()
        except requests.exceptions.HTTPError as e:
            if response.status_code == 429:
                retry_after = int(response.headers.get('Retry-After', 60))
                raise RateLimitError(f"Rate limited. Retry after {retry_after}s")
            raise APIError(f"API error: {e}")
        except Exception as e:
            raise APIError(f"Request error: {e}")

    def get(self, endpoint: str, params: Optional[Dict] = None) -> Dict:
        return self._request('GET', endpoint, params=params)

    def post(self, endpoint: str, data: Optional[Dict] = None) -> Dict:
        return self._request('POST', endpoint, json=data)

class APIError(Exception): pass
class RateLimitError(APIError): pass
```

## Webhook Integration

### Receiving Webhooks Securely
```python
import hmac
import hashlib
from flask import Flask, request, jsonify

app = Flask(__name__)
WEBHOOK_SECRET = 'your-webhook-secret'

def verify_webhook_signature(payload: bytes, signature: str) -> bool:
    expected_signature = hmac.new(
        WEBHOOK_SECRET.encode(),
        payload,
        hashlib.sha256
    ).hexdigest()
    return hmac.compare_digest(f'sha256={expected_signature}', signature)

@app.route('/webhooks/stripe', methods=['POST'])
def stripe_webhook():
    payload = request.get_data()
    signature = request.headers.get('Stripe-Signature')

    if not verify_webhook_signature(payload, signature):
        return jsonify({'error': 'Invalid signature'}), 401

    event = request.json
    # Process event...
    return jsonify({'received': True}), 200
```

## Best Practices

### Security
- **Never expose API keys** in code or logs. Use environment variables.
- **Verify webhook signatures** to prevent spoofing.
- **Use HTTPS only** for all API communication.

### Reliability
- **Implement exponential backoff** for retries.
- **Use circuit breakers** to prevent cascading failures.
- **Implement rate limiting** to respect external provider limits.
- **Log all interactions** for debugging and auditing.

### Performance
- **Use connection pooling** to reuse TCP connections.
- **Implement pagination** when dealing with large datasets.
- **Cache responses** when appropriate.

## Deliverables
- Robust API client with error handling and retries.
- Webhook listener with signature verification.
- Documentation of integration flows.
- Test suite with mocked API responses.

## Quality Checklist
- [ ] Authentication is secure (no keys in code).
- [ ] Retries with exponential backoff are implemented.
- [ ] Error handling is comprehensive (rate limits, timeouts).
- [ ] Webhook signatures are verified.
- [ ] Integration tests with mocked responses are present.
- [ ] All API calls are logged.
