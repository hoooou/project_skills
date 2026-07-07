# 模块说明

## 模块总览

| 模块 | 关键文件 | 主要职责 | 关系 |
| --- | --- | --- | --- |
| `project-init` | `project-init/SKILL.md` | 建立 AI 可读项目知识库基线。 | 工作流闭环的起点。 |
| `project-sync` | `project-sync/SKILL.md` | 在项目发生有意义变更后同步项目知识。 | 依赖 `project-init` 建立的知识结构。 |
| `project-review` | `project-review/SKILL.md` | 审查项目知识是否匹配当前项目现实。 | 可在多次同步后检查漂移。 |
| `project-init-en` | `project-init-en/SKILL.md` | `project-init` 的英文版本。 | 与中文版本语义对应。 |
| `project-sync-en` | `project-sync-en/SKILL.md` | `project-sync` 的英文版本。 | 与中文版本语义对应。 |
| `project-review-en` | `project-review-en/SKILL.md` | `project-review` 的英文版本。 | 与中文版本语义对应。 |
| `docs/ai-context` | 本目录下 Markdown 文件 | 为未来 AI 和人类维护者记录当前项目事实。 | 补充而不替代各 skill 入口文档。 |
| `docs/ai-context/features.md` | `docs/ai-context/features.md` | 记录灵光一现、不重要不紧急、长期目标、不影响短期目标、顿悟、性能收益巨大或人性化设计收益巨大的候选需求、功能和优化点。 | 属于 AI-context；不是路线图或决策记录。 |

## `project-init`

- 用途：首次接手新项目或缺少 AI-context 时，创建 `AGENTS.md` 和 `docs/ai-context/`。
- 关键职责：只读探索、识别技术栈、总结模块、创建知识库、记录未知项、提出建议。
- 重要边界：不改变产品方向，不替人做重大架构决策，不在初始化阶段大规模改代码。
- 稳定性：当前文档结构完整，职责清晰。

## `project-sync`

- 用途：在功能、修复、重构、API/数据库/集成变更后，同步项目知识。
- 关键职责：分析当前变更集、判断影响范围、更新受影响文档、维护决策记录、提醒低风险技术债。
- 重要边界：默认不修改代码；高风险重构、API 重设、产品行为变化需要人批准。
- 稳定性：当前文档结构完整，职责清晰。

## `project-review`

- 用途：审查 AI 可读项目知识健康度，发现缺失、过期、误导或漂移。
- 关键职责：盘点项目知识、对比文档和代码、找出知识缺口、发现技术债、评估决策卫生度。
- 重要边界：审查阶段不自动大规模修改文档或代码，不替人制定战略。
- 稳定性：当前文档结构完整，职责清晰。

## 英文模块

英文模块提供对应工作流的英文版本。当前可观察到三组英文目录：

- `project-init-en`
- `project-sync-en`
- `project-review-en`

Unknown：项目未记录双语版本同步原则。建议未来明确：

- 是否要求中文和英文完全等价。
- 是否允许英文版本省略或调整某些中文表达。
- 修改任一语言版本后是否必须同步另一版本。

## 模块依赖关系

```text
project-init
  -> creates baseline knowledge
project-sync
  -> updates baseline after meaningful changes
project-review
  -> audits baseline and project reality
```

`docs/ai-context` 记录这些关系，帮助未来 AI 更快理解项目，但每个 `SKILL.md` 仍应保持独立可执行。

`features.md` 记录候选想法和优化机会，供 `project-sync` 后续同步、供 `project-review` 周期性判断是否仍有必要保留。

## 所有权和不确定性

- Owner：Unknown，项目文件未记录维护者。
- 发布所有权：Unknown。
- 版本策略：Unknown。
- 自动验证：Not found。
