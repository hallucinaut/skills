---
name: data-management
description: "Design, implement, and manage data lifecycles. Covers database schema design, migrations, caching, search, backups, and data analysis."
---

# Data Management Skill

Design and manage efficient, reliable, and scalable data architectures.

## When to Use

Use this skill when the user wants to:
- Design database schemas (Relational or NoSQL).
- Implement database migrations.
- Implement caching strategies (Redis, Memcached).
- Implement search capabilities (Elasticsearch, Algolia).
- Set up backup and recovery procedures.
- Perform data analysis and ETL processes.

## Core Components

### 1. Database Design & Schema
- **Relational (SQL)**: Use for structured data requiring ACID compliance (e.g., PostgreSQL, MySQL).
- **Non-Relational (NoSQL)**: Use for unstructured or high-scale data (e.g., MongoDB, Cassandra, DynamoDB).
- **Normalization**: Organize data to minimize redundancy and dependency.
- **Indexing**: Optimize query performance using B-Tree, Hash, GIN, or GiST indexes.

### 2. Data Lifecycle Management
- **Ingestion**: Efficiently loading data from various sources (APIs, files, event streams).
- **Storage**: Choosing the right storage medium (Relational, Document, Key-Value, Graph) based on access patterns.
- **Archival**: Moving infrequently accessed data to cheaper storage (e.g., S3 Glacier) to reduce costs.
- **Deletion/Purging**: Implementing retention policies to remove expired or unnecessary data safely.

### 3. Maintenance & Reliability
- **Migrations**: Use version-controlled migration tools (e.g., Alembic, Flyway, Liquibase) to evolve schemas safely.
- **Backup & Recovery**:
    - **Full Backup**: Complete copy of the entire dataset.
    - **Incremental Backup**: Captures only changes since the last full or incremental backup.
    - **Differential Backup**: Captures all changes since the last full backup.
    - **Point-in-Time Recovery (PITR)**: Restoring to a specific moment in time using transaction logs.
- **Consistency**: Ensure data integrity through constraints, ACID transactions, and replication.

### 4. Performance & Scalability
- **Caching**: Use in-memory caches (e.g., Redis) to speed up frequent reads and reduce DB load.
- **Read Replicas**: Scale read operations by replicating data across multiple nodes.
- **Sharding/Partitioning**: Distribute large datasets across multiple database instances or tables to improve scalability.

### 5. Search & Analytics
- **Search Engines**: Implement full-text search (e.g., Elasticsearch, Meilisearch) for complex queries.
- **ETL (Extract, Transform, Load)**: Build pipelines to move and transform data for analysis.
- **Data Warehousing**: Use dedicated systems (e.g., Snowflake, BigQuery) for complex analytical queries (OLAP).

## Best Practices

- **Always version your schema** using migration tools.
- **Always test your migrations** in a staging environment that mirrors production.
- **Implement regular, automated backups** and periodically test the restore process.
- **Use indexes wisely**: Balance read performance against write overhead.
- **Prefer managed database services** (RDS, Cloud SQL) to reduce operational burden.
- **Monitor slow queries** and optimize database performance.

## Common Pitfalls

- **Data Silos**: Allowing data to become isolated in disconnected systems.
- **Stale Data**: Serving outdated information due to improper cache invalidation.
- **Lack of Backups**: Not having a tested, automated backup strategy.
- **Over-Normalization**: Excessive joins that degrade query performance.
- **Improper Data Types**: Using inefficient types for large datasets (e.g., using strings for dates).

## Deliverables

- Database schema diagrams (ERDs).
- Database migration scripts.
- Caching implementation logic.
- Search engine configuration and indexing strategies.
- Backup and recovery plans.
- Data analysis pipelines/scripts.

## Quality Checklist

- [ ] Schema is well-designed and normalized/de-normalized appropriately.
- [ ] All schema changes are handled via migrations.
- [ ] Automated backups are configured and tested regularly.
- [ ] Caching is implemented for performance-critical paths with proper invalidation.
- [ ] Search/indexing is optimized for common queries.
- [ ] Data integrity is maintained through constraints/transactions.
- [ ] Retention policies are defined and implemented.
