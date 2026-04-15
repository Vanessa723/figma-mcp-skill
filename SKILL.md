---
name: figma-mcp-skill
description: Generates and edits Figma UI using IDS (Infra Design System) tokens, components, and business configs via Figma MCP. Use when the user mentions IDS, Infra Design System, SHOPEE design org, component-index, Space/DataSuite/Ask/Smart products, or asks to create or update Figma files to team standards.
---

# IDS Figma（Cursor 技能入口）

## 何时使用

在通过 **Figma MCP** 生成或修改设计稿、且需符合 **IDS** 与业务配置时启用本技能。不适用：Figma 插件、Figma Make / Stitch 等内置 AI 设计工具。

---

## Quick Start Card | 快速启动

**Read this before loading any other file.**

### Core Rules (always apply)
1. **100% token coverage** — no bare hex values, raw font sizes, or unitless shadows anywhere
2. **Standard controls from IDS UI Kit** — never hand-draw Button / Input / Select / Table / Modal / Tag / Checkbox / Radio / Switch / Tabs / Pagination
3. **One screen per generation by default** — additional screens/states only when explicitly requested

### Most-Used Tokens
| Use | Token |
|-----|-------|
| Primary text | `Text/Primary` |
| Secondary text | `Text/Secondary` / `Character/Secondary .45` |
| Page bg | `Gray/gray-1` |
| Card / white | `Gray/White` |
| Brand blue | `Primary (Infra Blue)/6` |
| Error | `Dust Red/6` |
| Warning | `Sunset Orange/6` |
| Success | `Polar Green/2` |
| Disabled | `Neutral/5` |
| AI bg | `AI/5/BgPrimary` |
| Body text style | `Text Base/Normal` |
| Heading | `Heading/1` – `Heading/5` |
| Card shadow | `boxShadow` |

### Modes (always confirm before generating)
- **Guided Mode** — Product with a business config (Space / DataSuite / Ask / Smart). Apply its Design Language + use Biz Components where they naturally fit. Layout decisions are creative and open.
- **Open Mode** — No product config, or the user wants IDS foundation only. Full creative freedom; IDS tokens + base components as the floor.

**Always ask one question:** *"Guided Mode ([product]) or Open Mode?"* — Never auto-enter either mode.

### Forbidden Patterns | 绝对禁止

These are hard stops — violating any of these immediately invalidates the delivery:

- ❌ Bare hex values, raw font sizes, or unitless shadows — always use IDS tokens
- ❌ Hand-drawing Button / Input / Select / Table / Modal / Tag / Checkbox / Radio / Switch / Tabs / Pagination
- ❌ External icon libraries (Material, Heroicons, Feather, etc.) — IDS icons only, 12/16/20/24px
- ❌ Lorem ipsum or placeholder text — real product copy only
- ❌ Chinese characters in any UI element or layer name
- ❌ Detaching IDS components unless the user explicitly says "detach"
- ❌ Using underscore-prefixed components (`_ComponentName`) — internal base only
- ❌ Creating Figma files outside **SHOPEE SINGAPORE PRIVATE LIMITED** organization
- ❌ Writing into the IDS design system file (`zANozorPV3t5sueU20e0Nx`) — read-only library
- ❌ Generating more than one screen without explicit user confirmation
- ❌ Skipping Phase 1 structure preview (except for small targeted edits the user specifies)

---

## 第一步：读完整规范

**必须先阅读**同目录下的 [figma-ids-design.md](figma-ids-design.md)（完整工作流程：Pre-flight、模式确认、生成步骤、编辑流程、交付）。

## 输入类型处理 | Input Detection

自动检测用户提供的输入类型，无需询问——直接选择对应处理方式：

| 用户提供 | 如何处理 |
|---------|---------|
| 文字描述（需求/功能） | 从零生成；推断产品后询问模式 |
| Figma URL | 编辑已有文件；先读取当前内容再操作（见 figma-ids-design.md Edit 流程） |
| 截图 / 图片 | 分析视觉语言与布局结构，在 Figma 中复现并应用 IDS tokens |
| PRD / Confluence 链接 | 提取关键需求后生成对应页面 |
| 代码文件（HTML / JSX / TSX） | 分析组件结构与交互逻辑，反向还原为 IDS 规范的 Figma 设计稿 |
| 以上类型组合 | 综合使用——代码/描述用于结构分析，截图/URL 用于视觉参考 |
| 仅有模糊概念 | 询问：*"Can you share a screenshot, Figma URL, or describe the page/feature in more detail?"* |

## 本目录资产（相对路径）

| 路径 | 用途 |
|------|------|
| [figma-ids-design.md](figma-ids-design.md) | 主工作流：Pre-flight、模式确认、两阶段生成、编辑流程、交付 |
| [specs/canvas-layout.md](specs/canvas-layout.md) | 画布规格、Auto Layout、图层命名 |
| [specs/token-system.md](specs/token-system.md) | 完整 Token 速查表（Quick Start 卡未覆盖的 token 在此查） |
| [specs/component-rules.md](specs/component-rules.md) | 组件来源、图标规范、状态完整性、内容真实性 |
| [specs/delivery-checklist.md](specs/delivery-checklist.md) | 交付清单（分级检查项）、交付摘要输出格式 |
| [components-index.json](components-index.json) | 组件 variant → key 索引（按需搜索，勿全量加载） |
| [business-configs/](business-configs/) | 各产品线配置（Guided Mode 时加载对应 `[product].md`） |
| [fetch-components.sh](fetch-components.sh) | 刷新组件索引（需 `FIGMA_TOKEN`） |
| [README.md](README.md) | 仓库说明、MCP 安装示例、环境变量 |

## MCP 与 Cursor

1. 配置 **Figma MCP**（Personal Access Token，读写权限）。具体写法见 [README.md](README.md)；Cursor 侧以编辑器 MCP 文档为准。
2. 调用 MCP 工具前**查看当前环境提供的工具 schema**（参数名以实际 MCP 为准）。
3. Figma REST 调用（如刷新 tokens）以 [figma-ids-design.md](figma-ids-design.md) 中的命令为准；MCP 优先，REST 补全。

## Common Patterns | 常见请求模板

For frequent request types, use the matching Phase 1 skeleton directly — no need to invent structure from scratch.

### 列表 / 数据管理页 (List & Data Management)

**Trigger:** "create a [X] management page", "list of [resources]", "data table for [entity]"

```
Proposed structure — [Page Name]:

Layout:  Page Header → Filter Bar → Table → Pagination
         (Consult business config for frame nesting and spacing rules)
Key components:
  - IDS Table with [N] columns: [col names]
  - IDS Input + Select for filters
  - IDS Button (Primary) for main action
  - IDS Pagination at bottom

States this pass: Default populated view
```

### 表单 / 配置页 (Form & Settings)

**Trigger:** "create / edit form", "settings page", "configuration panel"

```
Proposed structure — [Page Name]:

Layout:  Page Header → Form Sections (grouped by topic) → Footer Actions (Save / Cancel)
         (Consult business config for frame nesting and spacing rules)
Key components:
  - IDS Input, Select, Switch, Radio for fields
  - IDS Button (Primary + Default) for footer
  - Section dividers with Heading/4 labels

States this pass: Empty form (default) + Validation error state
```

### Dashboard / 概览页 (Dashboard)

**Trigger:** "dashboard", "overview page", "home page", "summary"

```
Proposed structure — [Page Name]:

Layout:  Page Header → Stats Row (3-4 metric cards) → [Chart Zone / Activity Feed / Detail Panel]
         (Consult business config for frame nesting and spacing rules)
Key components:
  - IDS Card for metric tiles
  - Chart placeholder frames (annotated with chart type)
  - IDS Table or List for activity/detail

States this pass: Populated view
```

### 空状态 / 引导页 (Empty State / Onboarding)

**Trigger:** "empty state", "zero state", "onboarding", "getting started"

```
Proposed structure — [Page Name]:

Layout:  Centered zone — Illustration placeholder → Headline → Body copy → CTA button
Key components:
  - IDS Button (Primary) for main CTA
  - IDS Button (Default) for secondary action (optional)

States this pass: Empty state only
```

### 在已有页面添加元素 (Add to Existing)

**Trigger:** user provides a Figma URL + "add [X]", "insert [X]", "put [X] in"

Skip Phase 1 structure preview. Go directly to Edit flow (E1 → E2 → E3 in figma-ids-design.md):
read the existing file → identify the target location → add only the requested element.

---

## 执行顺序（摘要）

完整步骤以 [figma-ids-design.md](figma-ids-design.md) 为准；此处仅作快速索引：

1. **Pre-flight**：从 Quick Start 卡读 Token，按需搜索 components-index.json，询问 Product / IDS 模式。
2. **生成**：Phase 1 先以文字/ASCII 描述结构，等用户确认；Phase 2 再执行 MCP 操作，按需读取 specs 文件。
3. **交付**：运行 [specs/delivery-checklist.md](specs/delivery-checklist.md) 自检，输出结构化摘要与 Next Steps。

## 更新本技能内容

```bash
git -C ~/.cursor/skills/figma-mcp-skill pull
```

上游仓库：<https://github.com/Vanessa723/figma-mcp-skill>
