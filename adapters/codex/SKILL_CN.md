---
name: software-develop
description: 通用软件开发流程与协作约束。适用于 Codex 在现有项目中进行开发、修改、调试、重构、Review 或维护代码时，需要先读取关键上下文、保守改动、按项目语言习惯写注释、按需维护开发文档、按需备份源文件，并在交付时明确说明改动依据与验证情况的场景。
---

# Software Develop

这是一个可独立使用的 Codex skill 包。

英文版本见 [SKILL.md](SKILL.md)。

## 这个 Skill 强制约束什么

1. 改代码前先读取最相关的项目上下文。
2. 如果存在与当前任务匹配的开发文档，优先先读开发文档。
3. 默认不维护项目文档，只有用户明确要求时才允许更新。
4. 注释语言不固定写死，必须跟随当前项目或当前模块的主语言习惯。
5. 尽量保持项目现有日志、测试、命名和结构风格。
6. 优先做最小、可控的修改，不顺手做大范围重构。
7. 对部署、环境变更、不可逆操作保持谨慎，除非用户明确要求。
8. 如果用户明确要求备份，则默认备份到项目根目录 `backups/` 文件夹，并且同源文件最多保留三份。

## 触发条件

当用户任务包含下面这类“明确要动代码”的意图时，必须严格执行这套规则：

- 修改
- 实现
- 修复
- 重构
- 添加功能
- 调整现有行为
- 优化现有代码

如果用户用英文表达，同样按下面这些关键词触发严格执行：

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
- 中文开发文档模板：[references/开发文档模板.md](references/开发文档模板.md)
- 英文开发文档模板：[references/development-doc-template.md](references/development-doc-template.md)
- 英文开发文档写作说明：[references/development-doc-writing-guide.md](references/development-doc-writing-guide.md)
- 中文开发文档写作说明：[references/开发文档写作说明.md](references/开发文档写作说明.md)
- 备份脚本：[scripts/backup_source_file.py](scripts/backup_source_file.py)

## 必须遵循的工作流

先读取 [workflow.zh-CN.md](workflow.zh-CN.md)，并把它作为当前任务的主工作契约。
