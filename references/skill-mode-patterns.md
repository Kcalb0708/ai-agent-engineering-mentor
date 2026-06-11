# Skill 模式路由与门控规则

本文件把 5 种 Agent Skill 设计模式落到 `AI Agent 工程化每日导师`（技能标识符：`ai-agent-engineering-mentor`）的实际工作流中。它用于控制 skill 的内部组织方式，不直接作为每日学习内容输出。

## 模式组合

本 skill 是组合型 skill，不属于单一模式：

| 工作模式 | 主要设计模式 | 辅助设计模式 | 核心目的 |
| --- | --- | --- | --- |
| 每周大纲模式 | Generator | Inversion | 生成结构稳定的 Week 大纲，必要时先补问目标和基础 |
| 每日教学模式 | Pipeline | Generator | 按固定步骤生成每日 5 模块，禁止跳步 |
| 周计划调整模式 | Reviewer | Pipeline | 审查学习反馈和项目完整度，再决定推进或重排 |
| Obsidian 知识维护模式 | Reviewer | Generator | 评分双链重要性，再生成少量稳定知识卡 |
| 路线资料消化模式 | Tool Wrapper | Pipeline + Reviewer | 按需加载路线资料，把外部资料转成可执行规则 |

## 全局门控

- 必须先判断工作模式，再加载对应 reference；不要一次性加载全部资料。
- 对复杂任务先做内部阶段划分；如果缺失信息会改变长期路线或项目选择，先问一个最关键问题。
- 如果当前步骤失败，不继续执行后续步骤；先报告阻塞点或降级到更小任务。
- 不得把 reference 内容原样堆进输出；只提取和当前任务有关的规则。
- 遇到 `source-link-policy.md` 覆盖的知识点时，要在对应知识点附近提供少量 `可选来源` 链接，供用户自行决定是否打开。
- 链接服务于理解，不服务于堆资料；每日内容总链接数建议不超过 5 个。
- 不得为了“全面”扩大用户需求；路线优化必须服务于用户指定的学习目标。

## 每周大纲模式：Generator + Inversion

执行步骤：

1. 加载 `8-week-spine.md` 判断当前周所在阶段。
2. 加载 `weekly-outline-template.md` 获取固定输出结构。
3. 加载 `final-project-blueprint.md` 选择本周项目阶梯位置。
4. 加载 `obsidian-linking-policy.md` 统一双链命名。
5. 加载 `source-link-policy.md`，为本周核心技术点选择少量可选来源链接。
6. 如果用户没有说明基础、目标或当前 Week，按上下文合理推断；推断会影响长期路线时，只问一个关键问题。
7. 输出完整 Week 大纲，必须包含 Day 1-Day 7、核心产出物、面试仿真和避坑指南。

硬性要求：

- 每天必须有可运行或可临摹的代码任务。
- 本周必须有一个可运行产出物。
- 不允许把周计划写成资料清单。

## 每日教学模式：Pipeline + Generator

执行步骤：

1. 确认当前 Week 大纲；没有则先根据 `8-week-spine.md` 和 `weekly-outline-template.md` 重建。
2. 如果是 Day 1，加载 `day1-seed.md` 校准粒度。
3. 如果有学习反馈，加载 `adaptation-policy.md` 判断是否调整。
4. 加载 `obsidian-linking-policy.md` 统一双链。
5. 加载 `source-link-policy.md`，在核心知识点附近补充可选来源链接。
6. 生成且仅生成 5 个顶层模块。

硬性要求：

- 不得增加第 6 个顶层模块。
- 代码块前必须有 `关联知识：`。
- 代码必须可临摹、可运行、有 Type Hints、有中文注释、有异常处理。
- 可选来源链接必须嵌入现有模块，不得新增顶层模块。
- `📥 明日同步接口` 模板后不得再写任何内容。

## 周计划调整模式：Reviewer + Pipeline

执行步骤：

1. 加载 `adaptation-policy.md`。
2. 审查用户反馈属于哪类：正常推进、放慢复习、加难扩展、重排本周、Agent 项目完整度不足、求职包装不足。
3. 审查当前项目是否缺少 tool schema、permission、trace、eval、README、测试、失败记录。
4. 决定下一天任务，不单独输出完整新周大纲，除非用户明确要求。

硬性要求：

- 不机械推进周计划。
- 不因为用户提前完成就跳过主线；只增加工程化扩展。
- 连续卡住时必须降级和重排，不继续堆新框架。

## Obsidian 知识维护模式：Reviewer + Generator

执行步骤：

1. 加载 `obsidian-linking-policy.md`、`obsidian-note-maintenance-policy.md` 和 `source-link-policy.md`。
2. 提取所有 `[[...]]` 双链。
3. 按出现次数、出现位置、求职重要性评分。
4. 只选择 3-5 个最重要知识点。
5. 对命中关键来源的知识点补充 1-3 个延伸阅读链接。
6. 已存在同名笔记时只做增量补充，不整篇重写。

硬性要求：

- 不为低频概念制造空笔记。
- 不创建同义词重复笔记。
- 不为每个知识点机械添加外链，只给 P0/P1 概念补来源。
- 不修改每日主笔记结构，除非用户明确要求。

## 路线资料消化模式：Tool Wrapper + Pipeline + Reviewer

执行步骤：

1. 优先读取用户指定的本地 README 或资料文件。
2. 抽取链接和资料类别。
3. 按优先级阅读：官方文档和标准规范 > 现代 agent harness 项目 > 评测安全资料 > 论文摘要和开源项目 README > 可选博客。
4. 对资料做 Reviewer 式筛选：哪些会改变阶段目标、项目产出、验收标准、避坑指南。
5. 把关键来源写入或更新 `source-link-policy.md`，确保后续遇到对应知识点能给用户链接入口。
6. 再更新 `SKILL.md` 或 references。

硬性要求：

- 不声称逐字精读所有源码、论文全文或大型仓库。
- 如果只是 README 级别理解，必须明确。
- 外部资料必须转化成可执行学习规则，不能只堆链接。

## 模式设计约束

- `SKILL.md` 只保留触发、路由、门控和资源导航。
- 详细路线、模板、评分、项目蓝图全部放到 `references/`。
- 新增复杂模板时优先放到 `assets/`，不要塞进 `SKILL.md`。
- 新增确定性、重复性强的操作时优先放到 `scripts/`。
- reference 文件不做深层嵌套，必须能从 `SKILL.md` 直接发现。
