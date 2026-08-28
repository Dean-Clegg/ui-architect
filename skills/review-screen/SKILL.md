---
name: "review-screen"
description: "Review an existing UI screen or section against the project's design system and UI/UX principles, reporting both conformance drift and UX opportunities, then either doing a light conformance pass or a full redesign based on the user's choice. Use when the user asks to review, audit, clean up, or align a screen to the design system, or to improve an existing screen."
license: "MIT"
metadata:
  author: "Dean Clegg"
  version: "1.0.0"
---

# Review a Screen

## Overview
Reviews one existing screen or section at a time. It scans the screen against the project's design substrate and against UI/UX principles, then reports two things: conformance drift (hardcoded values, raw elements, off-system components) and any UX opportunities it spots. It then offers two tracks — a light conformance pass that keeps the design as-is, or a deeper redesign — and proceeds with the user's choice. It defaults to the safe track and never surprises the user with a redesign.

## Prerequisites Checklist
- [ ] `detect-design-substrate` has run and reported the stack + substrate
- [ ] The target screen/section has been identified
- [ ] The discovered component/token vocabulary is known

## Step-by-Step Guide

### 1. Scan the screen
Inspect the target screen for:
- **Conformance drift** — hardcoded colors/spacing, raw HTML elements where design-system components exist, one-off styled components, duplicated styling, missing use of theme tokens.
- **Accessibility gaps** — missing focus states, labels, insufficient contrast, small touch targets (per [principles.md](../design-new-screen/references/principles.md)).
- **UX opportunities** — overloaded controls, weak hierarchy, unclear primary action, confusing flow, poor wording (per [patterns.md](../design-new-screen/references/patterns.md) and [microcopy.md](../design-new-screen/references/microcopy.md)).

### 2. Report findings with evidence
Present a concise report with specific locations. Separate the two categories clearly:
- **Conformance drift** — e.g. "3 hardcoded hex colors in `Foo.tsx`; raw `<button>` where `Button` exists."
- **UX opportunities** — e.g. "the filter row has 12 buttons; hierarchy is flat; the primary action isn't visually dominant."

### 3. Offer the two tracks (ask)
Let the user choose, with the scan as evidence:

- **Track A — Conformance pass (light, default):** keep the current design and functionality. Replace hardcoded values with tokens/components, fix accessibility gaps, align to the design system. Low risk, no redesign.
- **Track B — Redesign (deep):** dive into the functionality and flow, then run the three-direction sketch loop (hand off to `design-new-screen`'s process) to propose new designs.

Recommend Track A unless the drift is minor and the UX opportunities are significant, in which case surface that Track B may be worthwhile — but let the user decide.

### 4a. Execute Track A (conformance)
- Replace hardcoded styles with the project's tokens.
- Swap raw elements for design-system components.
- Fix accessibility gaps.
- Improve obvious wording where low-risk (per [microcopy.md](../design-new-screen/references/microcopy.md)).
- Do not restructure the layout or change functionality.
- Verify with the project's build/typecheck.

### 4b. Execute Track B (redesign)
- Ground in the screen's functionality and flow (confirm inferred context).
- Propose three design directions as text sketches per [sketching.md](../design-new-screen/references/sketching.md).
- User chooses; implement using the substrate; add components (and stories, if Storybook) only when needed.
- Verify.

## Common Workflows

### Workflow: "Make this screen use my components"
Scan → report drift → Track A → replace raw markup/values with components + tokens → verify. Usually no redesign.

### Workflow: "This screen feels off, improve it"
Scan → report drift + UX opportunities → likely Track B → 3 directions → choose → implement → verify.

## Troubleshooting

### Issue: User expected a redesign but Track A was chosen (or vice versa)
**Solution:** The tracks are explicit and asked up front. If the user's intent shifts mid-task, re-confirm which track and continue.

### Issue: Scan finds no drift and no opportunities
**Solution:** Report that the screen already conforms and reads well; recommend no change rather than inventing work.

## Best Practices
- One screen or section per invocation.
- Report before acting; let the user pick the track with evidence in hand.
- Default to the non-destructive track; never surprise with a redesign.
- Keep conformance passes purely presentational — no functional or layout changes.
- Justify UX findings from named principles + real-world patterns.
