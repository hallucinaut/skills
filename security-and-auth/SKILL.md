---
name: security-and-auth
description: "Implement authentication, authorization, and security auditing. Protect applications against common vulnerabilities and ensure data integrity through validation."
---

# Security and Authentication Skill

Secure applications by implementing robust identity management, access controls, and proactive security measures.

## When to Use

Use this skill when the user wants to:
- Implement authentication (Login, Register, OAuth, JWT, Sessions)
- Implement authorization (RBAC, ABAC, Permission-based)
- Perform security auditing and vulnerability assessments
- Implement request/response validation to prevent injection attacks
- Secure an application against OWASP Top 10 vulnerabilities

## Core Concepts

### 1. Authentication (AuthN)
- **Goal**: Verify the identity of a user or service.
- **Methods**:
    - **Passwords**: Hashed and salted using modern algorithms like Argon2 or bcrypt.
    - **Tokens**: Stateless (JWT) for scalability, or state-based (Session Cookies) for centralized control.
    - **Social/External**: OAuth 2.0 and OpenID Connect (Google, GitHub, etc.) for federated identity.
    - **Multi-Factor Authentication (MFA)**: Adding an extra layer of security (TOTP, SMS, WebAuthn).

### 2. Authorization (AuthZ)
- **Goal**: Determine what an authenticated user is allowed to do.
- **Models**:
    - **RBAC (Role-Based Access Control)**: Assigning permissions to roles (e.g., `Admin`, `User`).
    - **ABAC (Attribute-Based Access Control)**: Decisions based on attributes of the user, resource, and environment (e.g., `Allow if User.Age > 18 and Resource.Type == 'Sensitive'`).
    - **ACL (Access Control Lists)**: Fine-grained permissions attached directly to specific resources.

### 3. Security Auditing & Defense
- **Input Validation**: Strict schema validation for all incoming data to prevent SQL Injection, XSS, and Command Injection.
- **Security Headers**: Using `Content-Security-Policy` (CSP), `X-Frame-Options`, `Strict-Transport-Security` (HSTS), etc.
- **Rate Limiting**: Preventing brute force and DoS attacks by limiting request frequency.
- **Audit Logs**: Recording critical security events (logins, permission changes, failed attempts) for forensic analysis.
- **Secrets Management**: Using environment variables or dedicated vaults (e.g., HashiCorp Vault, AWS Secrets Manager) instead of hardcoding keys.

## Implementation Examples

### RBAC vs ABAC (Conceptual)

**RBAC (Simple Role Check):**
```python
def delete_user(request, user_id):
    if request.user.role != 'admin':
        raise PermissionDenied()
    # Proceed with deletion...
```

**ABAC (Attribute-Based Check):**
```python
def access_document(request, document):
    if request.user.department == document.department and request.user.clearance >= 3:
        return True
    return False
```

## Best Practices

### Identity & Access Management
- **Never store plain-text passwords.** Use strong, modern hashing algorithms.
- **Use short-lived access tokens** (e.s. JWT) and longer-lived refresh tokens for a balance of security and UX.
- **Follow the Principle of Least Privilege**: Grant only the minimum necessary permissions required for a task.
- **Secure your cookies**: Always use `HttpOnly`, `Secure`, and `SameSite=Lax/Strict` flags.

### Defensive Programming
- **Fail Securely**: If an authentication or authorization check fails, default to denying access.
- **Sanitize everything**: Treat all external input (headers, body, query params) as untrusted.
- **Limit sensitive information in errors**: Don't leak database details, stack traces, or user existence in production error messages.

### Monitoring & Auditing
- **Log security-critical events**: Successful/failed logins, unauthorized access attempts, and privilege escalations.
- **Regularly audit permissions**: Periodically review user roles to prevent "Privilege Creep."

## Common Pitfalls

- **Hardcoding Secrets**: Storing API keys or database passwords in the source code.
- **Weak Password Policies**: Allowing simple, easily guessable passwords.
- **Broken Session Management**: Using predictable session IDs or not invalidating sessions on logout.
- **Insecure Error Messages**: Providing too much detail in error responses (e.g., "User 'admin' exists but password incorrect").
- **Ignoring Rate Limiting**: Leaving sensitive endpoints (like `/login`) open to brute force attacks.

## Deliverables

- Authentication system implementation (Login/Register/OAuth).
- Authorization logic (RBAC/ABAC/ACL).
- Input validation schemas for all sensitive endpoints.
- Security configuration (Headers, Cookies, Rate Limiting).
- Security audit report or checklist.
- Audit logging implementation.

## Quality Checklist

- [ ] Passwords are never stored in plain text and use strong hashing.
- [ ] Authentication is multi-factor aware (if required).
- [ ] Authorization checks are enforced on every sensitive endpoint.
- [ ] All user-provided input is strictly validated against a schema.
- [ ] Sensitive information is not leaked in error messages.
- [ ] Secrets (keys, tokens) are managed via environment variables or vaults.
- [ ] Security headers are configured correctly.
- [ ] Rate limiting is implemented on sensitive endpoints (e.g., login).
