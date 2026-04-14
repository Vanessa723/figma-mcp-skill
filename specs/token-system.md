# Design Token System
# 设计 Token 规范

Reference this file for token coverage rules and the quick-reference lookup table.

---

## Token Coverage — No Hardcoded Values | Token 全覆盖 — 禁止硬编码

每个视觉属性都必须引用 token，禁止出现裸值。因为使用了 token，切换到暗色模式只需一键切换变量模式。

Every visual property must reference a token. Bare values (`#3A86FF`, `14px`, `rgba(0,0,0,0.5)`) are not permitted.

| Property | Token category | Example tokens |
|----------|---------------|----------------|
| Text color | Color Style | `Text/Primary`, `Text/Secondary`, `Character/Secondary .45` |
| Background | Color Style | `Gray/gray-1`, `Gray/White`, `Neutral/1` |
| Brand color | Color Style | `Primary (Infra Blue)/6`, `Primary (Infra蓝)/8` |
| Semantic states | Color Style | `Dust Red/6` (error), `Neutral/5` (disabled), `Polar Green/2` (success) |
| AI surfaces | Color Style | `AI/5/BgPrimary`, `AI/5/Text`, `AI/4/BgHoverFocused` |
| Typography | Text Style | `Text Base/Normal`, `Heading/4`, `Body/regular`, `Text SM/Normal` |
| Shadows | Effect Style | `boxShadow`, `Component/Button/primaryShadow` |
| Spacing | Spacing Token | Use IDS spacing tokens — no raw pixel values |

> **Token-based theming:** Because tokens are used throughout, switching the entire design to dark mode requires only a single variable mode swap. You do not need to deliver a dark mode version — just ensure 100% token coverage and the dark switch will work automatically.

---

## Post-Generation Token Audit | 生成后 Token 检查

- [ ] No bare hex color values anywhere
- [ ] No bare font sizes (all Text Styles applied)
- [ ] No bare shadow values (all Effect Styles applied)
- [ ] All spacing uses IDS spacing tokens

---

## Token Quick Reference | Token 速查表

### Color Tokens

| Use case | Token |
|----------|-------|
| Primary text | `Text/Primary` / `Character/Primary .85` |
| Secondary text | `Text/Secondary` / `Character/Secondary .45` / `Gray/gray-7` |
| Brand primary | `Primary (Infra Blue)/6` |
| Brand dark | `Primary (Infra蓝)/8` |
| Page background | `Gray/gray-1` |
| Card / white surface | `Gray/White` / `Extra/white` |
| Disabled | `Gray/gray-6` / `Neutral/5` |
| Error | `Dust Red/6` |
| Warning | `Sunset Orange/6` |
| Success | `Polar Green/2` |
| AI surface background | `AI/5/BgPrimary` |
| AI text | `AI/5/Text` |
| AI hover | `AI/4/BgHoverFocused` |
| Clickable / link | `Other/Clickable` |

### Typography Tokens

| Use case | Token |
|----------|-------|
| Page title | `Heading/1` – `Heading/5` |
| Body text | `Text Base/Normal` / `Body/regular` |
| Small body | `Text SM/Normal` |
| Large body | `Text LG/Normal` |
| Bold body | `Text Base/Strong` / `Body/medium` |
| Button label | `Component/Button/Base` / `Component/Button/SM` |

### Effect Tokens

| Use case | Token |
|----------|-------|
| Card shadow | `boxShadow` |
| Secondary shadow | `boxShadowSecondary` |
| Tertiary shadow | `boxShadowTertiary` |
| Primary button shadow | `Component/Button/primaryShadow` |
| Default button shadow | `Component/Button/defaultShadow` |
| Danger button shadow | `Component/Button/dangerShadow` |
| Input focus shadow | `Component/Input/activeShadow` |
