# AI Agent 工程化每日导师

[![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)](#license)
[![Skill](https://img.shields.io/badge/Skill-Codex%20%2F%20Claude%20Code-blue)](#安装)
[![Language](https://img.shields.io/badge/Language-中文-red)](#适合谁)

一个中文 AI Agent 工程学习 skill：把现代 Agent 学习路线压成每周大纲、每日 6 小时任务、可运行项目、Obsidian 双链笔记和求职项目表达。

技能标识符：`ai-agent-engineering-mentor`

对外技能名：`AI Agent 工程化每日导师`

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
| 每日教学 | 固定输出 5 个模块，控制在 6 小时内完成 |
| 自适应调整 | 根据 Day 学习反馈判断正常推进、放慢复习、加难扩展或重排 |
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

### Codex

把本目录放到 Codex skills 目录，例如：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Kcalb0708/ai-agent-engineering-mentor.git ~/.codex/skills/ai-agent-engineering-mentor
```

然后在 Codex 中触发：

```text
使用 AI Agent 工程化每日导师，生成 Week 1 大纲
```

### Claude Code / 其他兼容 skills 的 agent

把本目录复制到对应 agent 的 skills 目录，并确保目录名与 `SKILL.md` 中的 `name` 一致：

```text
ai-agent-engineering-mentor/
└── SKILL.md
```

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
```

补全 Obsidian 笔记：

```text
使用 AI Agent 工程化每日导师，基于 Day 1 内容补全最重要的 3-5 个 Obsidian 知识点笔记。
```

## 每日输出结构

每日内容只输出 5 个顶层模块：

```markdown
📌 今日核心死磕
🎯 6小时精细化路线
💻 今日代码实战
🎯 每日自我验收题
📥 明日同步接口
```

代码要求：

- 有 Type Hints。
- 有中文注释。
- 有异常处理。
- 不使用 `pass`。
- 不给不可运行的伪代码。
- 早期优先标准库和轻量依赖，后期再引入 FastAPI、LangGraph、Playwright、MCP SDK 等。

## 工作模式

这个 skill 参考 Agent Skill 的 5 种设计模式组织：

| 工作模式 | 设计模式 | 用途 |
| --- | --- | --- |
| 每周大纲模式 | Generator + Inversion | 生成结构稳定的 Week 大纲，必要时先补问目标 |
| 每日教学模式 | Pipeline + Generator | 严格按 5 模块生成每日任务 |
| 周计划调整模式 | Reviewer + Pipeline | 审查反馈和项目完整度，再决定下一天任务 |
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

### 3. 输出要能复盘

每周产出物都要逐步补齐 README、测试、trace、eval、失败记录和面试表达。

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

## License

MIT
