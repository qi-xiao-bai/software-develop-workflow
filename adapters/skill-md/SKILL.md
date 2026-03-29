---
name: software-develop
description: Generic software development workflow and guardrails across languages and frameworks. Use when a SKILL.md-compatible coding agent is asked to develop, modify, debug, refactor, review, or maintain code in an existing project and disciplined context reading, conservative edits, project-aligned comments, fuller development-document guidance, controlled backups, and clear delivery notes are required.
license: MIT
---

# Software Development Workflow

This is a standalone generic SKILL.md-compatible skill package.

Use this directory in any platform that loads skills from a `SKILL.md` entry file.

Chinese files: [translations/](translations/).

## What This Skill Enforces

1. Read the most relevant project context before making edits.
2. Prefer task-specific development documents when they exist.
3. Do not update project documentation unless the user explicitly asks for documentation maintenance.
4. Use the comment language that matches the touched project context rather than a fixed language.
5. Preserve the project's existing logging, testing, naming, and structural conventions.
6. Prefer minimal, controlled edits over broad refactors.
7. Avoid dangerous environment commands, deployment commands, or irreversible actions unless the user explicitly asks for them.
8. If the user explicitly asks for a backup, create it under the project-root `backups/` directory by default and keep at most three backups per source file.

## Trigger Conditions

Strictly apply this skill when the user's task includes implementation-oriented intent such as:

- modify
- implement
- fix
- refactor
- add feature
- change behavior
- optimize existing code

The same rule applies to equivalent Chinese intent such as:

- 修改
- 实现
- 修复
- 重构
- 添加功能
- 调整现有行为
- 优化现有代码

## Resources

- Workflow guide: [workflow.md](workflow.md)
- Comment language policy: [references/comment-language-policy.md](references/comment-language-policy.md)
- English development document template: [references/development-doc-template.md](references/development-doc-template.md)
- Development document writing guide: [references/development-doc-writing-guide.md](references/development-doc-writing-guide.md)
- Backup helper script: [scripts/backup_source_file.py](scripts/backup_source_file.py)

Chinese files:

- Chinese skill notes: [translations/SKILL_CN.md](translations/SKILL_CN.md)
- Chinese workflow guide: [translations/workflow.zh-CN.md](translations/workflow.zh-CN.md)

## Required Workflow

Read [workflow.md](workflow.md) first and follow it as the main operating contract for the task.
