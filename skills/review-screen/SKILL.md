---
name: "review-screen"
description: "Review an existing UI screen, section, or component against the project's design system and UI/UX principles, reporting both styling drift and UX opportunities, then doing either a light styling-conformance pass or a deep redesign based on the user's choice. Use when the user asks to review, audit, clean up, redesign, or align an existing screen, section, or component to the design system."
license: "MIT"
metadata:
  author: "Dean Clegg"
  version: "1.1.0"
---

# Review a Screen

## Overview
Reviews one existing screen, section, or component at a time. It gathers context on the target, scans it against the design substrate and UI/UX principles, and reports two things — styling drift and UX opportunities — then offers a light styling pass (Track A) or a redesign (Track B). It is proactive about proposing improvements but never enacts behavior/data/content changes without a yes, and never surprises the user by touching things off-screen.

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

### 3. Offer the two tracks (one line each)
- **Track A — styling pass (default):** "Keep the layout and behavior; fix hardcoded values, swap in your components, fix accessibility. No redesign."
- **Track B — redesign:** "Rethink the layout — I'll propose 3 design directions using your theme, you pick one, I build it."

Recommend A unless drift is minor and the UX opportunities are significant; then flag that B may be worth it. User decides.

### 4a. Track A — styling pass
- Replace hardcoded styles with tokens; swap raw elements for design-system components.
- Fix accessibility gaps.
- Improve low-risk wording (per [microcopy.md](../design-new-screen/references/microcopy.md)); never let a label misrepresent its action.
- **Do not** change layout, behavior, data, or content. If you spot a worthwhile behavior/UX change, *propose* it — don't enact it in Track A.
- Verify with the project's build/typecheck.

### 4b. Track B — redesign
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

### Issue: The target is a shared component needing a big rework
**Solution:** Apply the reuse safety valve — if extending it risks other usages, build a new local component and label it a "merge later" candidate; tell the user the blast radius.

## Best Practices
- One screen/section/component per invocation.
- Report before acting; let the user pick the track with evidence in hand.
- Default to the styling pass; never surprise with a redesign.
- Be proactive proposing behavior/UX improvements; enact them only on a yes.
- Keep Track A purely presentational — no functional, data, or layout changes.
