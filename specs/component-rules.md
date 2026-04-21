# Component, Icon & Content Rules
# 组件、图标与内容规范

Reference this file for component sourcing, icon usage, state completeness, and content quality requirements.

---

## Component Source | 组件来源

### Both Modes — Base IDS Rule (always applies)

**All standard controls must come from the IDS UI Kit** — no hand-drawing:
`https://www.figma.com/design/zANozorPV3t5sueU20e0Nx`

Never hand-draw: Button, Input, Select, Table, Modal, Tag, Badge, Checkbox, Radio, Switch, Tabs, Pagination, etc.

Components with underscore prefix (`_`) cannot be used directly — internal/base components only. Exception: approved exceptions listed in each product's business config.

If a needed component does not exist in IDS: compose from IDS primitives first. Only hand-draw as a last resort, and annotate as `Custom — not in IDS`.

---

### Guided Mode | 引导模式

- Load the product's business config for available Biz Components
- Use a Biz Component when it's clearly designed for the current scenario
- Do not force-fit a Biz Component that distorts the design intent — compose from IDS base components following the Design Language instead
- Layout decisions are creative and open; Biz Components define the vocabulary, not the layout

### Open Mode | 开放模式

- No Biz Component requirements — compose freely from IDS base components
- Custom components can be created for novel layouts or interactions that have no IDS equivalent
- All custom components must be annotated as `Custom — requires development [Simple/Medium/Complex]` in layer name
- Document custom components in the Annotation frame with:
  - Design rationale (why this component is needed, what IDS alternatives were considered)
  - Expected development cost estimate

---

## Icon Rules | 图标规范

只允许使用 IDS Icon 库中的图标（共 7 组），禁止引入外部图标库。

- **Only use icons from the IDS Icon library** (7 icon sets within the file)
- No external icon libraries (Material, Heroicons, Feather, etc.)
- Icon sizes: 12 / 16 / 20 / 24px only

### Icon stroke (outer + inner) | 图标外描边与内描边

When an icon uses **both** an outer stroke and an inner stroke (双线 / 双描边):

| Property | Outer stroke (外描边) | Inner stroke (内描边) |
|----------|----------------------|------------------------|
| **Weight** | **1** | **1** |
| **Position** | **Center** | **Center** |

**Visual rule:** The inner stroke must **not** read as protruding past the outer stroke’s silhouette (内描边在视觉上不得突破外描边轮廓).

**Figma execution (same file / new icons):**

1. **Stroke stack order** — In the strokes list, keep the **outer stroke entry below** the **inner stroke entry** (outer renders underneath, inner on top). That preserves the outer contour as the perceived outside edge and keeps the inner treatment visually contained.
2. **Joins / caps** — Prefer **Round join** (and **Round cap** on open paths) so miters or square caps do not spike the inner stroke outside the outer stroke at corners or endpoints.
3. **Geometry** — Use clean, merged vector paths (Outline stroke / boolean flatten when needed) so dual center strokes do not mis-register and expose the inner stroke beyond the outer ring.

When generating or auditing icons via MCP, apply these values explicitly and flag any icon that violates the visual rule.

---

## Complete State Design | 完整状态设计

交互组件必须覆盖所有相关状态，不能只交付 Default 态。

Interactive components must cover all relevant states. Delivering only the Default state is not acceptable:

| Component type | Required states |
|---------------|----------------|
| Buttons, links | Default → Hover → Active → Disabled → Loading |
| Inputs, selects | Default → Focus → Filled → Error → Disabled |
| Table rows | Default → Hover → Selected |
| Data regions | Loading (skeleton) → Populated → Empty → Error |

> **Open Mode:** Default state + 1-2 key states sufficient. Full state coverage is required only in Guided Mode.

---

## Content Authenticity | 内容真实性

所有文案必须使用真实业务词汇，禁止 Lorem Ipsum。UI 语言：全英文，不得出现中文字符。

- All copy must reflect real product vocabulary — **no Lorem Ipsum, no placeholder text**
- UI language: **English only throughout** — no Chinese characters anywhere in the generated design
- Tables and lists must contain **at least 3 rows of distinct, realistic data** to convey visual density and data variety
- Status values, timestamps, resource names, user handles — all should look like production data
