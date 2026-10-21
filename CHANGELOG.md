# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

> Chinese version available: [CHANGELOG.zh-CN.md](./CHANGELOG.zh-CN.md)

---

## [v0.2.0] - 2026-10-21

### Added
- **Constrained Workspace Layout Engine**:
  - Independent resizable and collapsible left database tree (`180–320px`) and right AI assistant panel (`300–480px`).
  - Vertical split pane supporting drag resize and one-click collapse of the query results panel into a compact `32px` tab strip.
  - Central canvas viewport guard ensuring a minimum width of `480px`.
  - Atomic layout state persistence powered by Zustand and stored safely in `localStorage`.
- **Zero Layout Thrashing 60fps Resizing**:
  - Eliminated synchronous DOM reflows by caching bounding client rects on mousedown.
  - Batched geometric style application using `requestAnimationFrame`.
  - Global user-select and cursor lifecycle locks during drag interactions.
- **Documentation & Internationalization**:
  - Dual-language documentation support with default English `README.md` and Chinese `README.zh-CN.md`.
  - High-resolution dark and light theme screenshots.

---

## [v0.1.0-beta.1] - 2026-10-21

First public beta release of `jq-litedb` (LiteSQL Workbench) for Windows 11 / 10 x64.

### Added
- **Desktop Runtime & Security Boundary**:
  - Electron sandbox architecture without node integration for renderer processes.
  - Embedded Spring Boot local service bound strictly to `127.0.0.1` loopback address.
  - High-entropy random API token generated on every launch with strict Host and Origin validation.
  - Clean Software Principles: 100% of data and configuration stored in `%APPDATA%\jq-litedb\`.
  - Clean cascading termination of backend processes upon application exit.
- **Multi-Engine Relational & Cache Management**:
  - Support for MySQL (8.0+), PostgreSQL (14+), and Redis (6.0+).
  - SQLite + Flyway local metadata storage.
  - AES-256 hardware-bound password encryption with optional in-memory-only retention.
  - Optional database name field for instance-level exploration.
  - Built-in 5-second connection timeout guard.
- **Stable UX & Noise-Free Workspace**:
  - Linear anti-jitter guidelines with anchored notification slots.
  - Low-noise visual design without duplicate keyboard shortcut banners.
- **Schema Exploration & Fast Preview**:
  - Hierarchical tree for schemas, tables, views, primary keys, data types, and comments.
  - Safe 100-row preview without slow full-table `COUNT(*)` queries.
- **SQL Editor & Read-Only AST Guard**:
  - CodeMirror 6 editor with syntax highlighting and automatic theme adaptation.
  - JSqlParser AST validation strictly permitting single read-only `SELECT` queries.
  - Global query concurrency limit (max 4), 15s timeout, and 2MB payload circuit breaker.
- **Redis Browser & Console**:
  - Non-blocking cursor-based `SCAN` streaming retrieval.
  - Deep inspection for String, Hash, List, Set, and ZSet structures.
  - Integrated interactive console with automatic blocking of destructive management commands.
- **BYOK AI SQL Assistant**:
  - Bring-Your-Own-Key integration with OpenAI-compatible endpoints (DeepSeek, OpenAI, Qwen, etc.).
  - Schema-only context extraction with zero table row data leakage.
