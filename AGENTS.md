# 项目 AI 工作指南

## 项目概览

本项目是一个 Codex/AI 工具可用的项目知识维护 skill 集合。当前直接证据显示，项目包含 3 个中文 skill 和 3 个英文 skill：

- `project-init/`：初始化 AI 可读项目知识库。
- `project-sync/`：在项目发生有意义变更后同步 AI 可读项目知识。
- `project-review/`：审查 AI 可读项目知识健康度。
- `project-init-en/`、`project-sync-en/`、`project-review-en/`：对应英文版本。

项目当前不是应用、服务或库代码仓库；主要产物是 Markdown 格式的 `SKILL.md` 指令文档。

项目知识库包含 `docs/ai-context/features.md`，用于记录灵光一现、不重要不紧急、长期目标、不影响短期目标、顿悟、性能收益巨大或人性化设计收益巨大的需求、功能和优化点。

## 如何浏览代码库

- 每个顶层目录代表一个独立 skill。
- 每个 skill 的入口文件都是该目录下的 `SKILL.md`。
- 中文与英文版本按目录名成对维护：
  - `project-init/` 对应 `project-init-en/`
  - `project-sync/` 对应 `project-sync-en/`
  - `project-review/` 对应 `project-review-en/`
- 项目知识库位于 `docs/ai-context/`。

## 常用命令

当前未发现构建、测试、格式化或发布配置文件。

可用于人工检查的只读命令：

```bash
find . -maxdepth 3 -type f | sort
```

```bash
rg "project-init|project-sync|project-review" .
```

## 测试和验证方式

Not found：当前未发现自动化测试、lint、schema 校验或打包命令。

建议在修改 skill 文档后至少做人工验证：

- 检查每个 `SKILL.md` 是否保留有效 YAML frontmatter。
- 检查中英文版本的核心职责、边界和输出要求是否保持语义一致。
- 检查新增或修改内容是否仍然区分事实、建议、未知项和需人确认事项。

## 本项目中的 AI 工作规则

- 先读对应 skill 的完整 `SKILL.md`，再修改文档。
- 不要把推测写成事实；使用 `Unknown`、`Not found`、`Inferred from ...`、`Needs human confirmation` 标记不确定性。
- 不要替人决定 skill 的产品方向、适用范围或重大流程边界。
- 修改中文 skill 时，检查是否需要同步英文版本；修改英文 skill 时同理。
- 保持 skill 文档面向未来 AI Agent 可执行：职责、边界、输出、触发时机应明确。
- 避免为当前文档型项目引入应用式结构、运行时或复杂工具链，除非用户明确决定。

## AI-context 文档

- [architecture.md](docs/ai-context/architecture.md)
- [modules.md](docs/ai-context/modules.md)
- [data-flow.md](docs/ai-context/data-flow.md)
- [database.md](docs/ai-context/database.md)
- [api.md](docs/ai-context/api.md)
- [features.md](docs/ai-context/features.md)
- [decisions/](docs/ai-context/decisions/)

## 已知未知项和需人确认问题

- Unknown：这些 skill 的目标安装位置、发布流程和版本管理方式未在项目文件中记录。
- Unknown：中文与英文版本是否要求严格逐段等价，还是允许面向不同使用场景调整表达。
- Not found：未发现 README、贡献指南、测试命令、发布脚本或自动校验。
- Needs human confirmation：是否需要增加一个统一 README，说明 skill 集合的用途、安装方式和维护流程。
