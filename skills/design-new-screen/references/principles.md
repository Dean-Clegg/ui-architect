# UI/UX Principles

Named heuristics the power uses to justify every design direction. Each entry says what it is and when to apply it. These are the "why" behind a design — cite them by name when proposing directions.

## Visual hierarchy
Rank importance through size, weight, color, contrast, and position. The most important thing should be the most visually prominent. Apply on every screen: identify the one primary action or piece of information and make it dominant; de-emphasize secondary items.

## Gestalt grouping
The eye groups things by proximity, similarity, and enclosure. Use spacing and containers to signal what belongs together. Apply when a screen has multiple sections or clusters — group related controls, separate unrelated ones with whitespace rather than lines where possible.

## Hick's Law
The more choices presented, the longer the decision. Reduce the number of visible options; use progressive disclosure or grouping. Apply when a screen has many actions, filters, or menu items — consider collapsing, prioritizing, or defaulting.

## Fitts's Law
The time to hit a target depends on its size and distance. Make important/frequent targets large and easy to reach; keep primary actions within thumb reach on mobile. Apply to buttons, tap targets, and destructive-action placement.

## Cognitive load / recognition over recall
Don't make users remember things or think hard. Prefer recognizable labels and icons, sensible defaults, and visible state over hidden state. Apply everywhere: reduce steps, pre-fill sane defaults, show don't hide.

## Consistency
Reuse existing patterns, components, and wording. A new screen should feel like the same product. Apply by composing from the detected design substrate and matching established conventions rather than introducing novel styles.

## Progressive disclosure
Show only what's needed now; reveal detail on demand. Apply when a screen risks overwhelming — use accordions, "show more," secondary screens, or expandable cards for depth.

## Feedback & affordance
Interactive elements should look interactive and respond to interaction (hover, focus, active, loading, success/error states). Apply to every control; never leave an action without a visible response.

## Error prevention & recovery
Prevent mistakes (confirmations for destructive actions, disabled invalid states) and make recovery easy (clear errors, undo). Apply to forms, deletions, and any irreversible action.

## Accessibility (WCAG 2.2 essentials)
Not optional. On every screen ensure:
- Sufficient color contrast for text and meaningful UI.
- Visible focus indicators and a logical focus/tab order.
- Labels and ARIA roles on non-obvious interactive elements.
- Touch targets large enough (~44px) on touch surfaces.
- Never rely on color alone to convey meaning.

## How to use these in a proposal
For each design direction, name the one or two principles it leans on hardest — e.g. "Direction A favors Hick's Law and hierarchy: one dominant action, everything else demoted." This makes the reasoning legible and teaches the principle by showing it applied.
