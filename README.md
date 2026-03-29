<p align="center">
  <img src="https://img.shields.io/badge/license-MIT-green.svg" alt="License: MIT">
  <img src="https://img.shields.io/badge/Workflow-Generic%20Development-1f6feb" alt="Generic Development Workflow">
  <img src="https://img.shields.io/badge/Multi--Adapter-Codex%20%7C%20SKILL.md-0f766e" alt="Multi Adapter">
  <img src="https://img.shields.io/badge/Comments-Project%20Aligned-b45309" alt="Project Aligned Comments">
  <img src="https://img.shields.io/badge/Docs-Implementation%20First-8b5cf6" alt="Implementation First Docs">
</p>

# Software Development Workflow

<p align="center">
  A generic software development workflow package for AI coding agents across languages, frameworks, and project types.<br>
  一个面向 AI 编码代理的通用软件开发工作流仓库，适用于多语言、多框架和多种项目类型。
</p>

<p align="center">
  Built for teams and individual developers who want coding agents to behave like disciplined engineering collaborators rather than one-shot code generators.<br>
  适用于希望让编码代理更像“有工程协作规约的实现伙伴”，而不是一次性代码生成器的团队与个人开发者。
</p>

[中文介绍](#中文介绍)

## English

### Overview

Software Development Workflow is a generic development workflow package for AI coding agents.

Its purpose is not only to help an agent write code, but also to make it behave in a way that fits real repositories: read the right context first, preserve local conventions, choose comment language according to the project, document current implementation clearly when requested, and avoid careless refactors or risky actions.

Rather than treating every coding task as a one-shot generation problem, this repository treats implementation as a controlled engineering activity.

### Why This Repository Exists

Many agent-assisted changes become hard to trust not because models cannot generate code, but because the workflow around the code is weak. Common problems include:

- editing code before reading task context
- introducing comments in the wrong language for the touched module
- making broad refactors while solving a narrow issue
- updating documentation without enough implementation detail
- changing behavior without clearly stating assumptions, validation, or risks

This repository turns those concerns into reusable workflow rules.

### Core Capabilities

- Reads the most relevant project context before edits
- Prefers task-specific development documents when they exist
- Keeps comment language aligned with the local file or module context
- Encourages minimal, controlled, project-aligned changes
- Treats development documentation as a first-class engineering asset
- Supports controlled backups with configurable backup directory naming
- Requires explicit delivery notes about assumptions, changes, and validation

### Repository Structure

```text
software-develop/
├── adapters/
│   ├── codex/
│   │   ├── README.md
│   │   ├── SKILL.md
│   │   ├── SKILL_CN.md
│   │   ├── workflow.md
│   │   ├── workflow.zh-CN.md
│   │   ├── agents/
│   │   │   └── openai.yaml
│   │   ├── references/
│   │   └── scripts/
│   └── skill-md/
│       ├── README.md
│       ├── SKILL.md
│       ├── workflow.md
│       ├── workflow.zh-CN.md
│       ├── references/
│       └── scripts/
├── LICENSE.txt
├── LICENSE_CN.txt
└── .gitignore
```

### Design Strategy

This repository uses a multi-adapter structure.

Each platform directory is intentionally self-contained, which means:

- `adapters/codex` can be used directly as a Codex skill package
- `adapters/skill-md` can be used directly as a generic `SKILL.md`-compatible skill package
- each adapter keeps its own workflow notes, reference files, and helper scripts

The reason for this design is simple: an installable or reusable package should be complete by itself. Users should not have to understand hidden shared directories or internal packaging assumptions before using it.

### Comment Language Strategy

This workflow does not hard-code comment language.

Instead, it follows the strongest local signal:

1. explicit user instruction
2. existing comments in the touched file
3. comment language in adjacent files of the same module
4. task documents or technical notes
5. dominant repository convention
6. English as the fallback

That means:

- English-first projects stay English-first
- Chinese-first projects stay Chinese-first
- mixed repositories can still preserve module-level consistency

### Development Documentation Strategy

This repository treats development documentation as a serious part of engineering work.

When documentation is requested, the workflow expects the agent to explain:

- what the feature is for
- what is already complete
- how the code is layered
- which classes, methods, objects, fields, and states matter
- what the full flow and call chain look like
- how errors are handled
- what is still incomplete
- what risks and maintenance cautions remain

In other words, the development-document layer is expected to explain current implementation clearly enough for another maintainer to continue the work.

### Backup Strategy

Backups are only created when explicitly requested.

By default, backup files should be placed under the project-root `backups/` directory, but the directory name may follow the project's own convention or a user-provided override when needed.

### Usage

#### Codex

Use:

- [adapters/codex](./adapters/codex)

If you want to install it with a skill installer, point the installer at that directory.

#### SKILL.md Platforms

Use:

- [adapters/skill-md](./adapters/skill-md)

Start from `SKILL.md`, then continue with the matching workflow file.

### License

- Legal text: [LICENSE.txt](./LICENSE.txt)
- Chinese reference translation: [LICENSE_CN.txt](./LICENSE_CN.txt)

---

## 中文介绍

### 项目概述

Software Development Workflow 是一个面向 AI 编码代理的通用软件开发工作流仓库。

它的目标不只是“让代理会写代码”，而是让代理在真实仓库里按照更像工程协作的方式工作：先读对上下文、遵守项目现有习惯、按项目语言环境写注释、需要时把当前实现讲清楚、避免随手大重构和高风险操作。

它不是把每个编码任务都当成一次性生成问题，而是把实现过程当成受约束、可维护、可交接的工程活动。

### 为什么需要这个仓库

很多 Agent 辅助改动之所以不稳定，并不是因为模型不会写代码，而是因为围绕代码的工作流太弱。常见问题包括：

- 没读任务上下文就开始改代码
- 注释语言和当前模块的既有风格不一致
- 为了解一个小问题顺手做大范围重构
- 维护开发文档时写得过于空泛
- 修改完不说明假设、验证和风险

这个仓库的价值，就是把这些问题沉淀成可复用的工作流规则。

### 核心能力

- 改代码前先读取最相关的项目上下文
- 如果存在匹配任务的开发文档，优先先读开发文档
- 注释语言跟随当前文件或模块的语言环境
- 强调最小、可控、对齐项目风格的改动
- 把开发文档当成一等工程资产来维护
- 支持可配置备份目录的受控备份策略
- 要求交付时明确说明改动、依据、假设和验证情况

### 仓库结构

```text
software-develop/
├── adapters/
│   ├── codex/
│   │   ├── README.md
│   │   ├── SKILL.md
│   │   ├── SKILL_CN.md
│   │   ├── workflow.md
│   │   ├── workflow.zh-CN.md
│   │   ├── agents/
│   │   │   └── openai.yaml
│   │   ├── references/
│   │   └── scripts/
│   └── skill-md/
│       ├── README.md
│       ├── SKILL.md
│       ├── workflow.md
│       ├── workflow.zh-CN.md
│       ├── references/
│       └── scripts/
├── LICENSE.txt
├── LICENSE_CN.txt
└── .gitignore
```

### 设计思路

这个仓库采用的是多适配器结构。

每个平台目录都是自包含的独立包，这意味着：

- `adapters/codex` 可以直接当作 Codex skill 包使用
- `adapters/skill-md` 可以直接当作通用 `SKILL.md` 技能包使用
- 每个适配器都保留自己的 workflow、reference 和辅助脚本

这样设计的原因很直接：一个可安装、可复用的包应该自己就是完整的，使用者不应该先去理解一堆隐藏共享目录或内部打包假设，才能知道怎么用。

### 注释语言策略

这套工作流不会把注释语言写死。

它遵循的优先级是：

1. 用户明确要求
2. 当前修改文件中的现有注释语言
3. 同模块相邻文件的注释语言
4. 任务文档或技术说明的主语言
5. 仓库整体最稳定的习惯
6. 如果没有明确信号，默认英文

也就是说：

- 英文项目继续写英文注释
- 中文项目继续写中文注释
- 双语仓库也能维持模块级一致

### 开发文档策略

这个仓库把开发文档当成真正的工程资产来对待。

当任务要求维护开发文档时，工作流要求代理把这些东西讲清楚：

- 功能目标是什么
- 当前完成情况是什么
- 代码如何分层
- 哪些类、方法、对象、字段和状态最关键
- 完整流程链和方法调用链路是什么
- 错误是怎么处理的
- 还有哪些没完成
- 还存在哪些风险和维护注意点

也就是说，开发文档不是一句“实现了 XX 功能”的总结，而是要写到后续维护者能真正接手的程度。

### 备份策略

只有在用户明确要求时才创建备份。

默认备份目录是项目根目录下的 `backups/`，但如果项目本身已经有既定约定，或者用户明确要求其他目录名，就优先跟随项目或用户要求。

### 使用方式

#### Codex

使用：

- [adapters/codex](./adapters/codex)

如果使用 skill installer，就把这个目录作为安装目标。

#### `SKILL.md` 平台

使用：

- [adapters/skill-md](./adapters/skill-md)

从 `SKILL.md` 开始，再继续读取对应的 workflow 文件。

### 许可证

- 法律文本：[LICENSE.txt](./LICENSE.txt)
- 中文参考译文：[LICENSE_CN.txt](./LICENSE_CN.txt)
