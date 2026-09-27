---
name: apple-design-sdd
description: >
  Implement Apple-style UI (Human Interface Guidelines + Liquid Glass) using
  Spec-Driven Development. The agent MUST author a spec, extract the Apple design
  into a concrete design spec, get approval at each gate, then implement and
  verify against the spec. Use whenever the user asks for an Apple / iOS / macOS /
  Liquid Glass look in any project (web, SwiftUI, React, Figma spec).
---

# Apple Design — Spec-Driven

Do not jump to code. Drive every request through the pipeline below. Each phase
produces a file and ends at an approval GATE. Never enter a phase before the
previous gate is approved by the user.

## Pipeline
requirements.md → design.md (Apple design pulled in) → tasks.md → implement → verify.md

Store artifacts under `specs/<feature-slug>/`.

## Phase 0 — Intake
Ask only what blocks the spec (do NOT interview endlessly):
1. Target surface: web (HTML/CSS/React) or native (SwiftUI)?
2. Platform metaphor: iOS/iPadOS or macOS?
3. New project or existing codebase to adapt?
4. Scope: which screens/components?
Record answers at the top of `requirements.md`. Then STOP at GATE 0.

## Phase 1 — requirements.md
Write testable requirements in EARS-style acceptance criteria. GATE 1.

## Phase 2 — design.md  (PULL THE DESIGN HERE)
1. Consult the authoritative sources (see References). Fetch the relevant HIG pages
   when tools allow and cite what informed each decision; otherwise derive from the
   token defaults and state that assumption.
2. Emit resolved design tokens for THIS project (not generic prose).
3. Map every requirement to a component + tokens.

### Apple token defaults (starting point to resolve from)
- Type: `-apple-system, "SF Pro Text", "SF Pro Display", "Helvetica Neue", Arial, sans-serif`;
  serif `"New York", ui-serif, Georgia, serif`. Scale (px/lh): LargeTitle 34/41 · Title1 28/34 ·
  Title2 22/28 · Title3 20/25 · Headline 17/22 · Body 17/22 · Callout 16/21 · Subhead 15/20 ·
  Footnote 13/18 · Caption 12/16. Weights 400/500/600.
- Color: one accent per view. Blue `#007AFF` / `#0A84FF`. Semantic labels & backgrounds that
  flip with `prefers-color-scheme`. BG light `#FFFFFF`/`#F2F2F7`; dark `#000000`/`#1C1C1E`.
- Spacing: 4/8/12/16/20/24/32/44. Gutter 16-20. Reading width ~680px. Tap >=44px.
- Shape: controls 8-12, cards 16-20, sheets 24; continuous ("squircle") corners. Elevation via
  translucency + soft diffuse shadow, not hard borders.
- Liquid Glass: `background: rgba(255,255,255,.55)` (dark `rgba(30,30,30,.55)`);
  `backdrop-filter: blur(20px) saturate(180%)` (+ `-webkit-` + solid fallback);
  `border: .5px solid rgba(255,255,255,.25)`. Chrome only, never content layer.
- Motion: 200-400ms, ease-out/spring; honor `prefers-reduced-motion`.
GATE 2: user approves design.md before any code.

## Phase 3 — tasks.md
Small, ordered, independently verifiable tasks. Each cites the requirement(s) and design
section it satisfies. GATE 3.

## Phase 4 — Implement
Execute tasks in order. Emit light + dark via `prefers-color-scheme` and semantic vars.
Do NOT introduce values absent from design.md; if a gap appears, pause and update design.md.

## Phase 5 — verify.md  (HIG compliance)
Check the build against the spec AND the HIG checklist. Report pass/fail per item.

## Rules of engagement
- One gate at a time; never skip ahead. If the user says "just build it", still produce a
  minimal requirements.md + design.md first, fast, then implement.
- Removing conflicting styles is part of the work for existing projects — flag them in
  design.md §Conflicts.
- Font licensing: SF Pro / New York are Apple-restricted; state the fallback on non-Apple web.

## References
- Human Interface Guidelines: https://developer.apple.com/design/human-interface-guidelines
- Apple Design Resources: https://developer.apple.com/design/resources/
- WWDC26 Design guide: https://developer.apple.com/wwdc26/guides/design/
- Create UI prototypes using agents in Xcode: https://developer.apple.com/videos/play/wwdc2026/227/
