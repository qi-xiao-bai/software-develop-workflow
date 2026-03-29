# Comment Language Policy

Read this reference when the task involves adding or updating comments in code, configs, scripts, tests, or technical documentation.

## Core Rule

Use the comment language that best matches the surrounding project context.

The goal is consistency and readability for the team already maintaining the codebase, not personal preference.

## Decision Order

Choose the comment language in this order:

1. Explicit user instruction
2. Existing comments in the file being edited
3. Existing comments in adjacent files of the same module
4. Language used by the active development document, README, ADR, or task notes
5. Dominant language already used across the repository
6. English as the fallback when no clear signal exists

## Practical Examples

- If the touched module already uses English comments, continue with English comments.
- If the touched module and task documents are mainly Chinese, continue with Chinese comments.
- If the repo is bilingual but the current package is English-first, use English inside that package.
- If the repo has no meaningful comments, do not invent a bilingual style unless the user asks for it.

## Scope Rules

- Follow the dominant language per module, not necessarily per whole monorepo.
- Match the nearest stable convention before applying a repo-wide assumption.
- Keep comments in one language within the same edited block unless the codebase already mixes them intentionally.

## Quality Rules

- Write comments only where they improve understanding.
- Prefer explaining intent, constraints, edge cases, state transitions, side effects, or non-obvious behavior.
- Do not add comments for trivial assignments or obvious returns.
- Keep terminology aligned with existing project wording.

## When Ambiguous

If signals conflict and the choice materially affects maintainability:

- prefer the convention already used in the touched file
- otherwise prefer the convention used in the task document for that module
- if still unclear, state the assumption in the delivery notes
