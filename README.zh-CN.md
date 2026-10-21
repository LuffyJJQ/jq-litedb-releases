# jq-litedb (LiteSQL Workbench)

[English](README.md) | [简体中文](README.zh-CN.md)

**本地优先的轻量级桌面 SQL & Redis 数据库工作台**  
Local-First Lightweight Desktop SQL & Redis Workbench for Developers.

[![GitHub release (latest by date)](https://img.shields.io/github/v/release/LuffyJJQ/jq-litedb-releases?color=blue&label=Release)](https://github.com/LuffyJJQ/jq-litedb-releases/releases)
[![Platform](https://img.shields.io/badge/Platform-Windows%2011%20%2F%2010%20x64-informational)](https://github.com/LuffyJJQ/jq-litedb-releases/releases)
[![License](https://img.shields.io/badge/License-Freeware%20%2F%20Proprietary-lightgrey)](./LICENSE.txt)

---

## 📸 界面预览 (Screenshots)

### 暗色模式（默认）

![jq-litedb 暗色模式](docs/product-imgs/main-page-dark.png)

### 亮色模式

![jq-litedb 亮色模式](docs/product-imgs/main-page-light.png)

---

## ⚡ 核心亮点

- **多引擎支持**：内置 MySQL (8.0+)、PostgreSQL (14+) 关系型数据库与 Redis (6.0+) 键值缓存管理。
- **AST 只读安全防线**：使用 JSqlParser 对 SQL 进行 AST 抽象语法树强校验，严格只允许单条只读 `SELECT`，物理切断 DML（增删改）、DDL（改表删库）、`SELECT INTO` 以及 `FOR UPDATE` 锁定读取。
- **受限快速表预览**：默认 100 行受限预览，**绝不发起全表 `COUNT(*)` 慢查询**，避免大型线上表被统计拖垮。
- **非阻塞 Redis 键浏览器**：严禁阻塞单线程的 `KEYS *` 命令，底层统一封装流式游标 `SCAN` 检索，支持 String、Hash、List、Set、ZSet 深度结构解析与内置控制台。
- **BYOK AI SQL 辅助**：自带 API Key（Bring Your Own Key）接入任意兼容 OpenAI 接口的大模型服务（DeepSeek、OpenAI、通义千问等），受限提取 Schema（无行数据泄露），生成 SQL 后仅供人工审阅与“放入编辑器”，绝不自动执行。
- **优雅干净软件规范 (Clean Software)**：
  - **绝不在用户根目录随意散落文件**：所有配置与 SQLite 数据 100% 收敛至 Windows 标准的 `%APPDATA%\jq-litedb\`；
  - **零僵尸进程**：关闭桌面窗口立即级联终止后台子进程，内存与端口彻底释放；
  - **开箱即用**：自包含嵌入式运行环境，**用户机器无需提前安装 Java 运行时或任何开发工具**。

---

## 📥 立即下载 (Windows x64)

前往 [**GitHub Releases 最新发布页**](https://github.com/LuffyJJQ/jq-litedb-releases/releases/latest) 下载最新版本的安装程序：

- **安装包**：`jq-litedb-Setup-0.2.0.exe`（支持自定义安装路径与自动增量更新）

### 系统要求

- **操作系统**：Windows 11 / Windows 10 (64 位)
- **环境要求**：开箱即用，无需配置 Java、Node.js 或 Python 环境

---

## 🚀 核心功能快速览

### 1. 关系型数据库管理 (MySQL / PostgreSQL)
- **连接安全与免密秒连**：支持本地硬件密钥 AES-256 加密保存，未勾选时仅本次会话内存暂存，绝不明文落盘；支持整机实例多库浏览（库名选填）；
- **分层 Schema 树**：按需展开 Database / Schema，读取表、视图、字段主键、数据类型与字段注释；
- **CodeMirror 6 SQL 编辑器**：纯净无噪音控制台，支持语法高亮、暗亮主题自适应、`Ctrl+Enter` 运行选区或全量。

### 2. Redis 键值管理
- **分批游标检索**：非阻塞 `SCAN` 分批加载与 Pattern 模糊匹配；
- **数据结构可视化**：String 文本/JSON、Hash 键值表、List 索引序、Set 集合、ZSet 权重序；
- **安全控制台**：提供原生命令输入与响应输出，自动拦截高危危险命令。

### 3. 稳态交互与工作台降噪
- **Linear 零布局抖动规范**：异步反馈与连通性测试采用预留槽位与底栏物理锚定，彻底杜绝内容弹跳与按钮位移；
- **低噪音界面哲学**：去除多处快捷键重复提示与状态叫喊，打造专注、安静的专业开发者工作空间。

### 4. BYOK AI SQL 助手
- 打开右侧 AI 面板，配置您的 OpenAI 兼容端点（如 `https://api.deepseek.com/v1`）与 API Key；
- 配置采用临时文件 + 本地原子替换，仅保存在 `%APPDATA%\jq-litedb\ai-settings.json`；
- 输入自然语言需求，一键生成符合语法的标准只读 SQL 并填入编辑器。

---

## 📖 使用指南与文档

- [完整使用指南 (User Guide)](./docs/user-guide.md)
- [版本更新日志 (Changelog)](./CHANGELOG.md)

---

## 💬 反馈与问题报告

如果您在使用中发现问题或有优化建议，欢迎通过 [GitHub Issues](https://github.com/LuffyJJQ/jq-litedb-releases/issues) 提交反馈。
