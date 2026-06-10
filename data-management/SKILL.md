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
- **Indexing**: Optimize query performance.

### 2. Data Lifecycle & Maintenance
- **Migrations**: Use version-controlled migration tools to evolve database schemas safely.
- **Backup & Recovery**: Implement automated, tested backup strategies to prevent data loss.
- **Consistency**: Ensure data integrity through constraints, transactions, and replication.

### 3. Performance & Scalability
- **Caching**: Use in-memory caches (e.g., Redis) to speed up frequent reads and reduce DB load.
- **Read Replicas**: Scale read operations by replicating data across multiple nodes.
- **Sharding/Partitioning**: Distribute large datasets across multiple database instances or tables.

### 4. Search & Analytics
- **Search Engines**: Implement full-text search (e.g., Elasticsearch, Solr) for complex queries.
- **ETL (Extract, Transform, Load)**: Build pipelines to move and transform data for analysis.
- **Data Warehousing**: Use dedicated systems (e.g., Snowflake, BigQuery) for complex analytical queries.

## Best Practices

- **Always version your schema** using migration tools.
- **Always test your migrations** in a staging environment.
- **Implement regular, automated backups** and periodically test the restore process.
- **Use indexes wisely**: Balance read performance against write overhead.
- **Prefer managed database services** (RDS, Cloud SQL) to reduce operational burden.
- **Monitor slow queries** and optimize database performance.

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
- [ ] Automated backups are configured and tested.
- [ ] Caching is implemented for performance-critical paths.
- [ ] Search/indexing is optimized for common queries.
- [ ] Data integrity is maintained through constraints/transactions.
