---
name: "review-screen"
description: "Review an existing UI screen, section, or component against the project's design system and UI/UX principles, reporting styling drift and UX opportunities, then working one of three user-chosen tracks: a correctness touch-up, a polish with improvement suggestions, or a full redesign. Use when the user asks to review, audit, clean up, polish, redesign, or align an existing screen, section, or component to the design system."
license: "MIT"
metadata:
  author: "Dean Clegg"
  version: "1.1.0"
---

# Review a Screen

## Overview
Reviews one existing screen, section, or component at a time. It gathers context on the target, scans it against the design substrate and UI/UX principles, and reports two things — styling drift and UX opportunities — then works one of three tracks the user chooses by intent: a touch-up (A), a polish-with-suggestions (B), or a redesign (C). It is proactive about proposing improvements but never enacts behavior/data/content changes without a yes, and never surprises the user by touching things off-screen.

Follow the shared [working-agreement.md](../design-new-screen/references/working-agreement.md) for the flow, the "propose don't surprise" boundary, scope discipline, and reuse rules. Keep spoken output terse.

## Prerequisites Checklist
- [ ] `detect-design-substrate` has run and reported stack + substrate
- [ ] The target screen/section/component is identified
- [ ] The discovered component/token vocabulary is known

## Step-by-Step Guide

### 1. Gather context
Read the target and its setup: current markup/widgets, which components it uses, its data bindings and behaviors (handlers, navigation, API calls). You must understand what it *does* so the boundary can protect it.

If the target is a **shared component**, map every place it's used and note the blast radius before proposing changes (per the working agreement).

### 2. Scan and report (two categories, with evidence)
- **Styling drift** — hardcoded colors/spacing, raw elements where design-system components exist, one-off styled components, duplicated styling, missing token use, accessibility gaps (per [principles.md](../design-new-screen/references/principles.md)).
- **UX opportunities** — weak hierarchy, unclear primary action, overloaded controls, awkward flow, poor wording (per [patterns.md](../design-new-screen/references/patterns.md) and [microcopy.md](../design-new-screen/references/microcopy.md)). Be proactive here — name real improvements, including behavior reshapes worth proposing (e.g. "this modal could be a dropdown").

Report with specific locations; keep it scannable.

### 3. Offer the three tracks (one line each)
The user picks by intent — how much freedom they're giving you (see the working agreement).
- **Track A — Touch-up (default):** "Correctness only — tokens/theme, fix clashes and hardcoded values, fix wording accuracy. No adds, removes, or suggestions."
- **Track B — Polish + suggest:** "A, plus improvement suggestions — retreat elements, propose using already-present data or trimming redundant bits. No redesign."
- **Track C — Redesign:** "Free rein — rethink layout and flow. 3 design directions using your theme, you pick one, I build it."

Recommend A unless drift is minor and UX opportunities are significant; then flag B or C. User decides.

### 4a. Track A — touch-up
- Replace hardcoded styles with tokens; swap raw elements for design-system components; fix accessibility gaps.
- Fix wording accuracy (per [microcopy.md](../design-new-screen/references/microcopy.md)); never let a label misrepresent its action.
- **Do not** add, remove, restructure, or suggest anything beyond these corrections. If you spot a worthwhile improvement, note that Track B would cover it — don't do it here.
- Verify with the project's build/typecheck.

### 4b. Track B — polish + suggest
- Everything Track A does, **plus**: retreat existing elements (label/icon/color/size), and propose *adding* already-present data (e.g. an unused avatar field) or *removing* redundant elements — always confirmed first.
- Surface slightly-bigger-but-obvious wins as **optional proposals** (e.g. "search + button work better in one row — want that too?"). Keep suggestions proportional; don't nibble the screen into a redesign.
- **Do not** rethink the overall layout/flow. If the user's asks pile into structural territory, use the switch-track nudge and offer Track C.
- Honor the boundary throughout; verify.

### 4c. Track C — redesign
- Ground in the target's functionality and flow (confirm inferred context).
- Propose three text-sketch directions per [sketching.md](../design-new-screen/references/sketching.md).
- Honor the boundary: preserve behavior/data/content; any change to them is a labeled proposal in the sketch, confirmed before building. Never let a control silently disappear.
- User chooses; implement using the substrate; add components reuse-first (safety valve applies); add stories if Storybook exists.
- Verify.

## Troubleshooting

### Issue: A redesign would drop or change a control's behavior
**Solution:** Surface it explicitly and offer an alternative ("this opens a modal — we could move that into a dropdown, or keep it as an icon button"). Never remove functionality silently.

### Issue: Scan finds no drift and no opportunities
**Solution:** Say the screen already conforms and reads well; recommend no change rather than inventing work.

### Issue: User picked A or B but keeps asking for redesign-level changes
**Solution:** Apply the switch-track nudge — name that the asks are closer to a redesign and offer to switch to Track C. Never silently exceed the declared track.

### Issue: The target is a shared component needing a big rework
**Solution:** Apply the reuse safety valve — if extending it risks other usages, build a new local component and label it a "merge later" candidate; tell the user the blast radius.

## Best Practices
- One screen/section/component per invocation.
- Report before acting; let the user pick the track (A/B/C) with evidence in hand.
- Default to the touch-up (A); never surprise with a redesign.
- Treat the chosen track as declared intent, not a cage — if the asks outgrow it, use the switch-track nudge and offer to move up (usually to C).
- Be proactive proposing improvements; enact behavior/data/content changes only on a yes.
- Keep Track A purely corrective, Track B free of layout/flow rethinks.
