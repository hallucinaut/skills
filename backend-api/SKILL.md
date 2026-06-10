---
name: backend-api
description: "Build RESTful APIs, GraphQL endpoints, and database-driven backend services. Use when designing APIs, implementing CRUD operations, handling authentication, or working with backend logic."
---

# Backend API Skill

Build robust, well-documented APIs with clear contracts, proper error handling, and scalable architecture.

## When to Use

Use this skill when the user wants to:
- Design or implement RESTful API endpoints
- Create GraphQL schemas and resolvers
- Handle authentication and authorization
- Work with database models and migrations
- Implement CRUD operations and data validation
- Create API documentation (OpenAPI/Swagger)

## API Design Principles

- **Clear contract**: Define request/response formats explicitly.
- **Consistent naming**: Use RESTful conventions (GET, POST, PUT, DELETE) or GraphQL query structure.
- **Versioning**: Include API version in path (e.g., `/api/v1/...`) to manage breaking changes.
- **Error handling**: Return meaningful HTTP status codes and structured error messages.
- **Documentation**: Include clear examples and describe all fields (using OpenAPI/Swagger).

## Implementation Examples

### FastAPI (Python) - RESTful API
```python
from fastapi import FastAPI, HTTPException, Depends
from pydantic import BaseModel

app = FastAPI()

class Item(BaseModel):
    name: str
    price: float

@app.post("/items/", response_model=Item)
async def create_item(item: Item):
    if item.price < 0:
        raise HTTPException(status_code=400, detail="Price cannot be negative")
    return item

@app.get("/items/{item_id}")
async def read_item(item_id: int):
    if item_id != 1:
        raise HTTPException(status_code=404, detail="Item not found")
    return {"item_id": item_id, "name": "Sample Item", "price": 10.0}
```

### Express (JavaScript/Node.js) - RESTful API
```javascript
const express = require('express');
const app = express();
app.use(express.json());

let items = [{ id: 1, name: 'Item One', price: 10.0 }];

// Get all items with pagination
app.get('/api/v1/items', (req, res) => {
  const page = parseInt(req.query.page) || 1;
  const limit = parseInt(req.query.limit) || 10;
  const startIndex = (page - 1) * limit;
  const endIndex = page * limit;

  const results = items.slice(startIndex, endIndex);
  res.json({
    page,
    limit,
    total: items.length,
    data: results
  });
});

// Create an item
app.post('/api/v1/items', (req, res) => {
  const { name, price } = req.body;
  if (!name || !price) {
    return res.status(400).json({ error: 'Name and price are required' });
  }
  const newItem = { id: items.length + 1, name, price };
  items.push(newItem);
  res.status(201).json(newItem);
});

app.listen(3000, () => console.log('Server running on port 3000'));
```

## Pagination and Filtering

- **Offset-based**: Use `limit` and `offset` (or `page`) for simple datasets.
- **Cursor-based**: Use a unique identifier (e.g., `after_id`) for high-frequency updates to avoid skipping items.
- **Filtering**: Implement query parameters for filtering (e.g., `/items?category=tech&sort=price_desc`).

## Common Pitfalls

- **Improper Error Handling**: Returning `200 OK` with an error message in the body instead of correct HTTP status codes.
- **Leaking Sensitive Info**: Including stack traces or database details in production error responses.
- **Lack of Rate Limiting**: Leaving endpoints open to brute force or DoS attacks.
- **Ignoring Pagination**: Returning massive datasets in a single response, causing performance issues.
- **Insecure Direct Object References (IDOR)**: Failing to check if the authenticated user has permission to access a specific resource ID.

## Deliverables

- Complete API implementation (Controllers, Services, Models).
- Request/response examples and schemas.
- Comprehensive error handling strategy.
- Input validation logic.
- Interactive API documentation (Swagger/OpenAPI).

## Quality Checklist

- [ ] Clear endpoint definitions following RESTful conventions.
- [ ] Proper use of HTTP status codes (200, 201, 400, 401, 403, 404, 500).
- [ ] Robust input validation for all request bodies and parameters.
- [ ] Error responses are structured and do not leak implementation details.
- [ ] API is documented with clear examples.
- [ ] Implementation includes pagination for large resource collections.
