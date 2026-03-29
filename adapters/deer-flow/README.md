<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License: MIT">
  <img src="https://img.shields.io/badge/Workflow-Generic%20Development-1f6feb" alt="Generic Development Workflow">
  <img src="https://img.shields.io/badge/Adapter-deer--flow-0f766e" alt="deer-flow Adapter">
  <img src="https://img.shields.io/badge/Comments-Project%20Aligned-b45309" alt="Project Aligned Comments">
  <img src="https://img.shields.io/badge/Docs-Implementation%20First-8b5cf6" alt="Implementation First Docs">
</p>

# Software Develop for deer-flow

<p align="center">
  A structured deer-flow adapter for a generic software development workflow across languages and frameworks.<br>
  一个面向 deer-flow 的结构化通用开发工作流适配包，适用于多语言、多框架项目。
</p>

<p align="center">
  Built for teams and individual developers who want deer-flow to behave like a disciplined engineering collaborator instead of a one-shot code generator.<br>
  适用于希望让 deer-flow 更像“有工程协作规约的实现伙伴”，而不是一次性代码生成器的团队与个人开发者。
</p>

[中文介绍](#中文介绍)

## English

### Overview

This adapter applies a generic software development workflow to deer-flow.

Its purpose is not just to help deer-flow produce code, but to make it work in a way that fits real repositories: reading context first, respecting local conventions, writing comments in the right language, documenting current implementation clearly when needed, and avoiding careless refactors or risky actions.

Rather than treating deer-flow as a generic prompt runner, this adapter treats it as an implementation partner with explicit workflow boundaries.

### Why This Adapter Exists

Many agent workflows become hard to trust when they drift away from repository conventions. Common problems include:

- editing code before reading task context
- introducing comments in the wrong language
- writing development documents that are too thin to be useful
- making broad refactors while solving a narrow problem
- changing docs or behavior without explaining assumptions

This adapter turns those concerns into explicit execution rules.

### Core Capabilities

- Requires reading the most relevant project context before edits
- Prefers task-specific development documents when they exist
- Aligns comment language with the touched file or module context
- Encourages conservative, project-aligned edits
- Provides fuller development document templates and writing guides
- Supports controlled backups under the project-root `backups/` directory by default, with directory naming left configurable when needed
- Requires clear delivery notes about assumptions, changes, and validation

### Package Layout

```text
deer-flow/
├── README.md
├── prompt.md
├── prompt.zh-CN.md
├── workflow.md
├── workflow.zh-CN.md
├── references/
│   ├── comment-language-policy.md
│   ├── development-doc-template.md
│   ├── development-doc-writing-guide.md
│   ├── 开发文档模板.md
│   └── 开发文档写作说明.md
└── scripts/
    └── backup_source_file.py
```

### How To Use

1. Start from [prompt.md](./prompt.md) or [prompt.zh-CN.md](./prompt.zh-CN.md).
2. Read the matching workflow file.
3. Use the reference files only when the task actually needs them.
4. Use the backup script only when backup is explicitly requested.

### Design Principles

1. Understand current implementation before editing.
2. Prefer local repository consistency over personal preference.
3. Keep comments, logs, and docs useful rather than noisy.
4. Prefer minimal, controlled changes over broad rewrites.
5. Treat validation and delivery notes as part of the work.

---

## 中文介绍

### 项目概述

这个目录是 deer-flow 的通用开发工作流适配包。

它的目标不只是“让 deer-flow 会写代码”，而是让它在真实项目里按照更像工程协作的方式工作：先读上下文、遵守项目风格、按正确语言写注释、需要时把当前实现讲清楚、避免随手大改和高风险操作。

它不是把 deer-flow 当成一个随便塞提示词就能跑的工具，而是把它当成一个需要明确工作边界的实现协作者。

### 为什么需要这个适配包

很多 agent 工作流之所以不稳定，不是因为模型不会写代码，而是因为它和仓库原有习惯脱节。常见问题包括：

- 没读任务上下文就开始改代码
- 注释语言和项目习惯不一致
- 开发文档写得太薄，后续维护者看不懂
- 为了解一个小问题顺手做大重构
- 修改完不说明假设、验证和风险

这个适配包的价值，就是把这些问题变成明确规则。

### 核心能力

- 改代码前优先读取最相关的项目上下文
- 如果存在匹配任务的开发文档，优先先读开发文档
- 注释语言跟随当前修改文件或模块的语言环境
- 强调保守、对齐项目风格的改动
- 提供更完整的开发文档模板和写作说明
- 支持按规约备份源文件到项目根目录默认 `backups/` 文件夹，并允许按项目习惯调整目录名
- 要求交付时明确说明改动、依据、假设和验证情况

### 包结构

```text
deer-flow/
├── README.md
├── prompt.md
├── prompt.zh-CN.md
├── workflow.md
├── workflow.zh-CN.md
├── references/
│   ├── comment-language-policy.md
│   ├── development-doc-template.md
│   ├── development-doc-writing-guide.md
│   ├── 开发文档模板.md
│   └── 开发文档写作说明.md
└── scripts/
    └── backup_source_file.py
```

### 使用方式

1. 从 [prompt.md](./prompt.md) 或 [prompt.zh-CN.md](./prompt.zh-CN.md) 开始。
2. 继续读取对应的工作流文件。
3. 只有任务真的需要时，再去加载参考资料。
4. 只有用户明确要求备份时，才使用备份脚本。

### 设计原则

1. 改代码前先理解当前实现。
2. 优先保持仓库局部一致性，而不是按个人习惯输出。
3. 注释、日志和文档要有信息量，而不是堆噪音。
4. 优先做最小、可控的修改，不顺手做大范围重写。
5. 验证和交付说明本身就是实现工作的一部分。
