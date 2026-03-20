---
name: perf-audit
description: Audit a piece of code or endpoint for performance issues. Use for "why is this slow", "optimize this query", or "perf audit".
---
Audit for performance issues across these layers:

**Database**
- N+1 queries (ORM relations not prefetched)
- Missing indexes for the actual query patterns
- SELECT * where only specific columns are needed
- Missing query result caching for stable data

**Application**
- Synchronous I/O that should be async/deferred to Celery
- In-memory operations on large datasets (should be DB-side)
- Serialization of full objects when partial is enough
- Missing pagination

**Caching**
- What can be cached? What's the invalidation strategy?
- Cache stampede risks on cold starts

**Infrastructure**
- Connection pool exhaustion risks
- Missing connection timeouts

For each issue: show the problematic code, explain the cost, give the fix.
If you can access the codebase, check for Django ORM `select_related`/`prefetch_related` usage before asking.
