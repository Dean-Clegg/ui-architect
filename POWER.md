---
name: "ui-architect"
displayName: "UI Architect"
description: "UI/UX architect that designs and reviews UI one screen at a time. Activate by saying \"use ui-architect\". Detects your design system, then does a touch-up, a polish with suggestions, or a full redesign — always building from your own components and theme. (v1.2.0)"
keywords: ["ui-design", "ux", "screen-design", "design-review", "redesign-screen", "design-system", "microcopy"]
author: "Dean Clegg"
---

# UI Architect

## Overview

**UI Architect** is a stack-agnostic UI/UX design engine for Kiro. It designs and reviews UI **one screen or section at a time**, grounded in UI/UX principles and proven real-world patterns, and always builds from the project's own components and theme rather than inventing one-off styles.

Activate it by saying **"use ui-architect"**. On activation it announces itself and waits — it never scans the project or spends effort until you say go.

## How It Works

1. **Detect the design substrate.** It inspects the project to identify the stack (React, Flutter, plain CSS, etc.) and the design system in place — Storybook, a component library plus tokens, raw CSS, or nothing — and reports it in one line. If nothing exists, it offers to create a *minimal* foundation matched to your stack (for example a `theme.dart` for Flutter or a `theme.css` for a CSS site), never over-scaffolding.
2. **Gather context.** For an existing screen it reads the current markup, components, data bindings, and behaviors. For a brand-new screen there is nothing to gather, so it skips straight to designing.
3. **Ground the design.** It asks a few tight questions — who uses it and on what device, the one primary action, the screen archetype — confirming inferences instead of interrogating.
4. **Work the chosen track** (see below).

## The Three Tracks

When reviewing an existing screen, you choose a track by intent — how much freedom you are giving the architect:

- **Track A — Touch-up.** Correctness only: enforce your tokens and theme, fix clashing colors or text, remove hardcoded values, fix wording accuracy. It adds, removes, and suggests nothing else.
- **Track B — Polish + suggest.** Everything in A, plus improvement suggestions — retreating elements (an "Add" button to a "+"), proposing use of data that is already present (an unused avatar field), or trimming redundancy. No full redesign.
- **Track C — Redesign.** Free rein: rethink the layout and flow. It proposes three principle-backed design directions as text sketches, you pick one, and it builds it.

New screens and sections always use Track C. If your requests outgrow the chosen track, it offers to switch (usually up to C) rather than silently exceeding it.

## The Governing Boundary: Propose, Don't Surprise

> You change how it looks freely. You never silently change what it does.

Layout, styling, theming, which UI elements appear, and wording are the architect's to change. A control's function, the data shown, and existing content are protected — the architect may change or remove them, but only as a proposal you approve first. The enemy is surprise, not change.

## Reuse First

The architect prefers extending an existing component (an optional icon or variant) over spawning near-duplicate one-off components. When a change to a shared component would be large or risky, it builds a clean local component instead and flags it as a "merge later" candidate, so shared code used across many screens is never broken silently.

## Getting Started

After installing, in any project just say:

- **"use ui-architect"** — activates the power; it will offer to gather your design context.
- **"review the [screen name] screen"** — scans an existing screen and offers Track A, B, or C.
- **"design a new [screen/section/component] that does X"** — grounds, proposes three design directions, and builds the one you choose.

## Structure

```
plugin.json                                   # agent-plugins manifest (loader)
POWER.md                                       # metadata + overview (this file)
skills/
  detect-design-substrate/SKILL.md             # runs first: detect + report substrate
  design-new-screen/SKILL.md                   # ground, propose 3 directions, build
  design-new-screen/references/                # shared knowledge:
    working-agreement.md                       #   activation gate, tracks, boundary, reuse
    principles.md                              #   named UI/UX heuristics
    patterns.md                                #   real-world archetype conventions
    sketching.md                               #   text-sketch house style
    microcopy.md                               #   wording / voice principles
  review-screen/SKILL.md                       # scan, then Track A / B / C
```

## License

MIT. See [LICENSE](LICENSE).
