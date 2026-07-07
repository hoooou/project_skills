# API 和接口

## 当前状态

Not applicable：当前未发现 HTTP API、RPC、事件协议、CLI 接口、前后端接口或外部系统集成代码。

## Skill 接口形态

本项目可确认的“接口”是 `SKILL.md` 文档约定：

- YAML frontmatter：
  - `name`
  - `description`
- Markdown 主体：
  - Role / 角色
  - Goal / 目标
  - Operating model / 工作模型
  - Trigger / 触发时机
  - Responsibilities / 职责
  - Boundaries / 边界
  - Output / 输出

这些不是运行时 API，而是供支持 skills 的 AI 工具读取的文档接口。

## 认证和授权

Not applicable：未发现认证、授权或访问控制实现。

## 请求/响应模式

Not applicable：无运行时 request/response contract。

从工作流角度看，每个 skill 接收用户请求和项目文件作为上下文，输出文档、报告或建议。但这属于 AI 工具执行约定，不是项目内代码实现。

## 开放问题

- Unknown：目标 AI 工具对 `SKILL.md` frontmatter 是否有额外 schema 要求。
- Unknown：是否需要为 skill 元数据增加自动校验。
- Unknown：是否需要定义目录命名规范，例如 `*-en` 是否为唯一英文后缀规则。

## 建议

如果未来要增强可维护性，可添加轻量 schema 或检查清单，验证每个 `SKILL.md` 的 frontmatter 和关键章节完整性。
