# Delivery Checklist
# 交付清单

Run this checklist before considering the design complete. Each item is marked with its priority tier:
- **[Must]** — Required for all non-Explore deliveries. Blocking.
- **[Should]** — Strongly recommended; skip only with explicit justification.
- **[Explore-OK]** — May be skipped in Explore Mode.

---

## Components

- [ ] **[Must]** All base UI from IDS UI Kit — no hand-drawn Button / Input / Select / Table / Modal / etc.
- [ ] **[Must]** Guided Mode: Design language applied (navigation shell, page identity, data patterns consistent with product config)
- [ ] **[Should]** Guided Mode: Biz Components used where they clearly fit; IDS primitives composed per design language where not
- [ ] **[Must]** Open Mode: Custom components annotated with rationale and complexity (`Custom — [Simple/Medium/Complex]`)
- [ ] **[Should]** No component detached unless absolutely necessary

## Token Coverage

- [ ] **[Must]** Zero bare hex values in the design
- [ ] **[Must]** Zero bare font sizes (all Text Styles applied)
- [ ] **[Must]** Zero bare shadow values (all Effect Styles applied)
- [ ] **[Must]** All spacing uses IDS spacing tokens

## Content Quality

- [ ] **[Must]** All copy is in English — no Chinese characters
- [ ] **[Must]** No Lorem Ipsum or placeholder text
- [ ] **[Should]** Tables/lists have 3+ rows of realistic, distinct data
- [ ] **[Should]** Guided Mode: Interactive components show Default + Hover + Disabled states
- [ ] **[Should]** Open Mode: Default state + 1-2 key states sufficient
- [ ] **[Should]** Data regions have Loading skeleton + Empty state + Error state (Guided Mode required; Open Mode optional)

## Visual Validation

- [ ] **[Must]** Screenshot taken of generated frame after Phase 2 — not skipped without justification
- [ ] **[Must]** No text clipping or descender cutoff visible in any text node
- [ ] **[Must]** No placeholder copy remaining ("Title", "Heading", "Button", "Label", "Lorem")
- [ ] **[Should]** No overlapping elements or blank zones due to Auto Layout issues
- [ ] **[Should]** All layer names are semantic — no "Frame N", "Group N", or "Rectangle" remaining

## Layout

- [ ] **[Must]** Primary frame: 1728 × 1117 px
- [ ] **[Must]** All frames and groups use Auto Layout
- [ ] **[Must]** Layer names are semantic (no "Frame 12", "Rectangle")

## Handoff

- [ ] **[Must]** File is created under SHOPEE SINGAPORE PRIVATE LIMITED organization
- [ ] **[Must]** File is NOT created inside the IDS design system file (zANozorPV3t5sueU20e0Nx)
- [ ] **[Must]** Any custom components flagged as "Custom — not in IDS"

---

## Delivery Summary Format | 交付摘要格式

After completing the checklist, output the following summary in the conversation:

```
Design delivered: [Page/Feature name] — [Mode: Product / IDS]

Quality tally:
  Components   ✓ IDS sourced | X custom (annotated)
  Tokens       ✓ 100% coverage | or: ⚠ N bare values found
  States       ✓ All states present | or: ⚠ Missing: [list]
  Visual       ✓ Screenshot validated, N issues fixed | or: ⚠ Issues requiring attention: [list]
  Layout       ✓ 1728px primary | ✓ Auto Layout applied
  Handoff      ✓ Org correct | ✓ Custom components flagged

Next steps — pick one:
  1. "Run token audit" — verify all token coverage in detail
  2. "Add interaction states" — fill in Hover / Disabled / Loading states
  3. "Run UX evaluation" — evaluate the design against Nielsen's heuristics
```

> If any **[Must]** item is unchecked, **do not deliver** — fix it first and note it to the user.
> If only **[Should]** or **[Explore-OK]** items are unchecked, deliver and call them out in the summary with a ⚠ warning.
