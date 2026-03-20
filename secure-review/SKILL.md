---
name: secure-review
description: Security-focused review of backend code, endpoints, or configuration. Use for "is this secure", threat modeling a feature, or auditing auth/authz logic.
---
Perform a security-focused review across these categories:

**Authentication & Authorization**
- Missing or bypassable auth checks on endpoints
- Broken access control (IDOR, privilege escalation, missing ownership checks)
- Token handling (expiry, rotation, storage, revocation)

**Injection**
- SQL injection (raw queries, string interpolation)
- Command injection (shell exec with user input)
- Template injection, LDAP injection, header injection

**Data Exposure**
- Sensitive data in logs, error messages, or API responses
- Secrets hardcoded in source (API keys, passwords, tokens)
- PII returned without need-to-know filtering

**Input Validation**
- Missing or incomplete input validation at system boundaries
- Type coercion issues, oversized payloads, path traversal
- File upload risks (type, size, storage location)

**Configuration**
- CORS policy (overly permissive origins)
- CSRF protection on state-changing endpoints
- Security headers (HSTS, Content-Security-Policy, X-Frame-Options)
- Rate limiting on auth and sensitive endpoints

**Cryptography**
- Weak hashing (MD5/SHA1 for passwords), missing salts
- Predictable tokens or session IDs
- Insecure random number generation

For each finding: severity (critical/high/medium/low), the vulnerable code, attack scenario, and the fix.
Explore the codebase for auth middleware, input validation layers, and config files before reporting.
