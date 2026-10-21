# jq-litedb User Guide

[English](user-guide.md) | [简体中文](user-guide.zh-CN.md)

Welcome to **jq-litedb (LiteSQL Workbench)**. This guide walks you through installation, configuration, and everyday workflows.

---

## 1. Installation & Startup

1. Go to the [GitHub Releases](https://github.com/LuffyJJQ/jq-litedb-releases/releases/latest) page and download `jq-litedb-Setup-0.2.0.exe`.
2. Double-click the installer. You can customize the target installation directory (defaults to `%LOCALAPPDATA%\Programs\jq-litedb`, requiring no administrator privileges).
3. Once installed, launch the application. The system will silently bootstrap the local embedded service and open the main workbench within seconds.

---

## 2. Clean Software Principles (Local Storage)

jq-litedb strictly follows clean software architecture and **never pollutes your user home directory (`C:\Users\<username>`)**:

- **Unified Data & Config Directory**:
  ```text
  %APPDATA%\jq-litedb\
  ├── jqlitedb.sqlite         # Stores your connection metadata (AES-256 encrypted passwords)
  ├── ai-settings.json        # Your BYOK AI endpoint and API key settings
  ├── settings.json           # Application preferences (theme, layout dimensions)
  └── logs/                   # Application runtime logs
  ```
- **Encrypted Password Storage**: Passwords can be saved using hardware-bound AES-256 encryption. If unchecked, credentials are held only in memory for the active session and wiped upon exit.
- **Zero Zombie Processes**: When closing the desktop window, all child backend processes are immediately terminated, releasing ports and memory cleanly.

---

## 3. Database Connection Management

### 3.1 Creating a Connection
- Click the **`+` (New Connection)** button in the left sidebar header;
- Select the database type: **MySQL**, **PostgreSQL**, or **Redis**;
- Enter the Host, Port, Database name (optional for instance exploration), Username, and Password;
- Check **Save Password** if you wish to persist it encrypted locally;
- Click **Test Connection** to verify network reachability;
- Click **Save** to persist the connection metadata.

### 3.2 Schema Browsing & Table Preview
- Expand any connection in the left sidebar tree;
- Expand databases / schemas to view tables and views;
- Click a table to display an instant, constrained **100-row table preview** in the bottom panel;
- Expand the table node to inspect columns, data types, primary key flags, and comments.

---

## 4. Querying with the SQL Editor

1. Enter your SQL query in the CodeMirror 6 editor located in the central pane;
2. **Read-Only Safety Guard**: jq-litedb is purpose-built for safe diagnostic exploration. It strictly permits single read-only `SELECT` statements (including CTE `WITH ... SELECT`). All mutating operations (`UPDATE`, `DELETE`, `DROP`, `ALTER`, `SELECT INTO`, locking reads) are physically rejected;
3. Execute queries using:
   - Click the **Run** button in the editor toolbar, or
   - Press **`Ctrl + Enter`** to execute the highlighted selection (or the entire script if nothing is selected);
4. Query results render in a virtualized data grid with row numbering. Double-click any cell to copy its content to the clipboard.

---

## 5. Non-Blocking Redis Browser

1. Connect to a Redis instance from the left sidebar;
2. Browse keys through streaming non-blocking `SCAN` iteration (never blocks the server with `KEYS *`);
3. Inspect key details and data structures: String (Text/JSON), Hash, List, Set, and ZSet;
4. Open the integrated Redis console for direct diagnostics with built-in safety filtering against destructive commands.

---

## 6. BYOK AI SQL Assistant

1. Click the **AI Assistant** button on the right to toggle the side drawer;
2. For initial setup, open the drawer settings:
   - **Base URL**: Any OpenAI-compatible endpoint (e.g., `https://api.deepseek.com/v1` or `https://dashscope.aliyuncs.com/compatible-mode/v1`);
   - **Model**: Model identifier (e.g., `deepseek-chat` or `qwen-plus`);
   - **API Key**: Enter your personal API key (saved atomically to `%APPDATA%\jq-litedb\ai-settings.json`);
3. Enter your natural language prompt (e.g., *"Find departments where the average salary exceeds 8000"*);
4. Click **Generate SQL**. The assistant retrieves table metadata (schemas only, zero row data transmission) and produces clean, read-only SQL;
5. Click **Insert into Editor** to review the SQL before executing it manually with `Ctrl + Enter`.
