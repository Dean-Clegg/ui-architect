---
name: "design-new-screen"
description: "Design a new UI screen, section, or component one at a time by grounding in its functionality and flow, proposing three principle-backed design directions as text sketches for the user to choose, then implementing the chosen one using the project's own components and theme. Use when the user asks to create, design, or add a new screen, section, page, view, or component."
license: "MIT"
metadata:
  author: "Dean Clegg"
  version: "1.1.0"
---

# Design a New Screen

## Overview
Designs one screen, section, or component at a time. It grounds in who uses it and what it must do, proposes three genuinely distinct design directions as text sketches — each justified by named principles — and lets the user choose before any code. Implementation uses the project's existing substrate; new components are added only when needed, reuse-first.

Follow the shared [working-agreement.md](references/working-agreement.md) for the conversation flow, the "propose don't surprise" boundary, scope discipline, and reuse rules. Keep spoken output terse.

## Prerequisites Checklist
- [ ] `detect-design-substrate` has run and reported stack + substrate
- [ ] The discovered component/token vocabulary is known
- [ ] The user described the functionality the new thing needs

## Step-by-Step Guide

### 1. Ground the design (always, briefly)
Ask up to three tight questions; skip any the context already answers, and confirm inferences instead of asking blind:
- **Who / where / when** — user, device/surface, moment of use.
- **The one primary action** — what it most needs the user to do.
- **Archetype** — list, list-detail, form/wizard, dashboard, settings, feed, empty/onboarding, etc.

Note: a brand-new screen has **no existing context to gather** — go straight from grounding to sketches. (Context-gathering only applies to existing targets, handled in `review-screen`.)

### 2. Propose three directions as text sketches
Per [sketching.md](references/sketching.md). Each direction:
- **Box/ASCII layout sketch** (structure + hierarchy).
- **Theming note (words)** — uses the project's real tokens/components.
- **Wording note** — titles, labels, key microcopy, per [microcopy.md](references/microcopy.md).
- **Responsive note ONLY if the layout reflows** (rows, grids, tables, split panels). Omit for atomic layouts.
- **Pros / cons.**
- **Named principle(s)** from [principles.md](references/principles.md) / [patterns.md](references/patterns.md).

Default three; offer two only if the screen can't support three distinct models, and say why. User can ask for more.

### 3. User chooses
Pick one, blend, or request more. Do not build until a direction is chosen.

### 4. Implement the chosen direction
Build from the substrate's real components and tokens:
- Compose from existing components; reuse established patterns.
- Theme tokens only — no hardcoded colors/spacing.
- Apply the agreed microcopy.
- Honor accessibility (focus order, contrast, labels, touch targets) per [principles.md](references/principles.md).
- Respect the boundary in the working agreement: even here, if a design implies a behavior/data change, surface it.

### 5. New components — reuse-first with the safety valve
Per the working agreement:
- Before creating a new component, check if an existing one extends safely with an optional prop — if small/safe, just do it.
- If extending would be large/risky, build a clean local component and label it a "merge later" candidate.
- If Storybook exists, add a story for genuinely new components.
- At the end, offer once to promote a new reusable component into the shared system.

### 6. Verify
Run the project's build/typecheck. Confirm it composes from the design system with no hardcoded styles.

## Troubleshooting

### Issue: The three directions feel too similar
**Solution:** Vary the *structural* model, not just styling (dense list vs single-focus vs split). See [patterns.md](references/patterns.md).

### Issue: User wants to skip grounding
**Solution:** Confirm inferred context in one sentence, then proceed. Never design fully blind; never force a questionnaire.

## Best Practices
- One screen/section/component per invocation.
- Describe-then-build: sketches are cheap and discardable; code comes only after a choice.
- Justify from principles + real-world patterns, freshly (no stored taste profile).
- Responsiveness only where the layout reflows.
- Always propose wording, not just layout.
