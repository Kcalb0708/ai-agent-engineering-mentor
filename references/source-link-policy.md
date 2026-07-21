# 知识点来源链接输出规则

本文件用于控制“已消化过的 README 关键来源”如何在周大纲、每日内容和知识点笔记中按需露出链接。目标是给用户自主深入阅读的入口，而不是把学习内容变成链接列表。

## 输出原则

- 遇到对应知识点时，提供 1-2 个最相关来源链接，最多 3 个。
- 优先官方文档、标准规范和论文摘要；其次是高质量开源项目 README；最后才是博客或社区资料。
- 链接必须放在对应知识点附近，使用 `可选来源：` 或 `延伸阅读：`，不要集中堆在文末。
- 每日内容总链接数建议不超过 5 个；Week 大纲总链接数建议不超过 12 个。
- 不为链接新增顶层模块；链接必须嵌入当前“每日模块配置”中承担对应职责的模块内。
- 不强迫用户阅读链接；措辞使用“可选来源”而不是“必须阅读”。
- 如果链接只做过 README 级理解，不要声称已经精读源码或论文全文。
- 如果用户明确要求“不要外链”，只保留 Obsidian 双链，不输出外部链接。

## 输出位置

### 每周大纲

在 `核心技术拆解` 的每个技术点下增加：

```markdown
可选来源：[来源名](URL)、[来源名](URL)
```

只给本周最核心技术点加链接，不需要每个 Day 都重复。

### 每日内容

优先放在承担“核心知识”职责的模块中；默认 5 模块配置下是 `📌 今日核心死磕`：

```markdown
可选来源：[Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)
```

如果当天上午任务明确要求读文档，可以在承担“学习路径”职责的模块中加入 1 个链接；默认配置下是 `🎯 6小时精细化路线` 的上午段。

不要在次日反馈模板后添加任何链接；默认配置下该位置是 `📥 明日同步接口`。

### Obsidian 知识点笔记

如果生成独立知识点笔记，可以在 `相关链接` 或新增 `延伸阅读` 小节里放 1-3 个外部链接。不要为每个低频概念都补来源。

## 知识点到来源映射

### Agent 边界与基础循环

适用概念：

- `[[Workflow 与 Agent 边界]]`
- `[[Agent Loop]]`
- `[[Agent 停止条件]]`
- chatbot / workflow / agent / multi-agent 区分

优先来源：

- [Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)
- [OpenAI: A practical guide to building agents](https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/)
- [Lilian Weng: LLM Powered Autonomous Agents](https://lilianweng.github.io/posts/2023-06-23-agent/)

### Tool Calling 与结构化输出

适用概念：

- `[[Function Calling]]`
- `[[Tool Schema]]`
- `[[工具参数校验]]`
- `[[工具结果回填]]`
- `[[结构化输出]]`

优先来源：

- [OpenAI Function Calling](https://platform.openai.com/docs/guides/function-calling)
- [Claude Tool Use](https://docs.anthropic.com/en/docs/agents-and-tools/tool-use/overview)
- [Gemini Function Calling](https://ai.google.dev/gemini-api/docs/function-calling)

### RAG、Research Agent 与引用

适用概念：

- `[[RAG 检索增强生成]]`
- `[[Embedding 向量化]]`
- `[[Chunk 文档切分]]`
- `[[Citation 引用来源]]`
- `[[检索评估]]`
- `[[Web Research Agent]]`
- `[[Deep Research]]`

优先来源：

- [LlamaIndex Agents](https://docs.llamaindex.ai/en/stable/use_cases/agents/)
- [LangChain Docs](https://docs.langchain.com/)
- [GPT Researcher](https://github.com/assafelovic/gpt-researcher)
- [Open Deep Research](https://github.com/langchain-ai/open_deep_research)
- [RAGFlow](https://github.com/infiniflow/ragflow)

### Coding Agent 与 Agent Harness

适用概念：

- `[[Agent Harness]]`
- `[[Coding Agent]]`
- `[[Tool Registry]]`
- `[[Permission Gate]]`
- `[[Session Store]]`
- `[[Context Compaction]]`
- `[[Trace 与回放]]`
- `[[Nano Coding Agent]]`

优先来源：

- [Claude Code Overview](https://code.claude.com/docs/en/overview)
- [Claude Code Subagents](https://code.claude.com/docs/en/sub-agents)
- [Claude Code Hooks](https://code.claude.com/docs/en/hooks)
- [OpenAI Codex](https://github.com/openai/codex)
- [learn-claude-code](https://github.com/shareAI-lab/learn-claude-code)
- [claw0](https://github.com/shareAI-lab/claw0)
- [Dive into Claude Code](https://arxiv.org/abs/2604.14228)
- [AI Harness Engineering](https://arxiv.org/abs/2605.13357)

### Skills 与协议

适用概念：

- `[[Skills 能力打包]]`
- `[[Skill 与 Tool 区别]]`
- `[[Skill 与 Prompt 区别]]`
- `[[MCP 协议]]`
- `[[A2A 协议]]`
- `[[ACP 协议]]`
- `[[Skill Smoke Test]]`

优先来源：

- [Claude Code Skills](https://code.claude.com/docs/en/skills)
- [Claude Agent Skills](https://docs.claude.com/en/docs/agents-and-tools/agent-skills)
- [Claude Code Agent SDK Skills](https://code.claude.com/docs/en/agent-sdk/skills)
- [OpenClaw Skills](https://github.com/openclaw/openclaw/blob/main/docs/tools/skills.md)
- [Model Context Protocol](https://modelcontextprotocol.io/)
- [Agent2Agent Protocol](https://a2a-protocol.org/latest/specification/)
- [Agent Client Protocol](https://agentclientprotocol.com/)
- [SWE-Skills-Bench](https://arxiv.org/abs/2603.15401)

### Multi-Agent 与 Graph 编排

适用概念：

- `[[Multi-Agent 协调]]`
- `[[Planner Executor Reviewer]]`
- `[[Supervisor Agent]]`
- `[[LangGraph 状态图]]`
- `[[Agent 输入输出 Schema]]`
- `[[循环终止条件]]`

优先来源：

- [Claude Code Subagents](https://code.claude.com/docs/en/sub-agents)
- [Google Agent Development Kit](https://google.github.io/adk-docs/)
- [LangGraph](https://langchain-ai.github.io/langgraph/)
- [Agent2Agent Protocol](https://a2a-protocol.org/latest/specification/)

### Browser / Computer-use Agent

适用概念：

- `[[Browser Agent]]`
- `[[Computer-use Agent]]`
- `[[Playwright 自动化]]`
- `[[DOM Snapshot]]`
- `[[Action Log]]`
- `[[Screenshot Trace]]`
- `[[页面失败恢复]]`

优先来源：

- [Claude Computer Use](https://docs.anthropic.com/en/docs/agents-and-tools/tool-use/computer-use-tool)
- [browser-use](https://github.com/browser-use/browser-use)
- [WebArena](https://arxiv.org/abs/2307.13854)
- [VisualWebArena](https://arxiv.org/abs/2401.13649)

### Eval、Observability 与 Safety

适用概念：

- `[[Agent Eval]]`
- `[[Trace 与回放]]`
- `[[Human-in-the-loop]]`
- `[[Prompt Injection]]`
- `[[Data Exfiltration]]`
- `[[Tool Abuse]]`
- `[[Audit Log]]`

优先来源：

- [OpenAI Evals](https://platform.openai.com/docs/guides/evals)
- [OpenAI Agent platform](https://openai.com/agent-platform/)
- [LangSmith](https://docs.smith.langchain.com/)
- [AgentBench](https://arxiv.org/abs/2308.03688)
- [SWE-bench](https://arxiv.org/abs/2310.06770)
- [Your Agent, Their Asset](https://arxiv.org/abs/2604.04759)

## 链接选择规则

当同一知识点有多个来源：

1. 如果是概念边界，优先 Anthropic / OpenAI 官方指南。
2. 如果是 API 或协议，优先官方文档或规范。
3. 如果是项目实现，优先开源项目 README。
4. 如果是安全、评测或研究判断，优先论文摘要和 benchmark。
5. 如果当天任务是代码实战，最多给 1 个文档链接，避免打断编码。

## 示例

正确：

```markdown
### [[Agent Loop]]：为什么不是普通 workflow

今天你要理解 agent loop 的关键不是“让模型多想几步”，而是让模型在观察、选择工具、执行工具、读取结果之间形成可控闭环。

可选来源：[Anthropic: Building effective agents](https://www.anthropic.com/engineering/building-effective-agents)、[OpenAI: A practical guide to building agents](https://openai.com/business/guides-and-resources/a-practical-guide-to-building-ai-agents/)
```

错误：

```markdown
资料链接：
1. ...
2. ...
3. ...
10. ...
```

原因：链接和知识点脱节，会把学习任务变成资料收集。
