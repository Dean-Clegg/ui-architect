---
name: "design-new-screen"
description: "Design a new UI screen or section one at a time by grounding in its functionality and flow, then proposing three principle-backed design directions as text sketches for the user to choose from, then implementing the chosen one using the project's own components and theme. Use when the user asks to create, design, or add a new screen, section, page, or view."
license: "MIT"
metadata:
  author: "Dean Clegg"
  version: "1.0.0"
---

# Design a New Screen

## Overview
Designs one screen or section at a time. It first grounds itself in who uses the screen and what it must do, then proposes three genuinely distinct design directions as text sketches — each justified by named UI/UX principles and proven real-world patterns — and lets the user choose before any code is written. Implementation uses the project's existing design substrate; new components are added only when a chosen design truly needs them.

## Prerequisites Checklist
- [ ] `detect-design-substrate` has run and reported the stack + substrate
- [ ] The discovered component/token vocabulary is known
- [ ] The user has described the functionality the screen needs

## Step-by-Step Guide

### 1. Ground the design (always ask)
Before proposing anything, establish context with up to three tight questions. Skip any the project context already answers, and confirm inferences instead of asking blank questions.

Cover:
- **Who / where / when** — the user, their device/surface, and the moment of use.
- **The one primary action** — what the screen most needs the user to do.
- **Screen archetype** — list, list-detail, form/wizard, dashboard, settings, feed, empty/onboarding, etc.

If context already answers one (e.g. a mobile-first PWA used mid-task), state the assumption and move on: "Assuming mobile, primary action is 'roll' — correct me if not."

### 2. Propose three directions as text sketches
Produce three meaningfully different directions (not three shades of one idea). Follow the house style in [sketching.md](references/sketching.md). Each direction includes:

- A **box/ASCII layout sketch** showing structure and hierarchy.
- A **theming note in words** — how it uses the project's tokens/components (colors, emphasis, surfaces).
- A **wording note** — proposed titles, labels, and key microcopy, per [microcopy.md](references/microcopy.md).
- A **responsive note ONLY if the layout reflows** — rows of items, grids, tables, side-by-side panels. Omit for atomic layouts (a lone button/title/input do not need one).
- **Pros / cons.**
- The **named principle(s)** it leans on, drawn from [principles.md](references/principles.md) and [patterns.md](references/patterns.md).

Default to exactly three. If the screen genuinely can't support three distinct directions, offer two and say why. The user can always request more ("give me 3 more").

### 3. Let the user choose
The user picks one direction, or asks for more, or blends elements across directions. Do not start building until a direction is chosen.

### 4. Implement the chosen direction
Build using the detected substrate's real components and tokens:
- Compose from existing components; reuse patterns already in the project.
- Use theme tokens, never hardcoded colors/spacing.
- Apply the agreed microcopy.
- Honor accessibility from [principles.md](references/principles.md) (focus order, contrast, labels, touch targets where relevant).

### 5. Add new components only when needed
If the chosen design requires a building block that doesn't exist:
- Create it as a proper reusable component in the project's convention.
- If the substrate is Storybook, add a story for it.
- If the substrate is a component library without Storybook, place it alongside the others.
- Keep additions minimal — build what the screen needs, not a speculative kit.

### 6. Verify
Run the project's build/typecheck. Confirm the screen composes from the design system and introduces no hardcoded styles.

## Common Workflows

### Workflow: New screen on a Storybook project
Ground → 3 sketches → choose → implement with catalogued components → add story if a new component was needed → verify.

### Workflow: New screen, greenfield (minimal system just created)
Ground → 3 sketches → choose → implement against the minimal tokens/components → verify.

## Troubleshooting

### Issue: The three directions feel too similar
**Solution:** Vary the *structural* approach, not just styling — e.g. dense list vs focused single-card vs split master-detail. See [patterns.md](references/patterns.md).

### Issue: User wants to skip grounding
**Solution:** Keep it to a single confirming sentence of inferred context, then proceed. Never design fully blind, but don't force a questionnaire.

## Best Practices
- One screen or section per invocation.
- Describe-then-build: sketches are cheap and discardable; code comes only after a choice.
- Justify every direction from principles + real-world patterns, freshly each time (no stored taste profile).
- Consider responsiveness only where the layout actually reflows.
- Always propose wording, not just layout.
