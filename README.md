# AI Agent 工程化每日导师

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](#license--许可证)
[![Skill](https://img.shields.io/badge/Skill-Codex%20%2F%20Claude%20Code-blue)](#安装)
[![Language](https://img.shields.io/badge/Language-中文%20%7C%20English-red)](#english)

**中文** | [English](#english)

一个中文 AI Agent 工程学习 skill：把现代 Agent 学习路线压成每周大纲、每日 6 小时任务、可运行项目、Obsidian 双链笔记和求职项目表达。

技能标识符：`ai-agent-engineering-mentor`

对外技能名：`AI Agent 工程化每日导师`

项目地址：[github.com/Kcalb0708/ai-agent-engineering-mentor](https://github.com/Kcalb0708/ai-agent-engineering-mentor)

最新版本：[GitHub Releases](https://github.com/Kcalb0708/ai-agent-engineering-mentor/releases)

## 目录

- [为什么做这个 skill](#为什么做这个-skill)
- [At a glance](#at-a-glance)
- [适合谁](#适合谁)
- [学习路线](#学习路线)
- [安装](#安装)
- [快速开始](#快速开始)
- [每日输出结构](#每日输出结构)
- [工作模式](#工作模式)
- [可选来源链接](#可选来源链接)
- [Repository layout](#repository-layout)
- [关键设计](#关键设计)
- [Sources and credits](#sources-and-credits)
- [Contributing](#contributing)
- [License / 许可证](#license--许可证)
- [English](#english)

## 为什么做这个 skill

很多 AI Agent 学习路线会变成资料收藏夹：链接很多，但每天不知道写什么代码、做什么项目、如何判断自己真的进步。

这个 skill 的目标是把学习路线变成可执行闭环：

```text
每周大纲
-> 每日 6 小时任务
-> 可运行代码
-> 自我验收
-> 学习反馈
-> 下一天自适应调整
-> 项目包装与面试表达
```

学习路线参考并致谢 [datawhalechina/Agent-Learning-Hub](https://github.com/datawhalechina/Agent-Learning-Hub)。该项目强调构建可靠、有用的 agents，而不是收集随机链接；本 skill 将其中的 Stage 0-8 路线进一步转化为中文每日学习流程。

## At a glance

| 能力 | 说明 |
| --- | --- |
| 每周大纲 | 生成 Week 1-8 的中文学习计划，按 Day 1-Day 7 拆解 |
| 每日教学 | 默认输出 5 个模块，也可按用户计划保留、重命名、重排或增删 |
| 自适应调整 | 根据 Day 学习反馈判断正常推进、放慢复习、加难扩展或重排 |
| 代码 checkpoint 复盘 | 仅在代码完成并验证后，用真实代码与测试证据做分层复盘 |
| 项目阶梯 | 从 `Calculator Agent` 逐步推进到 `Production-style Agent Project` |
| Obsidian 双链 | 为核心概念、项目模块和面试表达生成稳定中文双链 |
| 可选来源链接 | 命中关键知识点时给出官方文档、规范、论文或项目 README 链接 |
| 求职包装 | 生成项目话术、简历 bullet、面试问答和 README 改进建议 |

## 适合谁

- 想系统学习现代 AI Agent 工程的中文学习者。
- 有 Python 基础，但缺少 AI Agent 项目经验的开发者。
- 想理解 Claude Code / Codex-style coding agents 的学习者。
- 想做一个可投递、可展示、可评测 agent 项目的应届生或实习求职者。
- 想把 Obsidian 知识库和每日学习反馈结合起来的人。

不适合：

- 只想收集资料链接，不打算写代码。
- 只想做 prompt 角色扮演，不关心工具、权限、trace 和 eval。
- 希望一天内直接跳到复杂多 agent 框架的人。

## 学习路线

路线参考 [Agent-Learning-Hub](https://github.com/datawhalechina/Agent-Learning-Hub)，并根据中文学习者的执行节奏重排成 8 周 project ladder。

| 周 | 主题 | 核心产出 |
| --- | --- | --- |
| Week 1 | Python MUP + 最小 Agent Loop | `Calculator Agent` |
| Week 2 | Tool Use + Web Research Agent | `Web Research Agent v1` |
| Week 3 | RAG + Memory + Citation | `PDF QA Agent` 或 `Knowledge Research Agent` |
| Week 4 | Coding Agent Harness 拆解与复刻 | `Nano Coding Agent` |
| Week 5 | Supervisor / Graph / Reviewer | `Multi-Agent Writer` 或 `Coding Review Agent` |
| Week 6 | Skills + Protocols + Capability Packaging | `Reusable Skill Pack` |
| Week 7 | Browser Agent + Computer-use Safety | `Browser Agent` |
| Week 8 | Evaluation, Observability, Safety, Ship | `Production-style Agent Project` |

默认推荐最终项目：

```text
NanoAgent：面向本地代码库的可审计 Coding Agent Harness
```

核心闭环：

```text
用户输入任务
-> 读取项目上下文
-> 选择工具
-> 权限检查
-> 执行安全工具
-> 记录 trace
-> 更新 session
-> 必要时压缩上下文
-> 输出结果或失败原因
-> eval / smoke test 验证
```

如果你的目标是 AI Agent 应用开发实习，也可以选择业务型项目：

```text
AI-Interview：基于 RAG 与 Agent 的智能模拟面试系统
```

但它必须补齐 RAG citation、检索评估、agent trace、session、权限边界、测试、README 和失败记录，不能停留在普通 RAG Demo。

## 安装

这个 skill 是标准 `SKILL.md` 目录结构，适用于支持 Agent Skills / SKILL.md 的宿主。已覆盖的安装入口：

| 宿主 | 推荐安装目录 | 说明 |
| --- | --- | --- |
| Codex | `~/.codex/skills/ai-agent-engineering-mentor` | 适合 OpenAI Codex / Codex CLI |
| Claude Code | `~/.claude/skills/ai-agent-engineering-mentor` | 个人全局 skill；项目级可放 `.claude/skills/` |
| cc-switch | `~/.cc-switch/skills/ai-agent-engineering-mentor` 或 `~/.agents/skills/ai-agent-engineering-mentor` | `~/.agents/skills` 更适合多工具共享 |
| Hermes Agent | `~/.hermes/skills/ai-agent-engineering-mentor` | 适合 Hermes 本地 skill 目录 |

### Codex

推荐始终从主仓库安装，避免复制到旧版本：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.codex/skills/ai-agent-engineering-mentor
```

然后在 Codex 中触发：

```text
使用 AI Agent 工程化每日导师，生成 Week 1 大纲
```

更新到最新版本：

```bash
git -C ~/.codex/skills/ai-agent-engineering-mentor pull --ff-only
```

### Claude Code

安装到个人全局 skills 目录：

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.claude/skills/ai-agent-engineering-mentor
```

项目级安装可以放到当前仓库：

```bash
mkdir -p .claude/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git .claude/skills/ai-agent-engineering-mentor
```

更新：

```bash
git -C ~/.claude/skills/ai-agent-engineering-mentor pull --ff-only
```

### cc-switch

安装到 cc-switch 默认 skills 目录：

```bash
mkdir -p ~/.cc-switch/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.cc-switch/skills/ai-agent-engineering-mentor
```

如果你希望多个 agent 工具共享 skill，也可以安装到社区共享目录：

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.agents/skills/ai-agent-engineering-mentor
```

更新：

```bash
git -C ~/.cc-switch/skills/ai-agent-engineering-mentor pull --ff-only
```

### Hermes Agent

安装到 Hermes skills 目录：

```bash
mkdir -p ~/.hermes/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.hermes/skills/ai-agent-engineering-mentor
```

更新：

```bash
git -C ~/.hermes/skills/ai-agent-engineering-mentor pull --ff-only
```

### 其他兼容 skills 的 agent

把本目录复制到对应 agent 的 skills 目录，并确保目录名与 `SKILL.md` 中的 `name` 一致：

```text
ai-agent-engineering-mentor/
└── SKILL.md
```

如果你是从 GitHub clone 安装的，进入 skill 目录后执行：

```bash
git pull --ff-only
```

参考文档：

- [OpenAI Codex Skills](https://developers.openai.com/codex/skills)
- [Claude Code Skills](https://code.claude.com/docs/en/skills)
- [cc-switch Skills](https://github.com/farion1231/cc-switch/blob/main/docs/user-manual/en/3-extensions/3.3-skills.md)
- [Hermes Agent Skills](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills)

## 快速开始

生成第一周大纲：

```text
使用 AI Agent 工程化每日导师，生成 Week 1 大纲。
我的基础：会一点 Python，但没系统做过 Agent 项目。
目标：8 周内做出可投递的 AI Agent 项目。
```

生成 Day 1：

```text
使用 AI Agent 工程化每日导师，根据 Week 1 大纲生成 Day 1 学习内容。
```

提交反馈并继续：

```text
【Day 1 学习反馈】
1. 今天实际学习时长：4 小时
2. 完成了哪些代码/文件：app/config.py、app/messages.py、app/tools/calculator.py
3. 哪个概念最清楚了：messages 结构
4. 哪个概念还没懂：Tool Schema
5. 卡住的 Bug / 报错全文：无
6. 自我验收题完成情况：2/3
7. 明天希望：正常推进
8. 后续每日模块偏好（留空=默认 5 模块；或填写保留/重命名/新增/删除/顺序）：
```

补全 Obsidian 笔记：

```text
使用 AI Agent 工程化每日导师，基于 Day 1 内容补全最重要的 3-5 个 Obsidian 知识点笔记。
```

## 每日输出结构

每日内容默认输出 5 个顶层模块：

```markdown
📌 今日核心死磕
🎯 6小时精细化路线
💻 今日代码实战
🎯 每日自我验收题
📥 明日同步接口
```

默认配置不会阻塞学习；用户可以在周计划或反馈模板中填写保留、重命名、新增、删除和顺序。自定义后仍需覆盖核心目标、学习路径、代码产出、验收和次日反馈。

代码要求：

- 有 Type Hints。
- 有中文注释。
- 有异常处理。
- 不使用 `pass`。
- 不给不可运行的伪代码。
- 早期优先标准库和轻量依赖，后期再引入 FastAPI、LangGraph、Playwright、MCP SDK 等。

## 工作模式

这个 skill 使用 5 种 Agent Skill 设计模式组合出多个工作模式：

| 工作模式 | 设计模式 | 用途 |
| --- | --- | --- |
| 每周大纲模式 | Generator + Inversion | 生成结构稳定的 Week 大纲，必要时先补问目标 |
| 每日教学模式 | Pipeline + Generator | 按用户模块配置生成每日任务，未配置时使用默认 5 模块 |
| 周计划调整模式 | Reviewer + Pipeline | 审查反馈和项目完整度，再决定下一天任务 |
| 代码 checkpoint 复盘模式 | Reviewer + Generator | 代码完成并验证后，用真实代码和证据做分层复盘 |
| Obsidian 知识维护模式 | Reviewer + Generator | 按评分选择 3-5 个知识点生成笔记 |
| 路线资料消化模式 | Tool Wrapper + Pipeline + Reviewer | 读取外部路线资料，并转成可执行学习规则 |

## 可选来源链接

本 skill 已消化一批现代 Agent 学习资料，但不会替用户封死理解路径。遇到关键知识点时，会在对应段落附近给出少量 `可选来源` 链接。

示例：

```markdown
### [[Agent Loop]]：为什么不是普通 workflow

今天你要理解 agent loop 的关键不是“让模型多想几步”，而是让模型在观察、选择工具、执行工具、读取结果之间形成可控闭环。

可选来源：[Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)、[OpenAI: A practical guide to building agents](https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/)
```

链接规则：

- 每日内容总链接数建议不超过 5 个。
- 每个知识点只给 1-2 个最相关来源，最多 3 个。
- 优先官方文档、标准规范、论文摘要和高质量开源项目 README。
- 不在 `📥 明日同步接口` 后追加链接。

## Repository layout

```text
ai-agent-engineering-mentor/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── skill-mode-patterns.md
    ├── 8-week-spine.md
    ├── weekly-outline-template.md
    ├── day1-seed.md
    ├── adaptation-policy.md
    ├── checkpoint-review-format.md
    ├── final-project-blueprint.md
    ├── internship-success-insights.md
    ├── obsidian-linking-policy.md
    ├── obsidian-note-maintenance-policy.md
    └── source-link-policy.md
```

## 关键设计

### 1. 路线不是资料清单

每天必须落到代码、项目、验收和反馈。资料链接只作为可选深入入口。

### 2. Agent 工程优先

主线关注 tool schema、permission gate、session store、context compaction、trace、eval 和 safety，而不是旧式角色扮演多 agent。

### 3. 代码 checkpoint 要能复盘

分层复盘只在代码 checkpoint 完成并验证后触发，必须引用真实代码、测试和设计依据；每日计划和普通问答不套用该格式。

### 4. 知识库要稳定

Obsidian 双链使用稳定中文命名，避免每天创造同义词导致知识库分裂。

## Sources and credits

主要学习路线参考：

- [datawhalechina/Agent-Learning-Hub](https://github.com/datawhalechina/Agent-Learning-Hub)

核心资料类别：

- Agent 设计：Anthropic Building Effective Agents、OpenAI Practical Guide to Building Agents。
- Tool calling：OpenAI Function Calling、Claude Tool Use、Gemini Function Calling。
- Coding agents：Claude Code、OpenAI Codex、learn-claude-code、claw0。
- Protocols：MCP、A2A、ACP。
- Eval and safety：OpenAI Evals、LangSmith、AgentBench、SWE-bench、AI Harness Engineering。

如果你基于本项目继续扩展学习路线，建议优先提交：

- 可运行项目任务。
- 更好的每日验收题。
- 新的 trace/eval/safety 实践。
- 面向中文学习者的解释和错误复盘。

## Contributing

欢迎提交 issue 或 PR，建议包含：

- 你希望优化的 Week / Day。
- 当前任务哪里不可执行。
- 你补充的官方来源或项目来源。
- 可运行代码、测试或失败复盘。

贡献原则：

- 不堆资料链接。
- 不引入无法执行的宏大计划。
- 不把旧式 role-play multi-agent 作为主线。
- 优先补齐项目闭环、测试、trace、eval 和安全边界。

## English

[中文](#ai-agent-工程化每日导师) | **English**

# AI Agent Engineering Daily Mentor

A Chinese-first AI Agent engineering skill that turns a modern Agent learning roadmap into weekly plans, daily 6-hour tasks, runnable projects, Obsidian-style linked notes, and job-ready project narratives.

Skill identifier: `ai-agent-engineering-mentor`

Display name: `AI Agent 工程化每日导师`

Repository: [github.com/Kcalb0708/ai-agent-engineering-mentor](https://github.com/Kcalb0708/ai-agent-engineering-mentor)

Latest version: [GitHub Releases](https://github.com/Kcalb0708/ai-agent-engineering-mentor/releases)

## Table of contents

- [Why this skill exists](#why-this-skill-exists)
- [At a glance](#at-a-glance-1)
- [Who it is for](#who-it-is-for)
- [Learning roadmap](#learning-roadmap)
- [Installation](#installation)
- [Quick start](#quick-start)
- [Daily output shape](#daily-output-shape)
- [Working modes](#working-modes)
- [Optional source links](#optional-source-links)
- [Repository layout](#repository-layout-1)
- [Design principles](#design-principles)
- [Sources and credits](#sources-and-credits-1)
- [Contributing](#contributing-1)
- [License](#license--许可证)

## Why this skill exists

Many AI Agent learning roadmaps become link collections. They contain plenty of resources, but they do not tell learners what to code today, what project to ship this week, or how to tell whether they are making real progress.

This skill turns a roadmap into an execution loop:

```text
Weekly outline
-> Daily 6-hour task
-> Runnable code
-> Self-check
-> Learning feedback
-> Adaptive next-day adjustment
-> Project packaging and interview narrative
```

The roadmap is based on and credits [datawhalechina/Agent-Learning-Hub](https://github.com/datawhalechina/Agent-Learning-Hub). That project emphasizes building useful, reliable agents instead of collecting random links. This skill converts its Stage 0-8 roadmap into a Chinese-first daily learning workflow.

## At a glance

| Capability | What it does |
| --- | --- |
| Weekly outline | Generates Week 1-8 learning plans with Day 1-Day 7 breakdowns |
| Daily teaching | Uses a default 5-module plan, while allowing users to rename, reorder, add, remove, or combine modules |
| Adaptive planning | Adjusts based on daily feedback: continue, slow down, extend, or reschedule |
| Code checkpoint review | Uses real code and validation evidence for a layered review after a checkpoint is completed |
| Project ladder | Moves from `Calculator Agent` to `Production-style Agent Project` |
| Obsidian links | Produces stable Chinese `[[...]]` links for concepts, modules, and interview notes |
| Optional sources | Adds official docs, specs, papers, or project README links near relevant concepts |
| Job packaging | Helps write project narratives, resume bullets, interview answers, and README improvements |

## Who it is for

- Chinese learners who want a structured path into modern AI Agent engineering.
- Developers with some Python knowledge but limited Agent project experience.
- Learners who want to understand Claude Code / Codex-style coding agents.
- Students or internship candidates who want a demonstrable, evaluable Agent project.
- Learners who want to connect daily study notes with an Obsidian knowledge base.

Not a good fit if you:

- Only want to collect links without writing code.
- Only want prompt role-play and do not care about tools, permissions, trace, or eval.
- Want to jump into complex multi-agent frameworks on day one.

## Learning roadmap

The roadmap references [Agent-Learning-Hub](https://github.com/datawhalechina/Agent-Learning-Hub) and rearranges it into an 8-week project ladder for Chinese learners.

| Week | Theme | Main output |
| --- | --- | --- |
| Week 1 | Python MUP + minimal Agent Loop | `Calculator Agent` |
| Week 2 | Tool Use + Web Research Agent | `Web Research Agent v1` |
| Week 3 | RAG + Memory + Citation | `PDF QA Agent` or `Knowledge Research Agent` |
| Week 4 | Coding Agent Harness study and rebuild | `Nano Coding Agent` |
| Week 5 | Supervisor / Graph / Reviewer | `Multi-Agent Writer` or `Coding Review Agent` |
| Week 6 | Skills + Protocols + Capability Packaging | `Reusable Skill Pack` |
| Week 7 | Browser Agent + Computer-use Safety | `Browser Agent` |
| Week 8 | Evaluation, Observability, Safety, Ship | `Production-style Agent Project` |

Recommended final project:

```text
NanoAgent: an auditable Coding Agent Harness for local codebases
```

Core loop:

```text
User task
-> Read project context
-> Select tool
-> Check permission
-> Execute safe tool
-> Record trace
-> Update session
-> Compact context if needed
-> Return result or failure reason
-> Validate with eval / smoke test
```

If your goal is an AI Agent application internship, you can also choose a business project:

```text
AI-Interview: a RAG + Agent powered mock interview system
```

It must include RAG citations, retrieval evaluation, agent trace, session, permission boundaries, tests, README, and failure records. It should not remain a simple RAG demo.

## Installation

This skill uses the standard `SKILL.md` directory layout and can be installed into hosts that support Agent Skills / SKILL.md.

| Host | Recommended path | Notes |
| --- | --- | --- |
| Codex | `~/.codex/skills/ai-agent-engineering-mentor` | For OpenAI Codex / Codex CLI |
| Claude Code | `~/.claude/skills/ai-agent-engineering-mentor` | Personal skill; project-level skills can live under `.claude/skills/` |
| cc-switch | `~/.cc-switch/skills/ai-agent-engineering-mentor` or `~/.agents/skills/ai-agent-engineering-mentor` | `~/.agents/skills` is better for sharing across tools |
| Hermes Agent | `~/.hermes/skills/ai-agent-engineering-mentor` | For Hermes local skills |

### Codex

Install from the canonical repository to avoid stale copies:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.codex/skills/ai-agent-engineering-mentor
```

Then trigger it in Codex:

```text
Use AI Agent 工程化每日导师 to generate a Week 1 outline.
```

Update to the latest version:

```bash
git -C ~/.codex/skills/ai-agent-engineering-mentor pull --ff-only
```

### Claude Code

Install as a personal global skill:

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.claude/skills/ai-agent-engineering-mentor
```

For a project-scoped skill, install it into the current repository:

```bash
mkdir -p .claude/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git .claude/skills/ai-agent-engineering-mentor
```

Update:

```bash
git -C ~/.claude/skills/ai-agent-engineering-mentor pull --ff-only
```

### cc-switch

Install into the default cc-switch skills directory:

```bash
mkdir -p ~/.cc-switch/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.cc-switch/skills/ai-agent-engineering-mentor
```

If you want multiple agent tools to share the same skill, install it into the shared community directory:

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.agents/skills/ai-agent-engineering-mentor
```

Update:

```bash
git -C ~/.cc-switch/skills/ai-agent-engineering-mentor pull --ff-only
```

### Hermes Agent

Install into the Hermes skills directory:

```bash
mkdir -p ~/.hermes/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.hermes/skills/ai-agent-engineering-mentor
```

Update:

```bash
git -C ~/.hermes/skills/ai-agent-engineering-mentor pull --ff-only
```

### Other agents with compatible skills

Copy this folder into the target agent's skills directory and make sure the folder name matches `name` in `SKILL.md`:

```text
ai-agent-engineering-mentor/
└── SKILL.md
```

If you installed it with Git, enter the skill directory and run:

```bash
git pull --ff-only
```

References:

- [OpenAI Codex Skills](https://developers.openai.com/codex/skills)
- [Claude Code Skills](https://code.claude.com/docs/en/skills)
- [cc-switch Skills](https://github.com/farion1231/cc-switch/blob/main/docs/user-manual/en/3-extensions/3.3-skills.md)
- [Hermes Agent Skills](https://hermes-agent.nousresearch.com/docs/user-guide/features/skills)

## Quick start

Generate the first weekly outline:

```text
使用 AI Agent 工程化每日导师，生成 Week 1 大纲。
我的基础：会一点 Python，但没系统做过 Agent 项目。
目标：8 周内做出可投递的 AI Agent 项目。
```

Generate Day 1:

```text
使用 AI Agent 工程化每日导师，根据 Week 1 大纲生成 Day 1 学习内容。
```

Submit daily feedback:

```text
【Day 1 学习反馈】
1. 今天实际学习时长：4 小时
2. 完成了哪些代码/文件：app/config.py、app/messages.py、app/tools/calculator.py
3. 哪个概念最清楚了：messages 结构
4. 哪个概念还没懂：Tool Schema
5. 卡住的 Bug / 报错全文：无
6. 自我验收题完成情况：2/3
7. 明天希望：正常推进
8. 后续每日模块偏好（留空=默认 5 模块；或填写保留/重命名/新增/删除/顺序）：
```

Generate Obsidian notes:

```text
使用 AI Agent 工程化每日导师，基于 Day 1 内容补全最重要的 3-5 个 Obsidian 知识点笔记。
```

## Daily output shape

Daily content uses these 5 top-level modules by default:

```markdown
📌 今日核心死磕
🎯 6小时精细化路线
💻 今日代码实战
🎯 每日自我验收题
📥 明日同步接口
```

The default works without extra setup. Users may customize retained, renamed, added, removed, and reordered modules in the weekly plan or feedback form. A custom profile must still cover goals, an executable path, code output, validation, and next-day feedback.

Code requirements:

- Type hints.
- Chinese comments.
- Meaningful error handling.
- No `pass`.
- No non-runnable pseudocode.
- Standard library and lightweight dependencies first; FastAPI, LangGraph, Playwright, and MCP SDK later when the roadmap reaches them.

## Working modes

This skill combines five common Agent Skill design patterns into multiple working modes:

| Mode | Pattern | Purpose |
| --- | --- | --- |
| Weekly outline | Generator + Inversion | Generate stable weekly plans and ask for missing goals when needed |
| Daily teaching | Pipeline + Generator | Follow the user's module profile, or use the default 5 modules |
| Feedback adjustment | Reviewer + Pipeline | Review feedback and project completeness before planning the next day |
| Code checkpoint review | Reviewer + Generator | Produce a layered review from real code and validation evidence after completion |
| Obsidian maintenance | Reviewer + Generator | Score links and generate 3-5 focused notes |
| Roadmap digestion | Tool Wrapper + Pipeline + Reviewer | Read external roadmaps and convert them into executable learning rules |

## Optional source links

This skill has digested a set of modern Agent learning materials, but it does not lock users into a single explanation. When a key concept appears, it provides a few optional source links near that concept.

Example:

```markdown
### [[Agent Loop]]: why it is not a normal workflow

The key idea of an agent loop is not "let the model think more". It is a controllable loop across observation, tool selection, tool execution, and result interpretation.

可选来源：[Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)、[OpenAI: A practical guide to building agents](https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/)
```

Rules:

- No more than about 5 external links per daily output.
- 1-2 links per concept, at most 3.
- Prefer official docs, specifications, paper abstracts, and high-quality project READMEs.
- Do not append links after the `📥 明日同步接口` template.

## Repository layout

```text
ai-agent-engineering-mentor/
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── skill-mode-patterns.md
    ├── 8-week-spine.md
    ├── weekly-outline-template.md
    ├── day1-seed.md
    ├── adaptation-policy.md
    ├── checkpoint-review-format.md
    ├── final-project-blueprint.md
    ├── internship-success-insights.md
    ├── obsidian-linking-policy.md
    ├── obsidian-note-maintenance-policy.md
    └── source-link-policy.md
```

## Design principles

### 1. The roadmap is not a link collection

Every day must end in code, a project artifact, a self-check, and feedback. Links are optional paths for deeper understanding.

### 2. Agent engineering first

The core line focuses on tool schema, permission gate, session store, context compaction, trace, eval, and safety instead of old role-play multi-agent patterns.

### 3. Code checkpoints must be reviewable

The layered review format is used only after a code checkpoint has been completed and validated. It must cite real code, tests, and design evidence; daily plans and general questions do not use this format.

### 4. Knowledge links must be stable

Obsidian links use stable Chinese names to avoid splitting the same concept across many aliases.

## Sources and credits

Primary roadmap reference:

- [datawhalechina/Agent-Learning-Hub](https://github.com/datawhalechina/Agent-Learning-Hub)

Core source categories:

- Agent design: Anthropic Building Effective Agents, OpenAI Practical Guide to Building Agents.
- Tool calling: OpenAI Function Calling, Claude Tool Use, Gemini Function Calling.
- Coding agents: Claude Code, OpenAI Codex, learn-claude-code, claw0.
- Protocols: MCP, A2A, ACP.
- Eval and safety: OpenAI Evals, LangSmith, AgentBench, SWE-bench, AI Harness Engineering.

If you extend this project, prioritize:

- Runnable project tasks.
- Better daily self-check questions.
- New trace/eval/safety practices.
- Chinese explanations and failure reviews for learners.

## Contributing

Issues and PRs are welcome. Please include:

- Which Week / Day you want to improve.
- What part of the current task is not executable.
- The official source or project source you are adding.
- Runnable code, tests, or failure records when possible.

Contribution principles:

- Do not dump links.
- Do not add grand plans that cannot be executed.
- Do not make role-play multi-agent the main path.
- Prioritize project closure, tests, trace, eval, and safety boundaries.

## License / 许可证

MIT
