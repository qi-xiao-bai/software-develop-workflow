<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License: MIT">
  <img src="https://img.shields.io/badge/Workflow-Generic%20Development-1f6feb" alt="Generic Development Workflow">
  <img src="https://img.shields.io/badge/Adapter-Claude%20Code-0f766e" alt="Claude Code Adapter">
  <img src="https://img.shields.io/badge/Comments-Project%20Aligned-b45309" alt="Project Aligned Comments">
  <img src="https://img.shields.io/badge/Docs-Implementation%20First-8b5cf6" alt="Implementation First Docs">
</p>

# Software Development Workflow for Claude Code

<p align="center">
  A structured Claude Code adapter for disciplined software development across languages and frameworks.<br>
  一个面向 Claude Code 的结构化通用开发适配包，适用于多语言、多框架项目。
</p>

<p align="center">
  Built for teams and individual developers who want Claude Code to behave like a disciplined engineering collaborator instead of a one-shot code generator.<br>
  适用于希望让 Claude Code 更像“有工程协作规约的实现伙伴”，而不是一次性代码生成器的团队与个人开发者。
</p>

[中文介绍](#中文介绍)

## English

### Overview

This package applies a generic software development workflow to Claude Code.

Its purpose is not just to help Claude Code produce code, but to make it work in a way that fits real repositories: reading context first, respecting local conventions, writing comments in the right language, documenting current implementation clearly when needed, and avoiding careless refactors or risky actions.

### Why This Adapter Exists

Many agent workflows become hard to trust when they drift away from repository conventions. Common problems include:

- editing code before reading task context
- introducing comments in the wrong language
- writing development documents that are too thin to be useful
- making broad refactors while solving a narrow problem
- changing docs or behavior without explaining assumptions

This adapter turns those concerns into explicit operating rules.

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
claude-code/
├── README.md
├── CLAUDE.md
├── workflow.md
├── references/
│   ├── comment-language-policy.md
│   ├── development-doc-template.md
│   └── development-doc-writing-guide.md
├── scripts/
│   └── backup_source_file.py
└── translations/
    ├── CLAUDE_CN.md
    ├── workflow.zh-CN.md
    └── references/
        ├── 开发文档模板.md
        ├── 开发文档写作说明.md
        └── 注释语言策略.md
```

### How To Use

Claude Code automatically reads a project-root `CLAUDE.md`.

To use this adapter:

1. Copy [CLAUDE.md](./CLAUDE.md) into your project root as `CLAUDE.md`, or merge its content into your existing project `CLAUDE.md`.
2. Keep `workflow.md`, `references/`, and `scripts/` alongside it if you want the linked supporting materials available in the same package.
3. Chinese files are under [translations/](./translations).

### Design Principles

1. Understand current implementation before editing.
2. Prefer local repository consistency over personal preference.
3. Keep comments, logs, and docs useful rather than noisy.
4. Prefer minimal, controlled changes over broad rewrites.
5. Treat validation and delivery notes as part of the work.

---

## 中文介绍

### 项目概述

这个目录是 Claude Code 的通用开发工作流适配包。

它的目标不只是“让 Claude Code 会写代码”，而是让它在真实项目里按照更像工程协作的方式工作：先读上下文、遵守项目风格、按正确语言写注释、需要时把当前实现讲清楚、避免随手大改和高风险操作。

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
claude-code/
├── README.md
├── CLAUDE.md
├── workflow.md
├── references/
│   ├── comment-language-policy.md
│   ├── development-doc-template.md
│   └── development-doc-writing-guide.md
├── scripts/
│   └── backup_source_file.py
└── translations/
    ├── CLAUDE_CN.md
    ├── workflow.zh-CN.md
    └── references/
        ├── 开发文档模板.md
        ├── 开发文档写作说明.md
        └── 注释语言策略.md
```

### 使用方式

Claude Code 会自动读取项目根目录下的 `CLAUDE.md`。

使用这份适配包时：

1. 把 [CLAUDE.md](./CLAUDE.md) 复制到你的项目根目录，并命名为 `CLAUDE.md`，或者把它的内容合并进你现有的项目级 `CLAUDE.md`。
2. 如果希望同一套包里的工作流、参考资料和脚本都能继续被引用，就把 `workflow.md`、`references/` 和 `scripts/` 一起放在相邻目录。
3. 中文文件位于 [translations/](./translations) 目录下。

### 设计原则

1. 改代码前先理解当前实现。
2. 优先保持仓库局部一致性，而不是按个人习惯输出。
3. 注释、日志和文档要有信息量，而不是堆噪音。
4. 优先做最小、可控的修改，不顺手做大范围重写。
5. 验证和交付说明本身就是实现工作的一部分。
