# jq-litedb-releases 仓库规范

## 基本约定

- 本仓库是 `jq-litedb` 的公开发布与用户文档仓库（`LuffyJJQ/jq-litedb-releases`），仅存放版本发布产物说明、对外自述文档、使用指南、安装说明及更新日志。
- **英文首选语言规则（严格遵循）**：
  - 面向用户的默认主入口（根目录 `README.md`、`CHANGELOG.md`、`docs/user-guide.md`、`.github/ISSUE_TEMPLATE/` 以及 GitHub Releases 发布说明）**统一默认且首选英文版本**，严禁使用中文为主或中英混排；
  - 仓库内配套提供中文对照留存版（`README.zh-CN.md`、`CHANGELOG.zh-CN.md`、`docs/user-guide.zh-CN.md`），并在文档顶部保持清晰的双向语言导航（如 `[English](...) | [简体中文](...)`）。
- **版本号真实性**：所有文档中提及的版本号与安装包名必须严格对应实际发布的 GitHub Release 版本（如 `v0.2.0`、`jq-litedb-Setup-0.2.0.exe`），严禁臆造虚构版本。
- **最小有效变更**：修改文档时只改动必要内容，保持格式与命名体系一致。
