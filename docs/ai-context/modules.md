# 模块

## 主要模块概览

该项目包含 6 个技能模块目录,每个技能有中英文两个版本:

| 技能名称 | 中文版目录 | 英文版目录 | 版本 |
|---------|----------|----------|-----|
| 项目初始化 | `project-init/` | `project-init-en/` | 1.0.1 |
| 项目审查 | `project-review/` | `project-review-en/` | 1.0.1 |
| 项目同步 | `project-sync/` | `project-sync-en/` | 1.0.1 |

## project-init (项目初始化)

**目录**: `project-init/` (中文), `project-init-en/` (英文)

**职责**:
- 为新项目或已有项目建立 AI 可读的知识库
- 创建标准化的项目文档结构 (AGENTS.md, docs/ai-context/)
- 分析项目结构、技术栈、模块关系
- 记录数据库、API、数据流等关键信息
- 收集需求、功能想法和优化机会到 features.md

**关键文件**:
- `SKILL.md`: 435 行完整技能定义

**触发时机**:
- 项目缺少 AI 可读上下文文档
- 首次在已有项目中使用 Claude Code
- 现有文档零散或过期
- 准备重大功能开发或重构前

**与其他模块的关系**:
- **被 project-sync 依赖**: 同步技能需要初始化建立的文档结构
- **被 project-review 依赖**: 审查技能需要初始化建立的基线
- **独立性**: 可单独使用,不依赖其他技能

## project-review (项目审查)

**目录**: `project-review/` (中文), `project-review-en/` (英文)

**职责**:
- 审查项目知识健康度
- 检查文档与代码的一致性
- 发现缺失、过期或误导性信息
- 评估 features.md 中条目的有效性
- 识别技术债和架构问题
- 提供分类建议 (AI-safe / 需批准 / 需人决策)

**关键文件**:
- `SKILL.md`: 约 400+ 行技能定义 (需确认实际行数)

**触发时机**:
- 项目持续变化一段时间后
- 计划重大功能或架构调整前
- 新成员或 AI Agent 加入前
- 作为周期性维护
- 多次 project-sync 后检查知识漂移

**与其他模块的关系**:
- **依赖 project-init**: 需要已初始化的知识库结构
- **为 project-sync 提供输入**: 审查发现的问题可指导后续同步工作
- **与 project-sync 形成闭环**: 审查 → 发现问题 → 同步修复 → 再审查

## project-sync (项目同步)

**目录**: `project-sync/` (中文), `project-sync-en/` (英文)

**职责**:
- 在代码变更后同步项目知识
- 基于 git diff 判断影响范围
- 更新受影响的文档 (architecture, modules, data-flow, database, api, features)
- 同步 AGENTS.md 中的工作规则
- 更新决策记录
- 识别并提醒低风险技术债

**关键文件**:
- `SKILL.md`: 约 400+ 行技能定义 (需确认实际行数)

**触发时机**:
- 功能完成后
- Bug fix 改变重要行为后
- 重构改变模块边界后
- 数据库/API/集成变化后
- commit 或 PR 前

**与其他模块的关系**:
- **依赖 project-init**: 需要已初始化的知识库结构
- **被 project-review 评估**: 审查技能会检查同步的有效性
- **高频使用**: 是三个技能中使用频率最高的

## 通用文档模块 (docs/ai-context/)

**目录**: `docs/ai-context/`

**职责**:
- 本项目自身的 AI 可读文档
- 为 AI Agent 提供项目上下文
- 记录架构、模块、数据流等信息

**关键文件**:
- `architecture.md`: 架构说明
- `modules.md`: 本文件,模块说明
- `data-flow.md`: 数据流说明 (待创建)
- `database.md`: 数据库说明 (不适用于本项目)
- `api.md`: API 说明 (不适用于本项目)
- `features.md`: 功能想法和优化点
- `decisions/`: 决策记录目录

**稳定性**: 该模块应随项目演进持续更新

## 模块依赖关系

```text
依赖关系 (从被依赖到依赖):

project-init
    ↑
    ├─── project-sync (依赖初始化的结构)
    └─── project-review (依赖初始化的基线)
         ↑
         └─── project-sync (参考审查结果优化同步)

循环反馈:
init → sync → review → sync → ...
```

## 所有权和稳定性

| 模块 | 所有权 | 稳定性 | 说明 |
|-----|-------|-------|-----|
| project-init | 核心 | 稳定 | 基础技能,变更应谨慎 |
| project-review | 核心 | 稳定 | 审查逻辑相对固定 |
| project-sync | 核心 | 演进中 | 可能随用户反馈调整 |
| docs/ai-context | 元数据 | 演进中 | 应持续反映项目现状 |

**不确定性说明**:
- 技能的版本号管理策略尚未明确
- 中英文版本的同步更新机制待确定
- 未来是否会新增更多技能尚不明确