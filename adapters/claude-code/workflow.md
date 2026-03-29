# General Development Workflow

This document is the main workflow contract for disciplined software development across languages, frameworks, and repository styles.

It is designed for real project maintenance rather than one-shot code generation. The goal is to help the agent work like a careful implementation partner: understand context first, preserve the repository's conventions, make controlled changes, and leave behind delivery notes that help future maintainers.

## Strict Trigger Conditions

This workflow must be applied strictly when the user's task clearly asks for code-changing work, especially requests containing intent such as:

- modify
- implement
- fix
- refactor
- add feature
- change behavior
- optimize existing code

Apply the same strict behavior for equivalent intent expressed in Chinese, including:

- 修改
- 实现
- 修复
- 重构
- 添加功能
- 调整现有行为
- 优化现有代码

## Core Principles

1. Read the most relevant project context before making edits.
2. Prefer local project conventions over personal preference.
3. Make minimal, controlled changes instead of broad refactors.
4. Keep comments, logs, tests, and documentation aligned with the existing codebase.
5. Treat validation and delivery notes as part of the implementation work.

## What This Workflow Is Trying To Prevent

Many coding tasks become risky not because the code is inherently hard, but because the implementation process becomes careless. Common failure modes include:

- editing code before reading the active task context
- solving a narrow bug with a broad refactor
- writing comments in the wrong language for the module
- adding logs that do not match the existing observability style
- updating docs without being asked
- delivering code without explaining assumptions or testing gaps

This workflow exists to make those risks explicit and prevent them by default.

## Required Workflow

### 1. Identify the project root

Use the user-provided path or repository markers such as:

- `.git/`
- `README.md`
- `package.json`
- `pyproject.toml`
- `Cargo.toml`
- `go.mod`
- `pom.xml`
- `build.gradle`
- other language-specific root markers

The project root matters because documentation, config, scripts, tests, and backup conventions often depend on it.

### 2. Read the most relevant context first

Before editing, read the sources of truth that best define the task boundary and current implementation.

Priority:

1. A task-specific `*-开发文档.md`, `*-development-doc.md`, design note, ADR, ticket-linked implementation note, or requirement document
2. The file or files being changed and adjacent implementation files
3. Repository-level docs such as `README.md`, architecture notes, config files, and tests
4. Existing error messages, logs, snapshots, or fixtures that clarify current behavior

If a task-specific development document exists and clearly matches the task, read it before editing.

If multiple documents are plausible and the choice materially affects implementation, ask for confirmation.

If no task document exists, ground the work in existing code, tests, and top-level project docs rather than guessing.

### 3. Extract the current implementation context

At minimum, capture:

- current behavior
- implemented scope
- confirmed business or technical rules
- expected end state
- known risks, test gaps, and pending items

When useful, summarize this context for yourself before editing so the planned change stays bounded.

### 4. Edit conservatively

- read existing logic first
- prefer minimal, controlled edits
- preserve the current project style
- do not perform unrelated refactors
- do not remove unrelated logic, comments, tests, fixtures, configuration, or user changes

When the cleanest fix truly requires a broader change, explicitly recognize that tradeoff instead of quietly expanding scope.

## Comment Rules

Follow the strongest local signal for comment language and comment style.

Use this order:

- the user's explicit instruction if one exists
- otherwise the dominant comment language of the touched file
- otherwise the dominant comment language of adjacent files in the same module
- otherwise the main language used by the task document or technical notes
- otherwise the dominant repository convention
- otherwise English as the fallback

Comments should explain:

- intent
- constraints
- edge cases
- state transitions
- side effects
- non-obvious behavior

Do not add low-value comments for trivial assignments, obvious returns, or simple wrappers unless the local project style explicitly expects them.

## Logging and Debug Rules

When adding logs or debug statements:

- follow the project's existing logging stack and style
- add logs only at meaningful checkpoints
- prefer logs that help diagnose state, branch choice, input preparation, side effects, failures, or retries
- avoid duplicate logs that say the same thing before and after the same block
- do not introduce noisy debug output into intentionally quiet paths unless required by the task

Logs should improve diagnosability, not simply prove that execution reached a line.

## Validation Rules

Validation is part of the task, not an optional afterthought.

When possible:

- run the most relevant existing tests
- run focused checks near the changed area first
- prefer project-native validation commands over invented ad hoc commands
- call out what was validated and what was not

If validation cannot be run:

- say so explicitly
- explain why
- name the most likely remaining risk

## Documentation Maintenance

Only update development documents or technical notes when explicitly requested.

When updating them:

1. Start with the high-level structure.
2. Focus on the core files, modules, classes, or functions.
3. Include both a runtime flow section and a method or call chain section.
4. In the method or call chain, every line should include parameters, return value, and purpose.

Use the development-document templates and writing guides in `references/` when the task requires documentation work.

## Backups and Risky Actions

If a backup is explicitly requested:

- create it under the project-root `backups/` directory by default
- keep at most three backups per source file
- back up the original file before the change

If the project already has an established backup directory convention, or the user explicitly requests a different directory name, follow that instead.

Avoid deployment commands, destructive environment actions, or irreversible operations unless the user explicitly asks for them and the target platform allows them.

## Delivery Notes

When finishing a task, report:

- which documents or context sources were read
- which files, modules, classes, or functions were changed
- which comment language was used and why
- where logs or debug statements were added, if any
- whether documentation was intentionally left untouched
- whether validation was run, and if not, why not

## Expected Outcome

If this workflow is followed well, the result should feel like careful repository maintenance:

- the change is understandable
- the scope is controlled
- the style matches the project
- the documentation story is clear
- the next maintainer is not forced to reverse-engineer the intent from the diff alone
