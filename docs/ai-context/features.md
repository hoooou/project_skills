# 需求、功能和优化点

## 用途

本文件用于记录值得保留但不一定进入短期执行计划的候选需求、功能和优化点。

适合记录：

- 灵光一现的想法
- 不重要不紧急的需求、功能或优化点
- 面向长期目标的想法
- 不影响短期目标的想法
- 顿悟式的产品、工程或交互方向
- 性能收益可能巨大的优化
- 人性化设计收益可能巨大的优化

本文件不是路线图、排期或已确认决策。条目需要保留来源、状态和不确定性。

## 条目格式

建议格式：

```markdown
### 标题

- Category: 灵光一现 / 不重要不紧急 / 长期目标 / 不影响短期目标 / 顿悟 / 性能收益巨大 / 人性化设计收益巨大
- Source: 用户提出 / Inferred from ... / AI suggestion / Unknown
- Status: Idea / Needs human confirmation / Accepted / Deferred / Archived
- Expected benefit: ...
- Cost/Risk: ...
- Short-term impact: None / Low / Medium / High / Unknown
- Notes: ...
```

## 当前条目

### AI-context 增加 features.md

- Category: 长期目标 / 不影响短期目标
- Source: 用户明确提出
- Status: Accepted
- Expected benefit: 集中存放不适合立即执行、但未来可能产生较大价值的需求、功能和优化点，降低想法散落在对话中的损失。
- Cost/Risk: 需要在 `project-review` 中定期检查是否仍有必要，避免文件长期空转或重复其他文档。
- Short-term impact: Low
- Notes: 已同步到中文版和英文版 skill 的初始化、同步和审查流程。

## 维护规则

- `project-init` 创建本文件或保留 `Not applicable` 判断。
- `project-sync` 在用户提出新想法、代码变化暴露优化机会或某个候选项状态变化时更新本文件。
- `project-review` 必须检查本文件是否仍然有必要，并建议 `Keep`、`Update`、`Archive`、`Merge` 或 `Remove`。
- 删除本文件或移除大量条目前需要人确认。
