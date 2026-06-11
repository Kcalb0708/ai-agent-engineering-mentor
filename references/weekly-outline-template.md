# 每周学习大纲模板

生成每周大纲时必须使用中文，并按下面结构输出。不要生成英文版。

每周大纲的职责是把长期路线压成 7 天可执行任务。它不是资料索引，也不是概念清单。每一天都必须有明确代码产出、运行检查点和项目位置。

## 固定结构

~~~markdown
# 📅 Week N：本周主题

## 1. 核心技术拆解

### 技术点 A

具体说明：

- 学什么
- 为什么对 Agent 工程重要
- 本周用在哪里
- 常见错误认知
- 关联笔记：[[稳定笔记标题]]、[[另一个稳定笔记标题]]
- 可选来源：[来源名](URL)、[来源名](URL)

## 2. 每日精细化学习路径

### Day 1：【类型】主题

关联知识：[[相关知识点 A]]、[[相关知识点 B]]

学习内容：

- ...

今天写什么：

1. ...

微练习：

```python
# 可运行或可临摹的核心代码
```

验收标准：

- ...

## 3. 本周核心产出物

### 项目名称

目录结构、核心功能、关键代码、trace/eval/权限/测试要求、简历话术、面试可讲亮点。

推荐建立的 Obsidian 笔记：

- [[项目总览]]
- [[核心模块设计]]
- [[Agent Trace]]
- [[面试表达]]

## 4. 面试仿真模拟

至少 4 个本周相关面试问答，必须覆盖本周项目实现、agent 工程边界、失败处理和求职表达。

## 5. 避坑指南

列出本周最容易浪费时间或走偏的点，尤其提醒不要做无法复现、无法评测、没有权限边界的孤立 Demo。
~~~

## Week 1 标准样例：Python MUP + 最小 Agent Loop

Week 1 的大纲必须参考以下内容生成。

### 固定主题

`Week 1：Python MUP + 最小 Agent Loop`

### 核心技术拆解

Python MUP 只死磕：

- 函数：参数、返回值、默认参数、`*args`、`**kwargs`
- 类型注解：`str`、`int`、`list[str]`、`dict[str, Any]`、`Optional`
- 异常处理：`try / except / raise`
- 文件处理：`pathlib`、JSON 读写
- 面向对象：`class`、`__init__`、实例方法、组合
- 装饰器：理解日志、计时和工具注册的基础
- 异步编程：`async def`、`await`、`asyncio.gather`
- 环境变量：`.env`、API Key 管理

关联笔记：[[Python MUP]]、[[Python 函数]]、[[Python 类型注解]]、[[异常处理]]、[[JSON 文件读写]]、[[环境变量与 API Key]]

可选来源：[Python 官方文档](https://docs.python.org/3/)

Agent 基础必须掌握：

- chatbot、workflow、agent、multi-agent 的区别
- agent 的基本循环：`observe -> think -> act -> observe`
- messages 结构：`system / user / assistant / tool`
- 结构化 JSON 输出
- tool schema、参数校验、工具执行、工具结果回填
- 最大步数、超时、工具失败和退出条件

关联笔记：[[Agent Loop]]、[[Workflow 与 Agent 边界]]、[[LLM messages 结构]]、[[结构化输出]]、[[Function Calling]]、[[Tool Schema]]

可选来源：[Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)、[OpenAI: A practical guide to building agents](https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/)

HTTP 和 API 必须掌握：

- GET、POST、Header、Body、JSON 请求体
- 状态码：`200`、`201`、`400`、`401`、`403`、`404`、`422`、`500`
- `httpx.Client` 和 `httpx.AsyncClient`
- timeout、`response.raise_for_status()`、网络异常

关联笔记：[[HTTP 请求结构]]、[[HTTP 状态码]]、[[httpx 异步请求]]、[[API 超时处理]]、[[OpenAI-compatible API]]

可选来源：[OpenAI Function Calling](https://platform.openai.com/docs/guides/function-calling)

Git 和工程化必须掌握：

- `git init`
- `git status`
- `git add`
- `git commit`
- `git log`
- `git diff`
- `.gitignore`
- 分支命名：`feature/week1-calculator-agent`
- commit 格式：`feat: add calculator agent loop`

关联笔记：[[Git 基础命令]]、[[Git 提交规范]]、[[.gitignore 配置]]、[[README 编写]]

### Day 1：Python 工程环境、messages 与最小工具函数

关联知识：[[Python 虚拟环境]]、[[环境变量与 API Key]]、[[LLM messages 结构]]、[[Tool Schema]]

学习内容：

- Python 虚拟环境
- `.env`
- 函数、类型注解、异常处理
- `pathlib`
- JSON messages 保存
- 一个 `calculator` 工具函数

今天写什么：

1. 创建项目目录：`week1_calculator_agent`
2. 创建虚拟环境
3. 安装依赖：`httpx python-dotenv rich pydantic`
4. 写 `app/config.py` 读取 `.env`
5. 写 `app/messages.py` 保存和读取 messages
6. 写 `app/tools/calculator.py` 实现安全的加减乘除工具
7. 写 `main.py` 做本地最小验证

微练习：

```python
from typing import Literal


def calculate(op: Literal["add", "sub"], a: float, b: float) -> float:
    if op == "add":
        return a + b
    if op == "sub":
        return a - b
    raise ValueError(f"不支持的操作: {op}")
```

验收标准：

- 能读取 `.env`
- 能保存 messages JSON
- 能调用 calculator 工具
- 能解释为什么 API Key 不能硬编码
- 完成一次 Git commit

### Day 2：HTTP、LLM API 与结构化 JSON 输出

关联知识：[[HTTP 请求结构]]、[[OpenAI-compatible API]]、[[结构化输出]]、[[API 超时处理]]

学习内容：

- HTTP 请求结构
- OpenAI-compatible chat API
- messages 结构
- 让模型输出 JSON
- API timeout 和异常处理

今天写什么：

1. 用 `httpx` 请求一个公开 API
2. 封装同步 `LLMClient`
3. 支持 `chat(messages: list[dict[str, str]]) -> str`
4. 写一个 `ask_json()`，要求模型返回 JSON
5. 对 JSON 解析失败给出清晰错误

验收标准：

- 能成功调用一个 LLM API
- 能换模型
- API Key 不出现在代码里
- 能解释“结构化输出不等于一定可靠”

### Day 3：Tool Schema 与 Function Calling

关联知识：[[Function Calling]]、[[Tool Schema]]、[[Pydantic 数据校验]]、[[工具参数校验]]

学习内容：

- tool/function schema
- 参数类型和必填字段
- Pydantic 校验
- 工具返回值结构

今天写什么：

1. 给 calculator 写 JSON schema
2. 用 Pydantic 定义工具参数
3. 写 `ToolResult` 数据结构
4. 模拟一次模型选择工具的 JSON
5. 校验参数并执行工具

验收标准：

- 能解释 schema 为什么重要
- 错误参数不会直接进入工具函数
- 工具结果能回填到 messages

### Day 4：单步 Agent Loop

关联知识：[[Agent Loop]]、[[工具结果回填]]、[[LLM messages 结构]]、[[Trace 日志]]

学习内容：

- observe / think / act / observe
- assistant tool call message
- tool result message
- 单步 loop 的退出条件

今天写什么：

1. 写 `AgentRunner`
2. 接收用户问题
3. 让模型决定是否调用工具
4. 执行 calculator
5. 把工具结果喂回模型
6. 输出最终答案

验收标准：

- 能完成一次“用户问题 -> 工具调用 -> 最终回答”
- 能打印每一步 trace
- 工具失败时不崩溃

### Day 5：最大步数、超时和错误处理

关联知识：[[Agent 停止条件]]、[[API 超时处理]]、[[异常处理]]、[[工具失败处理]]

学习内容：

- 最大步数
- 超时
- 工具失败反馈
- 循环和重复调用防护

今天写什么：

1. 给 `AgentRunner` 加 `max_steps`
2. 给 LLM 和工具执行加 timeout
3. 捕获工具异常并返回结构化错误
4. 检测重复工具调用
5. 写 3 个失败样例

验收标准：

- agent 不会无限循环
- 工具报错能进入 trace
- 最终输出能说明失败原因

### Day 6：Tool Registry、Trace 和 CLI

关联知识：[[Tool Registry]]、[[Trace 与回放]]、[[命令行交互]]、[[Rich 终端输出]]

学习内容：

- tool registry
- trace 结构
- CLI 入口
- README 初稿

今天写什么：

1. 把 calculator 注册到 `ToolRegistry`
2. 每一步写入 `data/traces/*.json`
3. `main.py` 支持交互式输入
4. 用 Rich 输出步骤
5. 写 README：运行方式、限制、失败样例

验收标准：

- 可以新增工具而不改 runner 主逻辑
- trace 可读
- 别人按 README 能跑

### Day 7：测试、复盘和边界表达

关联知识：[[pytest 基础]]、[[Agent Eval]]、[[Workflow 与 Agent 边界]]、[[AI Agent 面试题]]

学习内容：

- pytest 基础
- smoke test
- 简单 eval case
- agent/workflow 边界复盘
- 面试表达整理

今天写什么：

1. 给 calculator 写测试
2. 给 tool schema 校验写测试
3. 写 5 条 eval case
4. 写本周总结
5. 整理 10 个面试问答
6. 打 tag 或 final commit

验收标准：

- 至少 5 个测试用例
- 至少 5 条 eval case
- README 写清楚项目亮点和限制
- Git 提交历史干净

### 本周核心产出物

项目：`Calculator Agent`

推荐目录结构：

```text
week1_calculator_agent/
├── app/
│   ├── __init__.py
│   ├── agent.py
│   ├── config.py
│   ├── llm_client.py
│   ├── messages.py
│   ├── trace.py
│   ├── registry.py
│   └── tools/
│       ├── __init__.py
│       └── calculator.py
├── tests/
│   ├── test_calculator.py
│   ├── test_registry.py
│   └── test_agent_loop.py
├── data/
│   ├── traces/
│   └── .gitkeep
├── evals/
│   └── calculator_cases.jsonl
├── .env.example
├── .gitignore
├── README.md
├── requirements.txt
└── main.py
```

简历话术：

> 基于 Python 实现最小 Agent Loop，支持 OpenAI-compatible LLM 调用、结构化工具选择、calculator 工具执行、工具结果回填、最大步数限制、异常处理、trace 记录和基础 eval case，为后续 coding agent harness、RAG agent 和 skill packaging 打下工程基础。

推荐建立的 Obsidian 笔记：

- [[Calculator Agent 项目总览]]
- [[Agent Loop]]
- [[Tool Registry]]
- [[Function Calling]]
- [[Trace 与回放]]
- [[Agent Eval]]

## Week 2-8 项目导向规则

从 Week 2 开始，每周大纲必须围绕项目阶梯逐步展开。

生成 Week 2-8 大纲时必须遵守：

- 不生成孤立的“调 API Demo”作为本周核心产出物。
- 不生成孤立的“知识库问答系统”作为最终目标；RAG 必须包含 citation、失败处理和检索评估。
- 不生成孤立的“多工具 Agent Demo”作为最终目标；Agent 必须包含 tool schema、状态、停止条件、trace 和权限边界。
- `本周核心产出物` 必须写清楚它在项目阶梯中的位置。
- `面试仿真模拟` 必须加入至少 1 道“你这个项目为什么不是普通 Demo”的问题。
- `避坑指南` 必须提醒工程化要求：README、`.env.example`、测试、trace/eval、失败记录、权限边界、Docker 或部署说明。
- 必须按阶段加入稳定双链，例如 `[[Agent Loop]]`、`[[Tool Registry]]`、`[[Permission Gate]]`、`[[MCP 协议]]`、`[[Skills 能力打包]]`、`[[Browser Agent]]`、`[[Agent Eval]]`。
- 必须按 `source-link-policy.md` 给本周核心知识点加入少量 `可选来源` 链接；不要给每个 Day 重复堆同一批链接。
