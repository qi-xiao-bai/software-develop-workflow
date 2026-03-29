# Software Development Workflow

This is a standalone Claude Code project-instructions package.

Chinese files: [translations/](translations/).

## What This Adapter Enforces

1. Read the most relevant project context before making edits.
2. Prefer task-specific development documents when they exist.
3. Do not update project documentation unless the user explicitly asks for documentation maintenance.
4. Use the comment language that matches the touched project context rather than a fixed language.
5. Preserve the project's existing logging, testing, naming, and structural conventions.
6. Prefer minimal, controlled edits over broad refactors.
7. Avoid dangerous environment commands, deployment commands, or irreversible actions unless the user explicitly asks for them.
8. If the user explicitly asks for a backup, create it under the project-root `backups/` directory by default and keep at most three backups per source file.

## Trigger Conditions

Strictly apply this workflow when the user's task includes implementation-oriented intent such as:

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
- Comment language policy: [references/comment-language-policy.md](references/comment-language-policy.md)
- English development document template: [references/development-doc-template.md](references/development-doc-template.md)
- Development document writing guide: [references/development-doc-writing-guide.md](references/development-doc-writing-guide.md)
- Backup helper script: [scripts/backup_source_file.py](scripts/backup_source_file.py)

Chinese files:

- Chinese instructions: [translations/CLAUDE_CN.md](translations/CLAUDE_CN.md)
- Chinese workflow guide: [translations/workflow.zh-CN.md](translations/workflow.zh-CN.md)

## Required Workflow

Read [workflow.md](workflow.md) first and follow it as the main operating contract for the task.
