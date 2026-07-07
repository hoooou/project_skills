# 数据库和持久化

## 当前状态

Not applicable：当前项目是 Markdown skill 文档集合，未发现数据库、持久化层、schema、migration、model 或数据访问代码。

## 证据

- 顶层目录只包含各 skill 目录和 `SKILL.md`。
- 未发现数据库配置、ORM 配置、migration 目录或应用代码。
- 未发现 package、runtime 或服务配置。

## 数据所有权边界

Not applicable：无运行时数据实体或持久化记录。

## 开放问题

- Unknown：是否需要为 skill 发布、版本或变更历史建立单独元数据文件。
- Unknown：是否未来会把 skill 注册信息放入某种 manifest 或索引。

## 建议

当前不建议引入数据库或持久化层。若需要追踪版本和发布，优先考虑轻量文档或 manifest，而不是数据库。
