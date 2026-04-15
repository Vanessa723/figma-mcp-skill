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

## Frame Nesting & Page Structure | 帧嵌套与页面结构

Navigation structure, frame nesting, and ContentArea spacing **vary by product**. Different products use different navigation shells (e.g., topbar + sidebar, sidebar-only, or other layouts).

**In Guided Mode, always read the product's business config** (`business-configs/[product].md`) before creating any frames. The business config defines:

- Navigation shell structure (which navigation elements exist and how they're arranged)
- Which elements are navigation-level vs content-level
- ContentArea padding and gap between modules
- How PageHeader relates to other elements structurally

**In Open Mode**, choose a navigation structure that fits the use case, using IDS components where available.

Generic layer hierarchy principle:
```
[PageName]
  ├── [Navigation elements]     ← defined by business config
  ├── [Page identity elements]  ← e.g. PageHeader — nesting depends on product
  └── ContentArea
        ├── [Module A]
        ├── [Module B]
        └── ...
```

---

## Layer Naming Convention | 图层命名规范

每个图层必须使用语义化命名，镜像代码组件结构。

Every layer must have a semantic name that mirrors code component structure:

```
✓  PageHeader / ContentArea / FilterBar / DataTable / ActionBar / EmptyState / Navigation / Sidebar
✗  Frame 12 / Group 3 / Rectangle / Component 47
```

> These are examples of semantic names, not a required set. The actual elements depend on the product's navigation structure.

