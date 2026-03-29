<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License: MIT">
  <img src="https://img.shields.io/badge/Workflow-Generic%20Development-1f6feb" alt="Generic Development Workflow">
  <img src="https://img.shields.io/badge/Format-SKILL.md-0f766e" alt="SKILL.md Package">
  <img src="https://img.shields.io/badge/Comments-Project%20Aligned-b45309" alt="Project Aligned Comments">
  <img src="https://img.shields.io/badge/Docs-Implementation%20First-8b5cf6" alt="Implementation First Docs">
</p>

# Software Development Workflow for SKILL.md Platforms

<p align="center">
  A structured generic SKILL.md-compatible package for disciplined software development across languages and frameworks.<br>
  一个面向兼容 SKILL.md 平台的结构化通用开发工作流包，适用于多语言、多框架项目。
</p>

<p align="center">
  Built for teams and individual developers who want coding agents to behave like disciplined engineering collaborators instead of one-shot code generators.<br>
  适用于希望让编码代理更像“有工程协作规约的实现伙伴”，而不是一次性代码生成器的团队与个人开发者。
</p>

[中文介绍](#中文介绍)

## English

### Overview

This package applies a generic software development workflow to SKILL.md-compatible platforms.

Its purpose is not just to help an agent produce code, but to make it work in a way that fits real repositories: reading context first, respecting local conventions, writing comments in the right language, documenting current implementation clearly when needed, and avoiding careless refactors or risky actions.

### Why This Package Exists

Many agent workflows become hard to trust when they drift away from repository conventions. Common problems include:

- editing code before reading task context
- introducing comments in the wrong language
- writing development documents that are too thin to be useful
- making broad refactors while solving a narrow problem
- changing docs or behavior without explaining assumptions

This package turns those concerns into explicit execution rules.

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
skill-package/
├── README.md
├── SKILL.md
├── SKILL_CN.md
├── workflow.md
├── workflow.zh-CN.md
├── agents/
│   └── openai.yaml
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

1. Place this directory under the target platform's skill directory.
2. Use [SKILL.md](./SKILL.md) as the primary entry file.
3. Keep [SKILL_CN.md](./SKILL_CN.md) as the Chinese reference version when you want a bilingual companion copy.
4. Read the matching workflow file.
5. Use the reference files only when the task actually needs them.
6. Keep the `scripts/` helper available if you want backup automation.

### Design Principles

1. Understand current implementation before editing.
2. Prefer local repository consistency over personal preference.
3. Keep comments, logs, and docs useful rather than noisy.
4. Prefer minimal, controlled changes over broad rewrites.
5. Treat validation and delivery notes as part of the work.

---

## 中文介绍

### 项目概述

这个目录是一份面向兼容 `SKILL.md` 平台的通用开发工作流包。

它的目标不只是“让代理会写代码”，而是让它在真实项目里按照更像工程协作的方式工作：先读上下文、遵守项目风格、按正确语言写注释、需要时把当前实现讲清楚、避免随手大改和高风险操作。

### 为什么需要这个包

很多 agent 工作流之所以不稳定，不是因为模型不会写代码，而是因为它和仓库原有习惯脱节。常见问题包括：

- 没读任务上下文就开始改代码
- 注释语言和项目习惯不一致
- 开发文档写得太薄，后续维护者看不懂
- 为了解一个小问题顺手做大重构
- 修改完不说明假设、验证和风险

这个包的价值，就是把这些问题变成明确规则。

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
skill-package/
├── README.md
├── SKILL.md
├── SKILL_CN.md
├── workflow.md
├── workflow.zh-CN.md
├── agents/
│   └── openai.yaml
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

1. 把这个目录放到目标平台的技能目录里。
2. 以 [SKILL.md](./SKILL.md) 作为主入口文件。
3. 保留 [SKILL_CN.md](./SKILL_CN.md) 作为中文对照版，方便做双语维护。
4. 继续读取对应的工作流文件。
5. 只有任务真的需要时，再去加载参考资料。
6. 如果需要备份脚本能力，就把 `scripts/` 一起保留。

### 设计原则

1. 改代码前先理解当前实现。
2. 优先保持仓库局部一致性，而不是按个人习惯输出。
3. 注释、日志和文档要有信息量，而不是堆噪音。
4. 优先做最小、可控的修改，不顺手做大范围重写。
5. 验证和交付说明本身就是实现工作的一部分。
