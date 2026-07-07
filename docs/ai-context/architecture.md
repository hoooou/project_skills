# 架构概览

## 高层架构

本项目当前是文档型 skill 集合，而不是运行时应用。项目的“架构”主要由一组独立目录和其中的 `SKILL.md` 指令文档组成。

```text
skills/
  project-init/
    SKILL.md
  project-init-en/
    SKILL.md
  project-sync/
    SKILL.md
  project-sync-en/
    SKILL.md
  project-review/
    SKILL.md
  project-review-en/
    SKILL.md
  docs/
    ai-context/
```

## 主要层级和组件

| 层级/组件 | 证据 | 职责 |
| --- | --- | --- |
| Skill 目录 | `project-init/` 等顶层目录 | 按工作流拆分独立 skill。 |
| Skill 入口 | 各目录 `SKILL.md` | 定义 name、description、角色、目标、触发条件、职责、边界和输出要求。 |
| 语言镜像 | `*-en/` 目录 | 提供对应英文版本，便于英文工作流使用。 |
| AI-context | `docs/ai-context/` | 记录项目结构、模块、数据流、非适用领域、需求/功能/优化点和开放问题。 |

## 前端、后端、数据层、接口层

Not applicable：当前未发现前端、后端、数据库、接口服务、运行时入口或应用代码。项目的主要产物是 Markdown skill 文档。

## 依赖方向和边界

当前可确认的依赖关系是概念性的：

- `project-init` 建立项目知识基线。
- `project-sync` 依赖已有项目知识和当前变更，用于保持同步。
- `project-review` 依赖项目知识和当前项目现实，用于审查健康度。
- `features.md` 记录候选需求、功能和优化点，不等同于路线图或已确认决策。

边界：

- 每个 skill 应保持独立可读，不能依赖未来 AI 已经读过其他 skill。
- 中文和英文 skill 应保持核心工作流一致，但是否要求完全逐段同步需要人确认。
- AI-context 文档记录项目事实，不替代 `SKILL.md` 作为 skill 执行入口。

## 重要依赖

Not found：未发现代码依赖、包管理器、运行时依赖或外部服务配置。

隐含依赖：

- 支持 skills 的 AI 工具需要能读取 `SKILL.md`。
- `SKILL.md` 使用 Markdown 和 YAML frontmatter。

## 运行时或部署形态

Unknown：项目文件未记录安装、发布、同步到 Codex skills 目录或其他 AI 工具目录的流程。

当前只能确认这些文件可作为本地 skill 文档被读取。

## 架构约束

- 项目应保持文档优先、低工具链负担。
- Skill 文档需要明确区分事实、建议、开放问题和人类决策。
- `features.md` 中的条目需要明确区分想法、建议、已确认事项和需人确认事项。
- 初始化、同步、审查三类工作流形成闭环，修改一个 skill 时通常需要检查另外两个是否受影响。
- 中英文版本存在并行维护成本。

## 开放架构问题

- 是否需要根目录 README 作为人类入口？
- 是否需要自动校验 frontmatter、必备章节和中英文覆盖关系？
- 是否需要记录发布或安装流程？
- 是否需要正式定义中文/英文版本的同步策略？

## 可落地改进建议

### 最小可行方案

新增根目录 README，说明项目用途、目录结构、安装方式和维护规则。

- 收益：降低新会话和人类维护者的入口成本。
- 成本：低。
- 风险：低。

### 推荐方案

在 README 基础上增加轻量校验脚本或清单，检查每个 skill 是否包含 frontmatter、Role/Goal/Responsibilities/Boundaries/Output 等关键部分。

- 收益：减少 skill 文档漂移，提升人和 AI 的可维护性。
- 成本：中低。
- 风险：需要人确认是否接受引入脚本或工具链。

### 扩展方案

建立中英文同步维护策略，例如维护一个对照清单或差异审查流程。

- 收益：降低双语版本长期偏移风险。
- 成本：中。
- 风险：如果要求过度严格，可能增加维护摩擦。
