---
name: software-develop
description: Generic software development workflow and guardrails across languages and frameworks. Use when Codex is asked to develop, modify, debug, refactor, review, or maintain code in an existing project and the user wants disciplined context reading, conservative edits, project-aligned comments, fuller development-document guidance, controlled backups, and clear delivery notes.
---

# Software Development Workflow

This is a standalone Codex skill package.

For the Chinese version, see [SKILL_CN.md](SKILL_CN.md).

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
- 优化现有代码

## Resources

- Workflow guide: [workflow.md](workflow.md)
- Chinese workflow guide: [workflow.zh-CN.md](workflow.zh-CN.md)
- Comment language policy: [references/comment-language-policy.md](references/comment-language-policy.md)
- Chinese comment language policy: [references/注释语言策略.md](references/注释语言策略.md)
- Chinese development document template: [references/开发文档模板.md](references/开发文档模板.md)
- English development document template: [references/development-doc-template.md](references/development-doc-template.md)
- Development document writing guide: [references/development-doc-writing-guide.md](references/development-doc-writing-guide.md)
- Chinese development document writing guide: [references/开发文档写作说明.md](references/开发文档写作说明.md)
- Backup helper script: [scripts/backup_source_file.py](scripts/backup_source_file.py)

## Required Workflow

Read [workflow.md](workflow.md) first and follow it as the main operating contract for the task.
