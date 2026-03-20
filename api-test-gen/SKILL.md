---
name: api-test-gen
description: Generate integration/API tests for an endpoint or service method. Use when you need tests written for existing code, or "write tests for this endpoint".
---
Generate tests for the given endpoint or service method. Follow this process:

1. **Detect the test framework** — find existing tests in the codebase and match the framework, conventions, fixture patterns, and assertion style already in use.
2. **Read the implementation** — understand the endpoint's inputs, outputs, side effects, auth requirements, and error paths before writing tests.
3. **Generate tests in this order:**
   - **Happy path** — valid input, expected output, correct status code, verify side effects (DB writes, events emitted)
   - **Validation errors** — missing required fields, wrong types, boundary values, oversized input
   - **Auth/permission** — unauthenticated, wrong role, correct role, resource ownership checks
   - **Not found / conflict** — nonexistent resources, duplicate creation, stale updates
   - **Error paths** — downstream service failures, timeout behavior, partial failure handling
   - **Edge cases** — empty collections, unicode input, concurrent requests where relevant

4. **For each test:**
   - Descriptive name that states the scenario and expected outcome
   - Minimal setup — only the fixtures this test actually needs
   - Specific assertions (check exact status code, response body fields, DB state) — not just "no error"
   - Clean teardown / isolation from other tests

Match the project's existing patterns for factories, fixtures, API client helpers, and database setup.
Do not generate snapshot tests unless the project already uses them.
Ask what endpoint or method to test if not specified.
