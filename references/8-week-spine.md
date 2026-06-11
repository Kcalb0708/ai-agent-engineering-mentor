# 8 阶段现代 AI Agent 工程学习主线

这是全局骨架，只负责保证长期方向不跑偏。每一周实际执行前，必须先生成一个中文每周学习大纲；每日学习内容不能只参考本文件，必须优先参考“当前周大纲”和用户每日反馈。

本主线来自 `Agent Learning Hub` 的最新学习路线，重点从旧式“角色扮演多 agent 框架”转向更贴近真实生产力的现代 agent engineering：coding agent、agent harness、skills、MCP、trace、eval、权限和安全。

优先级：

1. 用户最新学习反馈。
2. 当前周中文学习大纲。
3. 本文件的 8 阶段主线。
4. 项目阶梯和最终交付标准。
5. 默认技术栈与导师经验。

## Phase 1：Stage 0-1

目标：理解 agent 边界，并实现一个最小可运行 agent loop。

### Week 1：Python MUP + 最小 Agent Loop

本周核心产出物：`Calculator Agent`。

主线：

- Day 1：Python 工程环境、messages 结构、最小工具函数。
- Day 2：HTTP、LLM API、结构化 JSON 输出。
- Day 3：工具 schema 与 function calling。
- Day 4：实现单步 tool call loop。
- Day 5：加入最大步数、超时、错误处理和工具失败反馈。
- Day 6：重构 tool registry、trace 日志和命令行入口。
- Day 7：测试、README、复盘和 agent/workflow 边界表达。

必须掌握：

- chatbot、workflow、agent、multi-agent 的区别。
- 什么时候不该用 agent。
- `observe -> think -> act -> observe -> final` 的基本循环。
- tool schema、参数校验、工具执行、工具结果回填。
- 最大步数、超时、异常、失败退出。

### Week 2：Tool Use + Web Research Agent

本周核心产出物：`Web Research Agent v1`。

主线：

- `httpx` 异步请求。
- 搜索/抓取工具的抽象。
- 资料筛选、引用来源、摘要生成。
- 工具失败、空结果、重复调用处理。
- trace 记录：每一步为什么调用了哪个工具。
- README 写清输入输出、限制和失败样例。

必须避免：

- 只做“调一次搜索 API 再总结”的脚本。
- 引用来源不可追踪。
- 工具失败时直接编造答案。

## Phase 2：Stage 2

目标：掌握 RAG、memory、工具组合和引用输出。

### Week 3：RAG + Memory + Citation

本周核心产出物：`PDF QA Agent` 或 `Knowledge Research Agent`。

主线：

- 文档导入、切分、Embedding、向量入库。
- 检索、答案生成、引用来源。
- 短期上下文、会话记忆、长期记忆的区别。
- 检索失败、空结果、幻觉引用处理。
- 检索评估：命中率、引用是否支持答案、失败分类。

可选框架：

- 早期可用 Chroma 降低门槛。
- 需要服务化时用 FastAPI 包一层 API。
- 对比 LlamaIndex 和 LangChain 时，重点看数据流，不背 API。

## Phase 3：Stage 3

目标：学习一个现代 agent harness，理解能力来自 harness，而不只是模型和 prompt。

### Week 4：Coding Agent Harness 拆解与复刻

本周核心产出物：`Nano Coding Agent`。

主线：

- 读懂一个现代 harness 的目录结构。
- 找出 agent loop、tool registry、permission gate、session store、context compaction。
- 复刻最小 shell/file agent：读文件、搜索、编辑建议、运行测试。
- 加入工具权限确认、路径限制、命令白名单、trace 日志。
- 对比裸 agent loop 和 harness 的差异。

重点参考：

- Claude Code / Codex-style coding agents。
- learn-claude-code。
- claw0。
- OpenClaw。
- LangGraph。

验收重点：

- 不能只会调用框架 API；必须能解释 harness 的入口、状态、工具、权限、输出和失败路径。

## Phase 4：Stage 4

目标：把 multi-agent 理解成协调和边界问题，而不是角色扮演。

### Week 5：Supervisor / Graph / Reviewer

本周核心产出物：`Multi-Agent Writer` 或 `Coding Review Agent`。

主线：

- planner / executor / reviewer / critic / router 的职责边界。
- 每个 agent 的输入输出 schema。
- 停止条件、循环限制、争论终止。
- 用 supervisor 或 graph 管理多 agent。
- 观察 trace，解释每一步为什么发生。

必须避免：

- 让多个 agent 自由聊天。
- 没有明确交付物、停止条件和错误处理。
- 用“角色名称”替代工程边界。

## Phase 5：Stage 5

目标：理解 skills、MCP、A2A、ACP 和能力打包。

### Week 6：Skills + Protocols + Capability Packaging

本周核心产出物：`Reusable Skill Pack`。

主线：

- Skill 与 Tool 的区别：tool 是可调用接口，skill 是可复用流程知识。
- Skill 与 Prompt 的区别：prompt 是一次性指令，skill 是可发现、可版本化、可分发的能力包。
- Skill 与 MCP 的区别：MCP 接外部工具/数据源，skill 告诉 agent 如何完成一类任务。
- MCP 的 client/server、tools、resources、prompts。
- A2A 的 agent 发现、任务、消息、协作。
- ACP 的编辑器/终端/IDE 与 agent 接口。
- 写一个最小 `SKILL.md`，加脚本、模板和 smoke test。

验收重点：

- skill 必须有清晰触发条件、步骤、资源加载策略、验证方式。
- 不写“万能 prompt 噪声”。
- 能说明这个 skill 如何提升任务成功率。

## Phase 6：Stage 6

目标：构建安全可复盘的 browser/computer-use agent。

### Week 7：Browser Agent + Computer-use Safety

本周核心产出物：`Browser Agent`。

主线：

- 浏览器 agent 与普通 API tool 的区别。
- 用 Playwright 或 browser-use 做公开网页观察、点击、提取。
- 记录 DOM、截图、动作日志、失败原因。
- 处理页面变化、弹窗、加载失败、元素定位失败。
- 加安全限制：不登录敏感账号、不越权、不绕过平台规则。

验收重点：

- 必须能复盘一次完整动作链。
- 必须有失败恢复和人工确认点。
- 只操作公开网页和允许自动化的场景。

## Phase 7：Stage 7-8

目标：把 agent 从 demo 推到可运行、可评测、可展示。

### Week 8：Evaluation, Observability, Safety, Ship

本周核心产出物：`Production-style Agent Project`。

主线：

- 准备固定 eval 数据集，至少 20 个任务。
- 记录成功率、失败原因、工具调用次数、成本、延迟。
- 看 trace，定位失败发生在 prompt、工具、检索、模型还是状态管理。
- 给危险工具加人工确认，例如发邮件、删文件、付款、发布内容。
- 整理 prompt injection、data exfiltration、tool abuse 风险。
- README 写清运行、配置、扩展工具、限制、eval、trace、失败样例。

最终交付必须包含：

- 一个别人能 clone 下来跑的 agent 项目。
- `.env.example`。
- `README.md`。
- 至少一组 smoke tests。
- 至少 20 条 eval case。
- trace 或日志样例。
- 权限边界说明。
- 失败记录和改进方向。
- 简历项目话术和面试问答。

## 可选求职项目：AI-Interview

如果用户明确目标是 AI Agent 应用开发实习，可以选择 `AI-Interview：基于 RAG 与 Agent 的智能模拟面试系统` 作为业务型项目。

但新版要求：

- RAG 必须服务于题库检索、参考答案、关键评分点和引用来源。
- Agent 必须服务于岗位匹配、面试流程编排、工具调用和报告生成。
- 必须补齐 trace、eval、权限边界、README、测试、Docker 和失败记录。
- 不能只做“知识库问答”或“多工具 Agent Demo”。
