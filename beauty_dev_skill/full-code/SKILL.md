---
name: full-code
description: >
  Write code, review it, and explain it in one pass, using the programming,
  code-review-pipeline, and explain-code standards. Use when the user asks
  to implement and review, code then explain, run the full pipeline, or
  runs /full-code.
---

# Full Code

Code, review, and explain with the user's three standards.
Do not edit those skills. Read each one you run, then follow it.

## Sources

Paths are next to this skill. Each file is the only copy of its rules.

- Code: `../programming/SKILL.md`
- Review: `../code-review-pipeline/SKILL.md`
- Explain: `../explain-code/SKILL.md`

## Which phases

- **Full** (default for a build, fix, or change, and for `/full-code` with a task): Code, Review, Fix, Explain.
- **Code**: the user asks only to implement.
- **Review**: the user asks only to review. Do not change code.
- **Explain**: the user asks only what the code does. Do not change code.

If the user names two of the three, run those in this order: Code, Review, Explain. Run Fix only when Code ran and Review found fixes.

## Code

Follow `../programming/SKILL.md`, including rule 2. Write only the requested change. Do not add a one-use helper or copy logic that already exists.

## Review

Follow `../code-review-pipeline/SKILL.md`.

Review this target, in order:

1. The change this run just made.
2. The diff or code block the user gave.
3. `git diff HEAD`.

## Fix

Run only after Code and Review, and only for FIX NEEDED items in the code.

- Apply them under `../programming/SKILL.md`.
- When review marks a one-use helper or copied logic FIX NEEDED, inline the helper or call the existing code.
- Step 8 may name missing tests. Report them. Do not add tests unless the user asked.
- One pass. Do not run the 10 steps again.
- If a fix would break a programming rule, skip it and say why.

## Explain

Follow `../explain-code/SKILL.md`.

When this run changed code, explain that change. Otherwise use the target order in that skill. Do not change code in this phase.

## Reply

Use this order. Skip a phase you did not run.

1. The code change.
2. The 10-step review, in that skill's shape.
3. Fixes applied, or "No fixes." One short list.
4. The explain-code output, and nothing after it.

Do not paste the three source skills into the reply.
