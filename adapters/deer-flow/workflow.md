# General Development Workflow

This document is the main workflow for disciplined software development across languages and frameworks.

## Strict Trigger Conditions

This workflow must be applied strictly when the user's task clearly asks for code-changing work, especially requests containing intent such as:

- modify
- implement
- fix
- refactor
- add feature
- change behavior
- optimize existing code

Apply the same strict behavior for equivalent Chinese intent, including:

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

## Required Workflow

### 1. Identify the project root

Use the user-provided path or repository markers such as `.git/`, `README.md`, `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, `pom.xml`, `build.gradle`, or other language-specific root markers.

### 2. Read the most relevant context first

Before editing, read the sources of truth that best define the task boundary and the current implementation.

Priority:

1. A task-specific `*-开发文档.md`, `*-development-doc.md`, design note, ADR, ticket-linked implementation note, or requirement document
2. The file(s) being changed and adjacent implementation files
3. Repository-level docs such as `README.md`, architecture notes, config files, and tests
4. Existing error messages, logs, snapshots, or fixtures that clarify current behavior

If a task-specific development document exists and clearly matches the current task, read it before editing.

If multiple documents are plausible and the choice materially affects implementation, ask for confirmation.

If no task document exists, ground the work in existing code, tests, and top-level project docs.

### 3. Extract the current implementation context

At minimum, capture:

- current behavior
- implemented scope
- confirmed business or technical rules
- expected end state
- known risks, test gaps, and pending items

### 4. Edit conservatively

- read existing logic first
- prefer minimal, controlled edits
- preserve the current project style
- do not perform unrelated refactors
- do not remove unrelated logic, comments, tests, fixtures, configuration, or user changes

## Comment Rules

Follow the strongest local signal for comment language and comment style.

Use:

- the user's explicit instruction if one exists
- otherwise the dominant comment language of the touched file
- otherwise the dominant comment language of adjacent files in the same module
- otherwise the main language used by the task document or technical notes
- otherwise the dominant repository convention
- otherwise English as the fallback

Comments should explain intent, constraints, edge cases, side effects, state transitions, or non-obvious behavior.

Do not add low-value comments for trivial assignments, obvious returns, or simple wrappers unless the local project style explicitly expects them.

## Logging and Debug Rules

When adding logs or debug statements:

- follow the project's existing logging stack and style
- add logs only at meaningful checkpoints
- prefer logs that help diagnose state, branch choice, input preparation, side effects, failures, or retries
- avoid duplicate logs that say the same thing before and after the same block
- do not introduce noisy debug output into intentionally quiet paths unless required by the task

## Documentation Maintenance

Only update development documents or technical notes when explicitly requested.

When updating them:

1. Start with the high-level structure.
2. Focus on the core files, modules, classes, or functions.
3. Include both a runtime flow section and a method or call chain section.
4. In the method or call chain, every line should include parameters, return value, and purpose.

## Backups and Risky Actions

If a backup is explicitly requested, create it under the project-root `backups/` directory by default and keep at most three backups per source file.

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
