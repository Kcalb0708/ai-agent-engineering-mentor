# Day 1 标准：Python MUP 与最小 Agent 地基

用于校准 `Phase 1 / Week 1 / Day 1` 的颗粒度。Day 1 必须对齐 Week 1 大纲中的 `week1_calculator_agent` 项目，不要写成孤立的 Python 语法课。

## Day 1 核心定位

主题：Python 工程环境、messages 结构与最小工具函数。

目标：让用户搭好 `week1_calculator_agent` 项目地基，并完成 `.env` 配置读取、messages JSON 保存、calculator 工具函数和本地最小验证。

## 必须覆盖的核心点

### 1. 环境就是 Agent 工程能力的一部分

- Python 版本、虚拟环境、依赖隔离、`.env` 都不是形式主义。
- Agent 应用会调用付费 API、读写本地文件、执行工具，配置错了就无法运行或无法复现。
- 新手坑：全局乱装包、硬编码 API Key、把 `.env` 提交到 Git、没有 `.env.example`。

### 2. Python MUP 是表达 Agent 数据流

Agent 项目的基础数据流：

用户输入 -> 组织 messages -> 模型决定是否调用工具 -> 校验工具参数 -> 执行工具 -> 保存工具结果 -> 返回最终答案。

Day 1 只死磕：

- 函数。
- 类型注解。
- 异常处理。
- `pathlib`。
- JSON 读写。
- `.env` 配置读取。
- messages 数据结构。
- 一个安全的 calculator 工具函数。

### 3. Day 1 不要求真的接入 LLM

Day 1 可以只做本地模拟，不强迫用户当天就跑通模型 API。

必须完成：

- 读取配置。
- 保存 messages。
- 调用本地工具。
- 用一段模拟的 tool call JSON 验证工具参数。

不要求完成：

- 真正 function calling。
- 多步 agent loop。
- RAG。
- LangChain / LangGraph。
- FastAPI 服务。

## Day 1 代码要求

优先围绕以下文件展开：

- `app/config.py`：读取 `.env` 中的 `LLM_API_KEY`、`LLM_BASE_URL`、`LLM_MODEL`。
- `app/messages.py`：保存和读取 `data/messages.json`。
- `app/tools/calculator.py`：实现加、减、乘、除，包含参数校验和除零错误。
- `main.py`：做最小命令行验证。

代码必须：

- 有 Type Hints。
- 有中文注释。
- 有异常处理。
- 不使用 `pass`。
- 不只给简化片段，要能让用户临摹并运行。
- 代码块内部不要出现 Obsidian 双链。

## Day 1 推荐目录

```text
week1_calculator_agent/
├── app/
│   ├── __init__.py
│   ├── config.py
│   ├── messages.py
│   └── tools/
│       ├── __init__.py
│       └── calculator.py
├── data/
│   └── .gitkeep
├── .env.example
├── .gitignore
├── requirements.txt
└── main.py
```

## Day 1 代码实战必须包含的行为

`main.py` 运行后至少做到：

1. 读取 `.env` 或给出清晰错误。
2. 创建一条 user message。
3. 创建一条模拟 assistant tool call。
4. 调用 calculator。
5. 创建一条 tool result message。
6. 保存到 `data/messages.json`。
7. 在终端打印工具结果。

## Day 1 验收标准

用户完成后应该做到：

- 创建 `week1_calculator_agent` 项目目录。
- 创建并激活虚拟环境。
- 安装 `httpx python-dotenv rich pydantic`。
- 能读取 `.env`。
- 能把 messages 保存到 `data/messages.json`。
- 能运行 calculator 工具。
- 能解释 messages 为什么要保存。
- 能解释为什么工具参数要先校验。
- 能解释为什么 API Key 不能硬编码。
- 完成一次 Git commit。

## Day 1 默认优先补充的 Obsidian 笔记

- `[[Python 虚拟环境]]`：详细。
- `[[环境变量与 API Key]]`：详细。
- `[[LLM messages 结构]]`：标准。
- `[[Tool Schema]]`：标准。
- `[[异常处理]]`：标准。
