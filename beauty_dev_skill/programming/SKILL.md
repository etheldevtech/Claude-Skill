---
name: programming
description: Write or change code to the team standard. Use when asked to implement, fix, or edit code, or when the user runs /programming. Do not write or run tests.
---

# Programming

Write the change. Match the surrounding code. Do not write tests, do not update tests, and do not run the test suite unless the user asks.

### 1. Correct, Not Clever
No logic errors, null dereferences, race conditions, or off-by-one errors. Handle empty input, nil/null, 0, -1, MaxInt, concurrent access, network timeouts, malformed data, and the wrong type.

### 2. Simple Enough for 6 Months
Fewer lines, less state, built-in language or library features over custom code. Keep the abstraction at the level the file already uses. Do not over-engineer. Change only what the task needs. Do not add a function that is used once and only moves a few straight lines out of the caller. Leave that code inline. A wrapper that only calls another function counts. Do not copy a check, query, or transform that already exists. Call or extend that code. Remove code this change leaves unused. A new function is allowed when more than one caller uses it, or the file already splits that work the same way.

### 3. Nothing Fails Silently
Do not swallow exceptions. Check returned errors. Every operation that can fail has an error path. Do not log an error and continue. Config matches across services. After an outage, the path recovers.

### 4. Do Not Break Callers
Do not remove or rename a public API, or change a signature, JSON field, env var, or default. A schema change ships with a migration. Do not edit a migration that already ran. Delete data that should be gone.

### 5. No Open Security Holes
Sanitize input that reaches a query, shell, or HTML. New endpoints and mutations check auth and permission. Do not log or return secrets, tokens, or PII. Do not trust a client-supplied id or role. No insecure default. Signatures must not be forgeable.

### 6. Bound the Cost
No N+1 queries. No unbounded loops or in-memory collections. Add the index the query needs. Retries have a cap and backoff. It still works at 20× traffic. Ignore micro-optimizations.

Skip any rule that does not apply.
