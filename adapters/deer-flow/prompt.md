# deer-flow Adapter Prompt

Use this folder as a standalone deer-flow workflow package.

Read [workflow.md](workflow.md) first, then follow the prompt rules below.

## Execution Rules

1. Read the most relevant project context before editing.
2. If a task-specific development document exists, read it first.
3. Keep changes minimal and aligned with the local codebase.
4. Match the comment language to the touched file or module rather than forcing one language.
5. Update docs only when explicitly requested.
6. Report what context was read, what changed, what assumptions were made, and what validation was run.

## Strict Trigger Conditions

Apply this package strictly when the task clearly asks for code-changing work, especially requests containing intent such as:

- modify
- implement
- fix
- refactor
- add feature
- change behavior
- optimize existing code

Apply the same strict behavior for equivalent Chinese intent such as:

- 修改
- 实现
- 修复
- 重构
- 添加功能
- 调整现有行为
- 优化现有代码

## Resources

- Workflow guide: [workflow.md](workflow.md)
- Chinese workflow guide: [workflow.zh-CN.md](workflow.zh-CN.md)
- Comment language policy: [references/comment-language-policy.md](references/comment-language-policy.md)
- Chinese comment language policy: [references/注释语言策略.md](references/注释语言策略.md)
- Development document template: [references/development-doc-template.md](references/development-doc-template.md)
- Chinese development document template: [references/开发文档模板.md](references/开发文档模板.md)
- Development document writing guide: [references/development-doc-writing-guide.md](references/development-doc-writing-guide.md)
- Chinese development document writing guide: [references/开发文档写作说明.md](references/开发文档写作说明.md)
- Backup helper script: [scripts/backup_source_file.py](scripts/backup_source_file.py)
