# Canvas & Layout Specs
# 画布与布局规范

Reference this file when setting up frames, applying Auto Layout, or delivering responsive variants.

---

## Canvas Specification | 画布规格

| Property | Value |
|----------|-------|
| Primary canvas | **1728 × 1117 px** |
| Secondary canvas | **1440 × 900 px** (required for core workflow pages) |
| Background | `Gray/gray-1` token |
| Base grid | 8px |
| Content margin | 24px left/right |

---

## Auto Layout — Mandatory on All Frames | Auto Layout — 所有帧必须使用

所有帧、区块、组件组都必须使用 Auto Layout，这样才能让 1440px 画布自动适配。

- Every frame, section, and component group must use Auto Layout
- Set correct horizontal/vertical resize behavior (Hug / Fill / Fixed as appropriate)
- This is what enables the 1440px secondary canvas to render correctly without manual re-layout

---

## Responsive Strategy (1728 → 1440) | 响应式策略

主画布 1728px，核心工作流页面必须同时交付 1440px 版本。1440 版本必须从 1728 自动缩放而来，不允许手动重新布局。

The primary canvas is 1728×1117px. For any **core workflow page** (a page users visit daily: dashboards, list pages, detail pages), also deliver a **1440×900px frame**.

Rules for the 1440 version:
- Do not manually re-layout — the 1440 frame must be derived from the 1728 frame by adjusting container widths only
- Content columns compress; sidebar and topbar remain fixed width
- If a layout breaks at 1440, it means Auto Layout was not set up correctly — fix the 1728 frame first
- Label the 1440 frame as `[PageName] — 1440` in the layer panel

Minimum supported width: **1280px**. If a layout cannot reasonably compress to 1280px without horizontal scroll, add a note in the Annotation frame explaining the constraint.

---

## Layer Naming Convention | 图层命名规范

每个图层必须使用语义化命名，镜像代码组件结构。

Every layer must have a semantic name that mirrors code component structure:

```
✓  Topbar / Sidebar / PageHeader / ContentArea / FilterBar / DataTable / ActionBar / EmptyState
✗  Frame 12 / Group 3 / Rectangle / Component 47
```

Layer hierarchy template:
```
[PageName]
  ├── Topbar
  ├── Sidebar
  ├── PageHeader
  └── ContentArea
        ├── [SectionName]
        │     ├── [ComponentName]
        │     └── ...
        └── ...
```

---

## Annotation Frame | 标注帧（每次交付必需）

每个设计帧旁边必须附一个 Annotation 帧，记录使用的 token 名称、组件来源、布局尺寸。

Alongside every design frame, include a separate **Annotation** frame that documents:
- Token names used for all colors, typography, and effects
- Which IDS / Biz components were inserted (by component name)
- Layout measurements (sidebar width, topbar height, content area dimensions)
- Any custom components (with "Custom — not in IDS" flag)
