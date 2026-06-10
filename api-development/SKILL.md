---
name: api-development
description: "Design and implement robust APIs (REST, GraphQL, gRPC). Focus on clear contracts, authentication, validation, and scalable architecture."
---

# API Development Skill

Design and build high-quality APIs that are secure, scalable, and easy to consume.

## When to Use

Use this skill when the user wants to:
- Design a new API (RESTful, GraphQL, or gRPC)
- Implement CRUD operations and business logic
- Create API documentation (OpenAPI/Swagger)
- Implement authentication and authorization for an API
- Add request/response validation
- Implement pagination and filtering for large datasets
- Handle API versioning

## API Paradigms

### 1. REST (Representational State Transfer)
- **Concept**: Resource-based, uses standard HTTP methods (GET, POST, PUT, DELETE, PATCH).
- **Best Practice**: Use meaningful URIs, standard HTTP status codes, and versioning (e.g., `/api/v1/`).

### 2. GraphQL
- **Concept**: Query language for APIs; clients request exactly the data they need.
- **Best Practice**: Use strong typing with schemas, implement query complexity limits, and use resolvers effectively.

### 3. gRPC
- **Concept**: High-performance, binary protocol using Protocol Buffers (Protobuf).
- **Best Practice**: Define strict service contracts, use streaming if necessary, and leverage interceptors for cross-cutting concerns.

## Core Components

### API Design Principles
- **Clear Contract**: Define request/response formats explicitly using schemas (OpenAPI, GraphQL Schema, Protobuf).
- **Consistent Naming**: Follow conventions (e.g., kebab-case for URIs, camelCase for JSON fields).
- **Error Handling**: Return descriptive error messages and appropriate HTTP status codes.
- **Versioning**: Always version your API to prevent breaking changes.

### Security
- **Authentication**: Implement JWT, OAuth2, or API Keys.
- **Authorization**: Use RBAC (Role-Based Access Control) or ABAC (Attribute-Based Access Control).
- **Validation**: Always validate incoming request payloads against a strict schema.
- **Rate Limiting**: Protect your API from abuse and DoS attacks.

### Performance
- **Pagination**: Use cursor-based or offset-based pagination for large collections.
- **Caching**: Use HTTP headers (Cache-Control) or server-side caching (Redis) to reduce load.
- **Compression**: Enable Gzip or Brotli to reduce payload size.

## Implementation Examples

### Standard Error Response Format
```json
{
  "error": {
    "code": "INVALID_INPUT",
    "message": "The 'email' field must be a valid email address.",
    "details": [
      {
        "field": "email",
        "issue": "format"
      }
    ]
  }
}
```

## Common Pitfalls

- **Inconsistent Error Responses**: Returning different error formats for different errors, making it hard for clients to handle them.
- **Lack of Versioning**: Making breaking changes to an existing API without versioning, which breaks all current clients.
- **Ignoring Pagination**: Returning massive datasets in a single response, causing performance issues and high latency.
- **Over-reliance on Client-Side Validation**: Relying only on the frontend for validation; always re-validate on the server.
- **Poor Error Messages**: Returning generic "Internal Server Error" messages without providing enough context for debugging (while still being secure).

## Deliverables

- Complete API implementation (REST, GraphQL, or gRPC)
- API documentation (OpenAPI/Swagger, GraphQL Schema, or Protobuf files)
- Input/Output validation schemas
- Error handling strategy
- Authentication and authorization implementation
- Integration tests for all endpoints

## Quality Checklist

- [ ] API follows a clear and consistent design pattern.
- [ ] Request/Response formats are explicitly documented.
- [ ] Input validation is performed on all incoming data.
- [ ] Proper HTTP status codes or error responses are used.
- [ ] Authentication and authorization are correctly implemented.
- [ ] API is versioned.
- [ ] Pagination is implemented for large datasets.
- [ ] Error messages are descriptive but don't leak sensitive info.
