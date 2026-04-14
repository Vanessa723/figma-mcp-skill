# Canvas & Layout Specs
# 画布与布局规范

Reference this file when setting up frames, applying Auto Layout, or delivering responsive variants.

---

## Canvas Specification | 画布规格

| Property | Value |
|----------|-------|
| Primary canvas | **1728 × 1117 px** |
| Background | `Gray/gray-1` token |
| Base grid | 8px |
| Content margin | 24px left/right |

---

## Auto Layout — Mandatory on All Frames | Auto Layout — 所有帧必须使用

所有帧、区块、组件组都必须使用 Auto Layout。

- Every frame, section, and component group must use Auto Layout
- Set correct horizontal/vertical resize behavior (Hug / Fill / Fixed as appropriate)

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

