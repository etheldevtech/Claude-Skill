---
name: design-architecture
description: >
  Write a function design document with high-level architecture, one simple
  diagram, schema design, and exception handling. Pick the most secure method
  that still meets the performance bar. Use when asked to design a function,
  write a function document, design architecture or a schema, or when the user
  runs /design-architecture.
argument-hint: "<function name or description>"
---

# Design Architecture

Write a function design document. Stop after the document.

Read the function the user names. If they name files or a diff, read those first. If the function is new, design from their description.

## Method

Choose the method before writing. It must pass both bars. If a faster method fails the security bar, reject it. The Method line names the cost of the secure method in one clause.

Skip a rule that cannot apply. A pure computation has no auth rule and no query rule. A read has no idempotent-write rule.

### Security bar

A method passes only when all of these hold:

- The caller is authenticated at the boundary.
- Every read and write is authorized on the server against the resource. A client-supplied id or role is not authority.
- Every query is parameterized. Every input is validated and size-bounded at the boundary. Default is deny.
- Secrets, tokens, and PII are not logged or returned.
- A write is idempotent, enforced by a unique constraint.
- Anything signed cannot be forged.

### Performance bar

A method passes only when all of these hold:

- The hot path is one indexed lookup or one indexed write. No N+1.
- Lists, loops, and payloads are capped.
- Work not needed for the response is off the request path.
- Retries have a cap and backoff. A cache has an explicit invalidation rule.
- No micro-optimization.

## Document

Write these sections, in this order, and nothing else. Write the document in the reply. If the user names a path, write that file instead.

# <Function name>

## High Architecture

Five lines or fewer. What the function does, who calls it, what it owns, and what it calls.

Then one line:

`Method: <name> — <the security property, the indexed access, and any cost of keeping the security bar>.`

## Image

One mermaid flowchart, direction `LR`. This is the only image. Eight nodes or fewer. Boxes and arrows only. No subgraphs, icons, emojis, or notes.

One style, applied to every node: `fill:#F7F5F2,stroke:#1F2933,color:#1F2933`.

Each box label is a short noun. Each arrow label is the data that moves, or is omitted.

## Schema Design

One table per entity this function reads or writes. No entity it does not touch.

| Field | Type | Constraint | Index |
| --- | --- | --- | --- |

- Constraint: nullability, uniqueness, length, or enum. 8 words or fewer.
- Index: the index the hot path uses, or `none`.
- Under each table, one line: `Access: <the single indexed lookup or write>.`
- When a field is new or changed, add one migration sentence under that table.

## Exception Handling

Special failures only. No happy path. One table. Number from E0001 with no gaps. Skip a case that cannot happen. If none apply, write `No exception cases for this function.` and stop.

| Case No. | Name | Handling |
| --- | --- | --- |
| E0001 | | |

- Name: 7 words or fewer. Name the exception.
- Handling: 20 words or fewer. What the function does, and what the caller sees.
- Fail closed. A failed auth, permission, signature, or write stops the function.
- Retry only a timeout or an unavailable dependency, with a cap and backoff.
- Count the words in each cell. Rewrite until it is inside the limit.

Check: empty input, nil, 0, -1, MaxInt, wrong type, malformed data, timeout, concurrent write, missing permission, forgeable signature, secret in a log, unbounded result, retry storm.
