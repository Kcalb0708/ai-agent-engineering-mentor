# AI Agent 实习准备重点：现代 Agent 工程版

本文件用于把 AI Agent 应用开发实习准备转化为 skill 的求职导向规则。生成 Week 6-8、项目规划、简历话术、个人优势和面试冲刺内容时必须参考。

新版求职重点不再只是“会 RAG + 会 LangChain Agent”，而是能展示现代 agent engineering 能力：coding agent、agent harness、tool schema、permission、trace、eval、skills、MCP、browser automation 和安全边界。

## 个人优势写法规则

个人优势不是泛泛夸自己，而是根据岗位要求逐条对齐。

写法：

- 先观察大量岗位要求，总结通用能力。
- 每条优势对齐一个岗位要求。
- 用“能力 + 技术栈 + 可落地场景 + 工程证据”表达。

推荐优势方向：

1. 具备 AI Agent 应用落地能力，理解 chatbot、workflow、agent 和 multi-agent 的边界，能从最小 agent loop 开始实现工具调用、状态管理、失败处理和最终输出。
2. 具备 Python 后端开发能力，熟悉 FastAPI、Pydantic、异步 HTTP、数据库和测试，能够完成接口设计、后端业务开发与系统联调。
3. 具备 agent harness 工程意识，理解 tool registry、permission gate、session store、context compaction、trace 和 eval 在 agent 系统中的作用。
4. 具备 RAG 工程能力，能完成 chunk、embedding、retrieval、citation、检索失败处理和基础检索评估，不只做普通知识库问答。
5. 具备现代 agent 协议和能力打包意识，了解 skills、MCP、A2A、ACP 的定位，能把常见任务封装成可复用 skill 或工具接口。
6. 熟练使用 Claude Code、OpenAI Codex、Cursor 等 AI 编程工具，能结合 AI 完成需求分析、代码开发、调试、重构和测试。
7. 具备 agent 安全和质量意识，能为高风险工具设置人工确认、路径/命令限制，并用 trace/eval 定位失败和防止能力退化。

## 面试考察五象限

AI 应用开发实习的面试通常来自五个方面：

- Python 后端基础：函数、类型注解、异常、异步、装饰器、文件处理、FastAPI、数据库、测试。
- LLM 应用基础：messages、Prompt、结构化输出、Function Calling、RAG、Embedding、Memory。
- Agent 工程能力：agent loop、tool schema、tool registry、permission gate、session、trace、eval、context compaction。
- AI 应用工程化：配置、日志、Docker、Redis/Celery、CI、README、部署、成本和延迟。
- 你的 AI Agent 项目：业务流程、技术选型、难点、失败处理、安全边界、评估结果和可展示程度。

判断：

- 大厂可能考算法和系统设计。
- 中小厂通常更看技术栈、项目和 AI 编程效率。
- 现在普通 RAG Demo 已经不够，能讲清 agent harness 和 eval/safety 更有区分度。

## 岗位画像

工作内容一般是“全栈 + AI + Agent 工程”，工作方式偏 AI-assisted coding。

技术要求通常不是纯 AI，也不是纯后端，而是：

- Python 后端。
- LLM API 和工具调用。
- RAG 和检索工程。
- Agent loop / workflow / harness。
- 能借助 AI 编程工具快速完成业务需求。
- 能把 demo 包装成可运行、可复现、可评测的项目。

## 项目选择原则

不要只做单独 Agent 项目，也不要只做单独 RAG 项目。这样的项目太普通。

更好的项目有两类：

### 1. 工程型项目：NanoAgent

适合展示现代 agent engineering。

推荐闭环：

`用户任务 -> 读取上下文 -> 选择工具 -> 权限检查 -> 执行工具 -> 记录 trace -> 更新 session -> 输出结果 -> eval 验证`

优点：

- 贴近 Claude Code / Codex-style coding agents。
- 能讲 tool registry、permission、session、trace、eval。
- 适合展示工程深度和 AI 编程工具理解。

### 2. 业务型项目：AI-Interview

适合投递 AI 应用开发实习。

推荐闭环：

`简历解析 -> 岗位匹配 -> RAG 出题 -> 模拟面试 -> AI 评分 -> 面试报告`

新版要求：

- 同时包含 RAG 和 Agent。
- RAG 有 citation 和检索评估。
- Agent 有 tool schema、trace 和失败处理。
- README 能证明项目不是普通 Demo。

## 项目经历写法参考：NanoAgent

项目名：

`NanoAgent：面向本地代码库的可审计 Coding Agent Harness`

项目简介：

面向本地代码库开发场景设计的轻量级 Coding Agent Harness，围绕“用户任务 -> 工具选择 -> 权限确认 -> 文件/命令工具执行 -> trace 记录 -> eval 验证”构建可审计的 agent 执行闭环。

技术实现要点：

- 基于 Python + Pydantic 设计 tool schema 和 tool registry，支持 read/search/shell 等工具注册、参数校验和结构化工具结果返回。
- 实现 permission gate，对 shell、文件写入和网络访问等高风险操作做路径限制、命令白名单和人工确认。
- 实现 session store 和 trace logger，记录每一步模型决策、工具调用、工具结果、耗时、异常和失败分类，支持复盘和调试。
- 实现 context compaction，在上下文过长时保留任务目标、已读文件、关键决策、未完成事项和风险。
- 构建 eval runner，维护固定任务集，统计成功率、工具调用次数、失败原因和回归情况。
- 使用 README、`.env.example`、pytest、smoke tests 和失败记录完成项目包装，保证别人能 clone 后运行。

面试可讲亮点：

- 不是只调用 LLM API，而是做了 agent harness 的关键工程环节。
- 权限边界和 trace 让 agent 行为可控、可解释、可复盘。
- eval case 让 prompt、工具或模型改动后可以观察能力是否退化。
- 通过 skill pack 把重复任务沉淀为可复用能力。

## 项目经历写法参考：AI-Interview

项目名：

`AI-Interview：基于 RAG 与 Agent 的智能模拟面试系统`

项目简介：

面向求职场景设计的 AI 模拟面试系统，围绕“简历解析 -> 岗位匹配 -> RAG 出题 -> 模拟面试 -> AI 评分 -> 面试报告”构建完整闭环，并加入 trace、eval 和工程化包装。

技术实现要点：

- 基于 FastAPI + PostgreSQL + Redis/Celery 搭建后端，完成岗位匹配、面试流程、题库管理等核心服务。
- 接入 DeepSeek API 或 OpenAI-compatible API，实现简历解析、候选人画像提取、面试题生成、回答评分与面试报告输出。
- 基于 Embedding + pgvector 或 Chroma 实现题库 RAG，支持题目向量化、检索、筛选、引用来源和检索评估。
- 基于 Tool Calling Agent 实现岗位匹配和面试流程编排，记录工具调用、失败原因和用户 session。
- 在评分阶段将 `reference_answer` 与 `key_points` 注入 Prompt，提升 AI 评分稳定性和可解释性。
- 使用 Docker Compose 管理 PostgreSQL、Redis、FastAPI、Celery 等服务，完成本地多服务联调与部署。

面试可讲亮点：

- RAG 不是普通问答，而是服务于面试题检索、参考答案和关键评分点。
- Agent 不是角色扮演，而是用于岗位匹配、流程编排和工具调用。
- trace/eval 让系统可以复盘失败并持续改进。

## 高频面试问答方向

必须准备：

- 什么时候该用 agent，什么时候 workflow 更好？
- 你实现的 agent loop 长什么样？
- tool schema 如何减少模型输出不确定性？
- 工具失败后怎么处理？
- 如何防止 agent 无限循环？
- permission gate 解决什么问题？
- trace 里记录哪些字段？
- eval case 怎么设计？
- RAG 如何避免幻觉引用？
- multi-agent 为什么不是多个角色自由聊天？
- skill 和 tool、prompt、MCP 的区别是什么？
- browser agent 有哪些安全限制？

## 投递建议

- 简历中直接放 GitHub 链接。
- README 必须写清楚项目背景、架构、启动方式、配置、示例输入输出、trace 样例、eval 结果、已知限制。
- 如果有在线演示链接、截图或录屏，面邀概率会明显提高。
- 项目介绍不要只写“使用 LangChain / LangGraph”，要写清你自己实现或理解的工程边界。
- 优先展示能运行、能复盘、能评估的项目，而不是堆很多框架名。
