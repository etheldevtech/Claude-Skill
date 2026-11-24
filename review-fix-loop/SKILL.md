---
name: review-fix-loop
description: Repeatedly run the code-review-pipeline skill and apply fixes until the code is clean (max 8 cycles). Use only when the user asks for the review + fix loop.
disable-model-invocation: true
---

# Code Review + Fix Loop

Goal: Make the current code clean, correct, and standardized.

Process:
1. Run the full `code-review-pipeline` skill on the current code/diff.
2. If **any** review category finds real issues (bugs, missing edge cases, silent failures, unnecessary complexity, architectural problems that will hurt in 6 months), then:
   - Apply the suggested fixes immediately.
   - Keep the changes minimal and focused.
   - Run the tests (`npm test`) after each fix round.
   - Re-run the full review pipeline on the updated code.
3. Stop only when **all** of the following are true:
   - No logic bugs / null dereferences / race conditions / off-by-one errors
   - No important missing edge cases
   - Error handling is solid (no silent failures)
   - No unnecessary complexity (the simpler version is not better)
   - Architecture is pragmatic and maintainable
   - Backward compatibility is not broken (or changes are intentional and documented)

Hard limits:
- Maximum 8 full review+fix cycles
- Prefer small, surgical edits over large rewrites
- Never introduce new public API surface unless necessary
- Follow the project's coding rules in CLAUDE.md

At the end, report: number of cycles run, what was fixed each cycle, and anything left unresolved.
