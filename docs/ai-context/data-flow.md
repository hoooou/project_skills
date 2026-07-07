# 数据流和工作流

## 适用范围

本项目没有运行时数据流。这里记录的是 skill 被 AI 工具使用时的知识流和维护工作流。

## 核心知识流

```text
项目文件 / 代码 / 文档
  -> project-init
  -> AGENTS.md + docs/ai-context/*
  -> project-sync
  -> 更新后的项目知识
  -> project-review
  -> 健康度报告 / 后续建议

灵感、长期想法、非紧急需求和高收益优化机会
  -> docs/ai-context/features.md
  -> project-review 检查是否仍有必要
```

## `project-init` 流程

输入：

- 当前项目目录。
- 项目文件、配置、源码、已有文档。
- 用户提供的顶层目标或约束，如果有。

处理：

- 先只读探索。
- 识别项目结构、技术栈、模块、数据流、数据库、API、决策和未知项。
- 创建或更新 AI 可读项目知识库。

输出：

- `AGENTS.md`
- `docs/ai-context/architecture.md`
- `docs/ai-context/modules.md`
- `docs/ai-context/data-flow.md`
- `docs/ai-context/database.md`
- `docs/ai-context/api.md`
- `docs/ai-context/features.md`
- `docs/ai-context/decisions/`
- 最终汇报：已创建/更新文件、重要事实、未知项、建议和下一步。

## `project-sync` 流程

输入：

- 当前项目文件。
- git diff 或可观察到的变更集；如果不是 git 仓库，则依赖文件事实和用户说明。
- 已有 AI-context 文档。

处理：

- 判断变更影响范围。
- 只更新受影响的项目知识。
- 必要时记录决策或开放问题。
- 如果出现尚未形成决策的需求、功能或优化点，记录或更新 `features.md`。
- 默认提醒低风险技术债。

输出：

- 更新后的 `AGENTS.md` 或 `docs/ai-context/*`。
- 变更影响分类和建议。

## `project-review` 流程

输入：

- 当前代码和文档。
- `AGENTS.md`、`docs/ai-context/`、README、决策记录，如果存在。

处理：

- 对比文档与项目现实。
- 检查 `features.md` 是否仍有必要，条目是否应保留、更新、归档、合并或移除。
- 发现缺失、过期、误导、漂移和技术债。
- 按 `AI-safe`、`Needs approval`、`Human decision` 分类建议。

输出：

- Project Knowledge Health Report。
- 后续同步、清理或需人决策的问题。

## 外部集成

Not found：当前未发现外部服务、API、数据库、CI、发布平台或自动化集成配置。

隐含外部上下文：

- 这些 skill 需要由支持 `SKILL.md` 的 AI 工具读取和执行。

## 未文档化流程

- Unknown：skill 如何安装到目标 AI 工具。
- Unknown：如何发布版本或同步到其他目录。
- Unknown：是否有人工审查流程。
- Unknown：中英文版本如何保持一致。
