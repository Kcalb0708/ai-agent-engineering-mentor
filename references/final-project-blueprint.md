# 最终项目蓝图：Modern Agent Project Ladder

本文件用于校准 Week 2-8 的学习大纲和每日内容。新版默认最终目标不是单一业务项目，而是一个能证明现代 AI Agent 工程能力的 project ladder。用户可以按时间和求职目标选择其中一个作为主项目。

## 项目选择原则

一个可展示的 agent 项目必须回答清楚：

- 用户是谁，任务是什么，成功标准是什么。
- 为什么需要 agent，而不是普通 workflow 或脚本。
- agent 能调用哪些工具，工具 schema 如何约束输入。
- 危险工具如何做权限确认。
- 状态、session、memory、trace 如何记录。
- 失败发生时如何定位：prompt、工具、检索、模型还是状态管理。
- 如何用 eval case 证明能力没有退化。
- 别人如何 clone、配置、运行、测试和扩展。

禁止把最终项目做成：

- 只调一次 LLM API 的脚本。
- 只有 prompt、没有工具和状态的 chatbot。
- 只有 RAG 问答、没有引用和评估的知识库。
- 只有多个角色互相聊天、没有职责边界和停止条件的 multi-agent demo。
- 没有 README、测试、trace、eval、失败记录和权限说明的演示项目。

## Project Ladder

### Level 1：Calculator Agent

学习目标：

- 最小 agent loop。
- tool schema。
- 参数校验。
- 工具结果回填。
- 最大步数和失败退出。

核心交付：

- `ToolRegistry`
- `AgentRunner`
- `calculator` 工具
- trace JSON
- smoke tests
- 5 条 eval case

适合 Week 1。

### Level 2：Web Research Agent

学习目标：

- 搜索、抓取、筛选、摘要。
- 引用来源。
- 工具失败处理。
- 多轮工具调用。

核心交付：

- `search` 工具
- `fetch_url` 工具
- `summarize_with_citations`
- trace
- README 限制说明
- 10 条 research eval case

适合 Week 2。

### Level 3：PDF QA Agent

学习目标：

- RAG、chunk、Embedding、retrieval、citation。
- 检索失败和幻觉引用处理。
- 检索质量评估。

核心交付：

- ingestion pipeline
- vector store
- retriever
- answer with citations
- retrieval eval
- 失败样例记录

适合 Week 3。

### Level 4：Coding Review Agent

学习目标：

- 读取 diff。
- 风险排序。
- 生成测试建议。
- 代码 review 输出结构。

核心交付：

- `read_diff` 工具
- `inspect_file` 工具
- review schema
- P0/P1/P2 风险排序
- trace
- review eval case

适合 Week 4 或 Week 5。

### Level 5：Browser Agent

学习目标：

- 页面观察、点击、提取。
- DOM、截图、动作日志。
- 页面变化和失败恢复。
- 安全边界。

核心交付：

- Playwright 或 browser-use harness
- 公开网页信息提取任务
- action log
- screenshot log
- recovery rules
- 安全限制文档

适合 Week 7。

### Level 6：Nano Coding Agent

学习目标：

- shell 工具。
- 文件读取和编辑建议。
- 权限确认。
- session。
- context compaction。
- trace 和回放。

核心交付：

- `ShellTool`
- `ReadFileTool`
- `SearchTool`
- `PatchSuggestionTool`
- permission gate
- session store
- compact summary
- trace replay

适合 Week 4-6，是最推荐的现代 agent 主项目。

### Level 7：OpenClaw-like Gateway

学习目标：

- channel。
- routing。
- session。
- memory。
- heartbeat。
- delivery。
- resilience。
- concurrency。

核心交付：

- message gateway
- session router
- memory store
- heartbeat task
- delivery retry
- audit log

适合进阶用户，不建议零基础直接上。

### Level 8：Reusable Skill Pack

学习目标：

- skill 与 tool/prompt/MCP 的区别。
- `SKILL.md` 结构。
- 资源渐进加载。
- 脚本和模板复用。
- smoke test 验证 skill 是否提升成功率。

核心交付：

- 一个完整 `SKILL.md`
- `scripts/`
- `templates/`
- 触发条件
- 验收标准
- smoke test
- 失败案例

适合 Week 6。

### Level 9：Multi-Agent Writer

学习目标：

- planner / writer / reviewer / reviser 协作。
- 角色边界。
- 输入输出 schema。
- 停止条件。
- supervisor 或 graph 编排。

核心交付：

- supervisor
- 3-4 个专用 agent
- schema
- trace
- dead-loop 防护
- review/revise eval case

适合 Week 5。

### Level 10：Production Harness

学习目标：

- evals。
- trace。
- 权限。
- CI。
- runner。
- 回放。
- human-in-the-loop。
- 安全风险文档。

核心交付：

- 20+ eval case
- trace dashboard 或 JSONL
- 权限配置
- smoke tests
- CI 或本地 test script
- README
- `.env.example`
- failure log
- safety notes

适合 Week 8，是最终包装标准。

## 推荐最终主项目

默认推荐用户选择 `Nano Coding Agent + Reusable Skill Pack + Production Harness` 作为主线。

原因：

- 最贴近 Claude Code / Codex-style coding agents。
- 能展示真实代码库、shell、文件编辑、测试、权限、上下文压缩、trace、eval。
- 面试时比普通 RAG Demo 更容易讲出工程深度。
- 可以和用户自己的学习 skill 形成闭环：一边学 agent，一边做 agent 能力包。

推荐最终项目名：

`NanoAgent：面向本地代码库的可审计 Coding Agent Harness`

## NanoAgent 核心闭环

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
-> eval/smoke test 验证
```

## NanoAgent 推荐技术栈

- Python 3.11+
- `httpx`
- `pydantic`
- `python-dotenv`
- `rich`
- `pytest`
- SQLite 或 JSONL session store
- FastAPI 可选，用于服务化
- LangGraph 可选，用于状态图编排
- MCP SDK 可选，用于协议化工具接入
- Docker Compose 可选，用于最终包装

## NanoAgent 核心模块

### 1. LLM Client

功能：

- OpenAI-compatible API 调用。
- timeout。
- retry。
- JSON/structured output 解析。
- 成本和耗时记录。

### 2. Tool Registry

功能：

- 注册工具名称、schema、描述和执行函数。
- 校验工具参数。
- 屏蔽不存在或未授权工具。

### 3. Permission Gate

功能：

- 按工具风险分级。
- 对 shell、文件写入、网络访问等操作做确认。
- 限制路径、命令和危险参数。

### 4. Session Store

功能：

- 保存用户输入、模型输出、工具调用、工具结果。
- 支持按 session 继续任务。
- 支持上下文压缩前后的状态保存。

### 5. Trace Logger

功能：

- 记录每一步 observe、decision、tool call、tool result、final answer。
- 记录耗时、错误、重试次数和失败分类。
- 支持 replay 或人工复盘。

### 6. Context Compaction

功能：

- 当上下文过长时生成结构化摘要。
- 保留任务目标、已读文件、关键决策、未完成事项和风险。

### 7. Eval Runner

功能：

- 读取固定 eval cases。
- 执行 agent。
- 记录实际输出、工具调用次数、是否成功、失败分类。
- 输出简单报告。

### 8. Skill Pack

功能：

- 把 code review、research report、migration helper 等流程打包为可复用 skill。
- 每个 skill 包含触发条件、步骤、模板、脚本和 smoke test。

## 分周落地方式

- Week 1：Calculator Agent，完成最小 agent loop。
- Week 2：Web Research Agent，加入搜索、抓取、引用和 trace。
- Week 3：PDF QA Agent，完成 RAG、citation 和检索评估。
- Week 4：Nano Coding Agent v1，完成 tool registry、read/search/shell、permission gate。
- Week 5：Coding Review Agent 或 Multi-Agent Writer，学习 reviewer/supervisor/schema/stop condition。
- Week 6：Reusable Skill Pack + MCP/A2A/ACP 理解，完成一个可复用 skill。
- Week 7：Browser Agent，完成公开网页自动化、动作日志和失败恢复。
- Week 8：Production Harness 包装，补 eval、trace、README、测试、权限、安全和简历话术。

## 可选业务项目：AI-Interview

如果用户明确目标是 AI Agent 应用开发实习，也可以选择：

`AI-Interview：基于 RAG 与 Agent 的智能模拟面试系统`

新版要求它必须包含：

- 业务闭环：`简历解析 -> 岗位匹配 -> RAG 出题 -> 模拟面试 -> AI 评分 -> 面试报告`。
- Agent 工程闭环：tool schema、permission gate、session、trace、eval、失败记录。
- RAG 工程闭环：chunk、embedding、retrieval、citation、检索评估。
- 项目包装：README、Docker、`.env.example`、测试、接口示例、限制说明。

## 面试表达要点

面试时必须能讲清：

- 这个项目为什么需要 agent，而不是普通 workflow。
- agent loop 如何组织：观察、决策、工具调用、结果回填、最终输出。
- tool schema 如何减少不确定性。
- permission gate 如何避免危险操作。
- trace 如何帮助定位失败。
- eval 如何证明改动没有让能力退化。
- RAG 在项目里如何保证引用和可追溯。
- multi-agent 为什么是协调问题，不是角色扮演。
- 项目如何从 Demo 变成可投递作品：可运行、可复现、可评测、可扩展、可解释。
