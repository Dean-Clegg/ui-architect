# ui-architect

A stack-agnostic UI/UX architect for [Kiro](https://kiro.dev). It designs and reviews UI **one screen or section at a time**, grounded in UI/UX principles and proven real-world patterns, and always builds from the project's own components and theme.

## What it does

- **Detects your design substrate** — Storybook, a component library + tokens, raw CSS, or nothing — and reports it before doing anything. If nothing exists, it offers to create a *minimal* foundation matched to your stack (e.g. `theme.dart` for Flutter, `theme.css` for a CSS site), never over-scaffolding.
- **Grounds before designing** — asks a few tight questions (who/where/when, the primary action, the screen archetype), confirming inferences instead of interrogating.
- **Proposes before building** — for redesigns, it pitches three distinct design directions as text sketches (layout, theming notes, wording, pros/cons, and the principle each leans on) so you choose before any code is written.
- **Reuses first** — extends existing components rather than spawning near-duplicates, with a safety valve that avoids risky edits to shared components.

## The three tracks

When reviewing an existing screen, you pick a track by intent:

| Track | Intent | What it does |
|-------|--------|--------------|
| **A — Touch-up** | "Just check it over" | Correctness only: enforce tokens/theme, fix clashing colors/text, remove hardcoded values, fix wording accuracy. No adds, removes, or suggestions. |
| **B — Polish + suggest** | "Check it and suggest improvements" | Everything in A, plus retreating elements, proposing use of already-present data, trimming redundancy. No full redesign. |
| **C — Redesign** | "This doesn't look good, go wild" | Full rethink of layout and flow via three design directions. |

New screens and sections always use Track C. If your asks outgrow the chosen track, it offers to switch (usually up to C) rather than silently exceeding it.

## The governing boundary: propose, don't surprise

> You change how it looks freely. You never silently change what it does.

Layout, styling, theming, which elements appear, and wording are fair game. A control's function, the data shown, and existing content are protected — the architect may change or remove them, but only as a proposal you approve first. The enemy is surprise, not change.

## Skills

- `detect-design-substrate` — runs first; detects stack + substrate and reports it.
- `design-new-screen` — grounds, proposes three directions, builds the chosen one.
- `review-screen` — scans an existing target, then works Track A, B, or C.

Shared knowledge lives in `skills/design-new-screen/references/`: `principles.md`, `patterns.md`, `sketching.md`, `microcopy.md`, and `working-agreement.md`.

## Install

In Kiro's Powers UI, add a custom power from either:

- **GitHub:** `https://github.com/Dean-Clegg/ui-architect.git`
- **Local directory:** the path to this folder (handy while iterating).

Then activate it in a chat by saying **"use ui-architect"**.

## License

[MIT](LICENSE)
