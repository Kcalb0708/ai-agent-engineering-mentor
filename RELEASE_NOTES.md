# v1.1.0 - 双语 README 与多宿主安装支持

## 更新内容

- 重构 Obsidian 双链与知识点笔记维护规则，统一中文稳定命名。
- 扩展 Python、Agent Loop、Tool Schema、RAG、MCP、Eval 等核心概念体系。
- 新增 `skill-mode-patterns.md`，按 Pipeline / Generator / Reviewer / Inversion / Tool Wrapper 组织工作模式。
- 新增 `source-link-policy.md`，为关键知识点提供可选官方文档、规范、论文和项目来源链接。
- 优化 `weekly-outline-template.md`，强化每周产出物、项目阶梯、验收标准和工程化导向。
- 更新 README 为中英文双语开源文档，默认中文，可跳转英文。
- 补充 Codex、Claude Code、cc-switch、Hermes Agent 等多宿主安装方式。
- 在 README 中加入主仓库地址和 Releases 链接，方便用户获取最新版本。

## 兼容性

- 技能标识符保持为 `ai-agent-engineering-mentor`。
- 目录名仍建议使用 `ai-agent-engineering-mentor`。
- 支持标准 `SKILL.md` 目录结构的 Agent 工具。

## 校验

- `quick_validate.py` 通过。
- Markdown 代码围栏检查通过。
- `git diff --check` 无空白错误。