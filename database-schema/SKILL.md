---
name: database-schema
description: "Design and document database schemas, migrations, relationships, and constraints. Use when creating database models, designing tables, defining relationships, or working with SQL/NoSQL databases."
---

# Database Schema Skill

Design scalable database schemas with proper relationships, constraints, and indexing strategies.

## When to Use

Use this skill when the user wants to:
- Design database tables and relationships
- Create schema migrations
- Define indexes and constraints
- Work with SQL or NoSQL databases
- Normalize or denormalize data models
- Design database migrations

## Schema Design Principles

- **Normalization**: Balance between normalization (reducing redundancy) and query performance (denormalization).
- **Naming conventions**: Use consistent, descriptive names (e.g., snake_case for PostgreSQL).
- **Primary keys**: Use natural or surrogate keys appropriately (UUID vs. Auto-incrementing Integer).
- **Foreign keys**: Define relationships clearly to enforce referential integrity.
- **Indexes**: Index columns used in `WHERE`, `JOIN`, `ORDER BY`, and `GROUP BY` clauses.
- **Constraints**: Enforce data integrity with `NOT NULL`, `UNIQUE`, `CHECK`, and `DEFAULT`.

## Database Types

- **SQL (Relational)**: PostgreSQL, MySQL, SQLite, SQL Server (Structured, ACID compliant).
- **NoSQL (Document/Key-Value)**: MongoDB, CouchDB, Redis (Flexible schema, high scalability).
- **NoSQL (Wide-column)**: Cassandra, ScyllaDB.
- **Time-series**: InfluxDB, TimescaleDB (Optimized for time-stamped data).
- **Search**: Elasticsearch, Meilisearch, PostgreSQL Full-Text Search.

## Implementation Examples

### SQL (PostgreSQL) - Relational Schema
```sql
CREATE TABLE users (
    id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
    email VARCHAR(255) UNIQUE NOT NULL,
    password_hash TEXT NOT NULL,
    created_at TIMESTAMP WITH TIME ZONE DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE posts (
    id SERIAL PRIMARY KEY,
    user_id UUID REFERENCES users(id) ON DELETE CASCADE,
    title VARCHAR(255) NOT NULL,
    content TEXT,
    published_at TIMESTAMP WITH TIME ZONE
);

-- Indexing for performance
CREATE INDEX idx_posts_user_id ON posts(user_id);
```

### NoSQL (MongoDB) - Document Schema
```json
// Users Collection
{
  "_id": "60d5ec...",
  "email": "user@example.com",
  "password_hash": "$2b$12$...",
  "profile": {
    "first_name": "John",
    "last_name": "Doe"
  },
  "created_at": "2023-01-01T00:00:00Z"
}

// Posts Collection (Denormalized for read performance)
{
  "_id": "70e6fd...",
  "user_id": "60d5ec...",
  "user_name": "John Doe", 
  "title": "My First Post",
  "content": "Hello world!",
  "tags": ["tech", "mongodb"],
  "created_at": "2023-01-05T10:00:00Z"
}
```

## Common Pitfalls

- **Over-indexing**: Too many indexes can slow down `INSERT`, `UPDATE`, and `DELETE` operations.
- **Ignoring Data Types**: Using `TEXT` when `VARCHAR(N)` or specific types (like `UUID` or `JSONB`) are more efficient.
- **Lack of Constraints**: Relying solely on application logic for data integrity instead of database constraints.
- **Not handling Migrations**: Changing schema manually in production without versioned migration scripts.
- **N+1 Query Problem**: Designing schemas/queries that require many subsequent round-trips to the DB.

## Deliverables

- Complete database schema design (ERD or text-based).
- Migration scripts (SQL, Alembic, Flyway, etc.).
- Indexing strategy and optimization plan.
- Data types and constraints definition.
- Query examples for complex joins or aggregations.

## Quality Checklist

- [ ] Primary keys are unique and efficient.
- [ ] Foreign keys enforce referential integrity.
- [ ] Indexes cover high-frequency query filters.
- [ ] Data types are optimal for storage and speed.
- [ ] Constraints (NOT NULL, UNIQUE) prevent invalid data.
- [ ] Migration scripts are versioned and reversible.
- [ ] Schema design is documented and easy to understand.
