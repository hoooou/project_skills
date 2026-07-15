# Skills 项目工作协议

> 本文件同时支持多种 AI 工具:
> - 对 Claude Code: 通过 `CLAUDE.md` 符号链接访问
> - 对其他 AI 工具: 直接访问 `AGENTS.md`

## 项目概览

这是一套为 Claude Code 设计的项目知识管理 Skills 库,包含三个核心技能:

- **project-init**: 初始化 AI 可读的项目知识库
- **project-review**: 审查 AI 可读项目知识健康度
- **project-sync**: 同步项目现实和 AI 可读项目知识

每个技能都提供中英文版本:
- `project-init/` 和 `project-init-en/`
- `project-review/` 和 `project-review-en/`
- `project-sync/` 和 `project-sync-en/`

这些技能形成一个闭环工作流:初始化 → 增量同步 → 周期审查。

## 如何浏览代码库

```text
skills/
├── project-init/         # 中文版:初始化技能
│   └── SKILL.md         # 技能定义文件
├── project-init-en/      # 英文版:初始化技能
│   └── SKILL.md
├── project-review/       # 中文版:审查技能
│   └── SKILL.md
├── project-review-en/    # 英文版:审查技能
│   └── SKILL.md
├── project-sync/         # 中文版:同步技能
│   └── SKILL.md
└── project-sync-en/      # 英文版:同步技能
    └── SKILL.md
```

**核心入口点**: 每个子目录下的 `SKILL.md` 是技能定义文件,包含:
- 技能元数据 (name, version, description) in YAML frontmatter
- 完整的技能指令文档

**命名约定**:
- 中文版使用裸技能名 (如 `project-init`)
- 英文版添加 `-en` 后缀 (如 `project-init-en`)

## 常用命令

该项目是纯文档型项目,无需构建或运行命令。

**查看技能列表**:
```bash
ls -d project-*/ | sed 's|/||'
```

**搜索特定概念**:
```bash
grep -r "Operating model" --include="SKILL.md"
```

## 测试和验证方式

该项目的验证方式为:
1. **结构完整性验证**: 确认每个技能目录包含 `SKILL.md`
2. **元数据验证**: 确认 YAML frontmatter 包含必需字段
3. **内容一致性验证**: 中英文版应表达相同语义
4. **实际使用验证**: 在真实项目中测试技能是否按预期工作

目前无自动化测试框架。验证方式依赖人工审查和实际使用反馈。

## 本项目中的 AI 工作规则

### 指令优先级

1. 用户当前消息中的明确指令
2. 本 `AGENTS.md` 中的项目规则
3. 每个技能 `SKILL.md` 中的指令
4. Claude Code 的通用工作原则

### 项目级工作原则

**文档编辑原则**:
- 保持 YAML frontmatter 格式严格正确
- `name` 字段必须匹配目录名
- `version` 遵循语义化版本规范
- `description` 应在 500 字符内概括技能用途和触发时机
- 中英文版本应保持语义对等,但不必逐字翻译
- 使用简洁、结构化的 Markdown
- 优先使用列表、表格、代码块,避免大段连续文本

**版本管理原则**:
- 修改技能逻辑时,更新 `version` 字段
- 仅修改措辞、格式时,不需要更新版本号
- 中英文版本号应同步更新

**内容一致性原则**:
- 修改某个技能的中文版时,应同步评估英文版是否需要对应调整
- 三个技能应保持一致的术语和工作流描述
- `Operating model` 部分应在所有技能中保持一致
- 「静默兜底掩盖 bug」的核心认知在所有 skill 中共用同一段表述和术语(fail fast, fail loud),只有「本 skill 动作」一句按角色不同

**编码纪律原则(fail fast, fail loud)**:
- 未经要求不添加错误处理和默认值;内部逻辑默认不兜底
- 静默兜底(默认值、空对象、裸 catch、静默重试)会把「预期内变化」和「内部不变量被破坏(bug)」抹平,让 bug 变成合理默认值被埋掉
- 兜底只允许存在于系统边界,且必须显式、有日志、有注释说明它兜的是哪种预期内情况
- 对内部不变量用断言暴露,而不是用默认值掩盖
- 验证不能只看「没报错」,要断言真实值——「不崩」不等于「正确」

### 项目特有注意事项

**易误判事实**:
- 该项目没有运行时组件,纯文档项目
- 该项目没有外部依赖或包管理器
- `SKILL.md` 文件不是 Markdown 文档,而是带 YAML frontmatter 的技能定义文件
- 该项目不需要构建、编译或打包流程

**反复提醒沉淀规则**:
- 如发现用户反复提醒某规则,在本节记录

## 相关资源

- AI 上下文文档: [docs/ai-context/](./docs/ai-context/)
- 架构说明: [docs/ai-context/architecture.md](./docs/ai-context/architecture.md)
- 模块说明: [docs/ai-context/modules.md](./docs/ai-context/modules.md)

---

**注**: 本项目同时提供 `AGENTS.md` 和 `CLAUDE.md` 两个文件名:
- `AGENTS.md` 是主文件,供通用 AI 工具识别
- `CLAUDE.md` 是符号链接,供 Claude Code 识别

## 已知未知项

- [ ] 这些技能是否已在其他项目中实际验证过?
- [ ] 是否有计划添加更多技能?
- [ ] 是否需要提供安装或使用文档?
- [ ] 中英文版本的维护策略是什么?(手动同步 vs 自动化)
- [ ] 版本号的更新策略是否需要更明确的规范?
