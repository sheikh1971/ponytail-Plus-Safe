---
name: ponytail-plus
description: Production-safe coding discipline. Use for any coding task (new code, bug fixes, refactors, reviews, dependency or infra choices) to write the least code that works, reuse what exists, test every change, and never cut safety, security or least privilege.
---

# ponytail-plus

Write the least code that solves the task, and prove it works. Small is the goal; safe is the rule.

## 1. Before writing code

- Read the task and the code it touches. State your assumptions.
- If a requirement, contract or threshold is unclear, ask. Do not guess.
- List every place the change must reach: callers, tests, fixtures, config, exports, docs.

## 2. Pick the first option that works, in this order

1. Skip what was not asked.
2. Reuse code already in the repo.
3. Use the standard library or a platform feature.
4. Use a dependency that is already installed.
5. Only then write the minimum new code.

Adding a new dependency needs a one-line reason.

## 3. While writing

- No speculative abstractions, wrappers, options, config or "for later" code.
- Prefer deleting to adding. Keep the repo's existing structure and conventions.
- Surgical changes: touch only what the task needs. No drive-by refactors or renames.
- Bug fix: find every caller of the touched function, then fix the root cause once, in the shared place.
- Moved or merged code keeps its error handling and validation.
- Comment only the "why", briefly.
- A shortcut with a known limit gets a comment naming the limit and when to upgrade. Use the repo's comment-tag convention if it has one.

## 4. Never cut

- Validation at trust boundaries.
- Error handling that prevents data loss.
- Security and privacy: no secrets or personal data in code or logs.
- Domain safety rules (for example, in medical or financial code: safety checks, "unclear" marking, disclaimers, audit records).
- Accessibility.

## 5. Tests and proof

- Every change gets a test, even a small one. Bug fixes get a test that fails before the fix.
- Run the project's lint, type check and tests before calling anything done.
- Never claim a check passed if it was not run.

## 6. Cloud, CI and production

- Least privilege for every cloud or CI identity. Never broaden a role or permission to make something pass; add the one narrow permission that is missing.
- Before a change that reaches production: know the rollback, change additively, verify, then remove the old.
- Never read or print secrets; give the user the command to run instead.

## 7. Report

End every report with:
- What changed, in one or two lines.
- What was skipped or not checked, plainly.
