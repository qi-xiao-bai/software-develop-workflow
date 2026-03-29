# deer-flow 适配提示词

把这个目录当成一个可独立使用的 deer-flow 工作流包。

先读取 [workflow.zh-CN.md](workflow.zh-CN.md)，再执行下面这些规则。

## 执行规则

1. 改代码前先读取最相关的项目上下文。
2. 如果存在匹配任务的开发文档，必须先读。
3. 改动要尽量小，并且保持和当前代码仓库风格一致。
4. 注释语言必须跟随当前修改文件或模块的主语言，不能强行固定中文或英文。
5. 只有在用户明确要求时才更新文档。
6. 交付时说明读取了什么上下文、改了什么、采用了什么假设、做了什么验证。

## 严格触发条件

当任务明显属于“要动代码”的场景时，必须严格执行这套规则，尤其是出现下面这些意图时：

- 修改
- 实现
- 修复
- 重构
- 添加功能
- 调整现有行为
- 优化现有代码

如果用户是英文表达，也把下面这些关键词视为严格触发条件：

- modify
- implement
- fix
- refactor
- add feature
- change behavior
- optimize existing code

## 资源

- 工作流说明：[workflow.zh-CN.md](workflow.zh-CN.md)
- 英文工作流说明：[workflow.md](workflow.md)
- 英文注释策略：[references/comment-language-policy.md](references/comment-language-policy.md)
- 中文注释策略：[references/注释语言策略.md](references/注释语言策略.md)
- 英文开发文档模板：[references/development-doc-template.md](references/development-doc-template.md)
- 中文开发文档模板：[references/开发文档模板.md](references/开发文档模板.md)
- 英文开发文档写作说明：[references/development-doc-writing-guide.md](references/development-doc-writing-guide.md)
- 中文开发文档写作说明：[references/开发文档写作说明.md](references/开发文档写作说明.md)
- 备份脚本：[scripts/backup_source_file.py](scripts/backup_source_file.py)
