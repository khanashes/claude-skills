---
name: api-design
description: Review or design a REST/GraphQL API for consistency, usability, and correctness. Use when designing new endpoints, reviewing API contracts, or asking "is this API good?".
---
Review the API design (or design one from requirements) covering:

1. **Resource naming** — nouns not verbs, consistent pluralization, logical nesting (max 2 levels)
2. **HTTP verbs** — correct method for each operation, PUT vs PATCH distinction, POST idempotency keys
3. **Status codes** — appropriate codes per endpoint (don't return 200 for everything), consistent error envelope
4. **Request/response design** — minimal payloads, consistent field naming (camelCase vs snake_case), no leaking of internal IDs or implementation details
5. **Pagination** — cursor-based vs offset, `Link` headers or envelope, default & max page sizes
6. **Filtering & sorting** — consistent query parameter patterns, allowlisted fields only
7. **Versioning** — strategy (URL path, header, or query param), backward compatibility of changes
8. **Error format** — machine-readable error codes, human-readable messages, field-level validation errors
9. **Idempotency** — write operations that need idempotency keys, retry safety
10. **Auth surface** — which endpoints need auth, rate limiting tiers, scope/permission requirements

For each issue: state what's wrong, why it matters for API consumers, and the recommended fix.
If designing from scratch, produce the endpoint table (method, path, description, request, response, status codes).
Ask clarifying questions about the client use cases if the intended consumers are unclear.
