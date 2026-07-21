# Obsidian 双链输出规范

本文件用于让每周大纲和每日内容适合放进 Obsidian 学习。默认启用，除非用户明确要求“不要 Obsidian 链接”。

## 基本规则

- 使用 Obsidian 双链格式：`[[Python 异步编程]]`。
- 技术概念首次出现时优先加双链，避免全文过度链接。
- 每日内容必须在当前“每日模块配置”内部加入链接，不得为了放链接额外创建顶层模块。
- 代码块内部禁止出现 `[[...]]`，避免影响复制运行。
- 文件名、命令、API 路径、环境变量使用反引号，例如 `main.py`、`python -m venv .venv`、`/api/v1/chat`、`LLM_API_KEY`，不要转成双链。
- 链接标题使用中文稳定命名；技术英文名可保留在中文标题中，例如 `[[OpenAI-compatible API]]`。

## 每日内容链接要求

下面按模块承担的语义职责规定链接位置。括号中的名称是默认 5 模块映射；用户重命名、合并、重排或增删模块后，按职责而不是固定标题选择位置。

### 核心知识模块（默认 `📌 今日核心死磕`）

- 每个核心技术点标题或首段放 1-3 个双链。
- 链接必须指向当天最核心的概念，不要堆链接。

### 学习路径模块（默认 `🎯 6小时精细化路线`）

- 上午、下午、晚上每个时间段至少关联 1 个双链。
- 链接应指向当天要学习或产出的知识点。

### 代码实践模块（默认 `💻 今日代码实战`）

- 代码块前增加一行：

`关联知识：[[知识点 A]]、[[知识点 B]]、[[知识点 C]]`

- 关联知识数量控制在 3-5 个。
- 代码块内不要出现双链。

### 验收模块（默认 `🎯 每日自我验收题`）

- 题目中可以引用相关双链，帮助跳转复习。
- 不要为了链接牺牲题目难度。

### 次日反馈接口（默认 `📥 明日同步接口`）

- 保持固定反馈模板。
- 模板后不得添加任何链接或说明。

## 每周大纲链接要求

- `核心技术拆解` 中每个技术点写 `关联笔记：[[...]]`。
- `每日精细化学习路径` 中每个 Day 增加 `关联知识：[[...]]、[[...]]`。
- `本周核心产出物` 中加入 `推荐建立的 Obsidian 笔记`。
- 不新增顶层模块，只在现有模块内部增加链接信息。

## 知识点补全优先级

双链不代表必须立刻生成完整笔记。每天只补最重要的 3-5 个知识点，避免知识库膨胀。

### P0：必须生成或更新

- 当天核心知识模块的核心概念。
- 当天代码实践模块依赖的关键概念。
- 本周项目核心模块。
- 高频/核心 Python 基础知识。
- Agent 工程主链路概念，例如 `[[Agent Loop]]`、`[[Tool Registry]]`、`[[Permission Gate]]`、`[[Trace 与回放]]`。

### P1：建议生成或更新

- 每日验收题涉及的概念。
- 常见 Bug 和排查相关概念。
- 本周会反复出现的工程概念。
- 当前项目的 README、eval、权限、安全和失败复盘概念。

### P2：暂时只保留双链

- 辅助背景概念。
- 只在相关链接中出现一次的低频概念。
- 暂时不会影响当天代码运行和项目推进的概念。

限制：

- 不要求一次性补全所有双链。
- 不为低频概念制造空笔记。
- 不生成同义词重复笔记。
- Python 基础知识允许比其他知识点更详细，具体规则见 `obsidian-note-maintenance-policy.md`。

## 稳定命名规则

优先复用稳定标题，不要每天创造同义词。

### Python 基础笔记

- `[[Python MUP]]`
- `[[Python 函数]]`
- `[[Python 类型注解]]`
- `[[异常处理]]`
- `[[JSON 文件读写]]`
- `[[pathlib 文件路径]]`
- `[[Python 虚拟环境]]`
- `[[环境变量与 API Key]]`
- `[[Python 异步编程]]`
- `[[asyncio.gather 并发]]`
- `[[装饰器]]`

### HTTP 与 LLM 基础笔记

- `[[HTTP 请求结构]]`
- `[[HTTP 状态码]]`
- `[[RESTful API 设计]]`
- `[[JSON API]]`
- `[[httpx 异步请求]]`
- `[[API 超时处理]]`
- `[[OpenAI-compatible API]]`
- `[[LLM messages 结构]]`
- `[[结构化输出]]`
- `[[Prompt Engineering]]`

### Agent 核心概念笔记

- `[[Workflow 与 Agent 边界]]`
- `[[Agent Loop]]`
- `[[Agent 停止条件]]`
- `[[Function Calling]]`
- `[[Tool Schema]]`
- `[[工具参数校验]]`
- `[[工具结果回填]]`
- `[[工具失败处理]]`
- `[[Tool Registry]]`
- `[[Permission Gate]]`
- `[[Session Store]]`
- `[[Memory 记忆机制]]`
- `[[Context Compaction]]`
- `[[Trace 与回放]]`
- `[[Agent Eval]]`
- `[[Human-in-the-loop]]`
- `[[Prompt Injection]]`
- `[[Data Exfiltration]]`
- `[[Tool Abuse]]`

### RAG 与 Research Agent 笔记

- `[[RAG 检索增强生成]]`
- `[[Embedding 向量化]]`
- `[[Chunk 文档切分]]`
- `[[Vector Store]]`
- `[[Hybrid Search]]`
- `[[Rerank 重排序]]`
- `[[Citation 引用来源]]`
- `[[检索评估]]`
- `[[Web Research Agent]]`
- `[[PDF QA Agent]]`
- `[[Deep Research]]`

### Harness 与 Coding Agent 笔记

- `[[Agent Harness]]`
- `[[Coding Agent]]`
- `[[Claude Code]]`
- `[[OpenAI Codex]]`
- `[[Nano Coding Agent]]`
- `[[Shell Tool]]`
- `[[Read File Tool]]`
- `[[Search Tool]]`
- `[[Patch Suggestion Tool]]`
- `[[命令白名单]]`
- `[[路径权限限制]]`
- `[[Audit Log]]`

### Multi-Agent 与 Graph 笔记

- `[[Multi-Agent 协调]]`
- `[[Planner Executor Reviewer]]`
- `[[Supervisor Agent]]`
- `[[LangGraph 状态图]]`
- `[[条件路由]]`
- `[[循环终止条件]]`
- `[[Agent 输入输出 Schema]]`

### Skills、协议和能力打包笔记

- `[[Skills 能力打包]]`
- `[[Skill 与 Tool 区别]]`
- `[[Skill 与 Prompt 区别]]`
- `[[MCP 协议]]`
- `[[MCP Tools Resources Prompts]]`
- `[[A2A 协议]]`
- `[[ACP 协议]]`
- `[[Skill Smoke Test]]`
- `[[SWE-Skills-Bench]]`

### Browser / Computer-use 笔记

- `[[Browser Agent]]`
- `[[Computer-use Agent]]`
- `[[Playwright 自动化]]`
- `[[DOM Snapshot]]`
- `[[Action Log]]`
- `[[Screenshot Trace]]`
- `[[页面失败恢复]]`
- `[[WebArena]]`

### 工程笔记

- `[[FastAPI 项目结构]]`
- `[[FastAPI 路由]]`
- `[[Pydantic 数据校验]]`
- `[[PostgreSQL 数据建模]]`
- `[[Redis 缓存]]`
- `[[Celery 异步任务]]`
- `[[Docker Compose 部署]]`
- `[[pytest 基础]]`
- `[[Mock 测试思路]]`
- `[[Git 基础命令]]`
- `[[Git 提交规范]]`
- `[[.gitignore 配置]]`
- `[[README 编写]]`
- `[[.env.example 配置]]`

### 项目笔记

- `[[Calculator Agent 项目总览]]`
- `[[Web Research Agent 项目总览]]`
- `[[PDF QA Agent 项目总览]]`
- `[[Coding Review Agent 项目总览]]`
- `[[Browser Agent 项目总览]]`
- `[[NanoAgent 项目总览]]`
- `[[Reusable Skill Pack 项目总览]]`
- `[[Production Harness 项目总览]]`
- `[[AI-Interview 项目总览]]`
- `[[面试题库 RAG]]`
- `[[岗位匹配 Agent]]`
- `[[AI 评分 Prompt]]`

### 面试笔记

- `[[AI Agent 面试题]]`
- `[[个人优势写法]]`
- `[[项目经历写法]]`
- `[[AI 应用工程化面试]]`
- `[[RAG 面试题]]`
- `[[Agent 面试题]]`
- `[[Coding Agent 面试题]]`
- `[[Agent Harness 面试题]]`
- `[[Agent Eval 面试题]]`

### 错题与 Bug 复盘笔记

- `[[Bug 复盘 - JSON 解析错误]]`
- `[[Bug 复盘 - 环境变量未读取]]`
- `[[Bug 复盘 - httpx 请求超时]]`
- `[[Bug 复盘 - asyncio 事件循环错误]]`
- `[[Bug 复盘 - FastAPI 422 错误]]`
- `[[Bug 复盘 - Tool Schema 校验失败]]`
- `[[Bug 复盘 - Agent 无限循环]]`
- `[[Bug 复盘 - 工具重复调用]]`
- `[[Bug 复盘 - RAG 引用幻觉]]`
- `[[Bug 复盘 - 浏览器元素定位失败]]`

## 示例

正确：

`关联知识：[[Agent Loop]]、[[Tool Schema]]、[[Trace 与回放]]`

错误：

`关联知识：[[agent循环]]、[[工具schema]]、[[追踪日志]]`

原因：同义词太多会让 Obsidian 笔记分裂，后期难以维护。
