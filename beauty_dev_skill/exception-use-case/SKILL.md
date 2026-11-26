---
name: exception-use-case
description: Write an exception use case report of special failure cases only. Use when asked for exception use cases, what a change will face, or /exception-use-case.
---

# Exception Use Case

Report special exception cases only. No happy path. No normal success flow.

If no target is given, use the current diff (`git diff HEAD`).

## Cases

List only exceptions this code can face. Check: empty input, nil/null, 0, -1, MaxInt, wrong type, malformed data, network timeout, concurrent access, config mismatch between services, 20× traffic, recovery after an outage, forgeable signature, edited migration, and data that should be deleted but is not.

Skip a case that cannot happen here. If none apply, say "No exception cases for this change." and stop.

## Report

One table. Number from U0001 with no gaps.

| Case No. | Name | Expected Result | Result |
| --- | --- | --- | --- |
| U0001 | | | |

- Name: 7 words or fewer. Name the exception.
- Expected Result: 20 words or fewer. What should happen.
- Result: 20 words or fewer. What the current code does when it faces this case. If this is not visible, say what an unhandled case does.
- Count the words in each cell. Rewrite until it is inside the limit.
- One case per row. Do not add columns. Do not write anything after the table.

## Handle

Only when the user asks to handle these cases. Change those exception paths and nothing else. Do not write tests. Do not change the happy path.
