---
name: schema-review
description: Critique a database schema or migration for correctness, performance, and maintainability. Use when user shares a schema, migration file, or asks "is this DB design good?".
---
Review the provided schema or migration with the eye of a senior backend engineer. Cover:

1. **Normalization** — unnecessary duplication, missing junction tables, denormalization that will cause update anomalies
2. **Indexes** — missing indexes on FK columns, query patterns, over-indexing
3. **Constraints** — missing NOT NULL, UNIQUE, CHECK constraints that should exist at the DB level
4. **Naming** — consistency, clarity, plural vs singular conventions
5. **Data types** — wrong types (e.g. VARCHAR for UUIDs, FLOAT for money), oversized columns
6. **Scalability** — partitioning needs, soft delete patterns, timestamp fields
7. **Migration safety** — is this migration safe to run on a live production DB? Lock risks?

For each issue, give: what's wrong, why it matters, and the exact SQL/Django/SQLAlchemy fix.
Ask one clarifying question at a time if query patterns are unknown.
