# Real-World Patterns

Proven conventions from well-designed products, organized by screen archetype. Use these to ground design directions in what already works, and to generate genuinely distinct structural options. Includes a responsive section at the end.

## Choosing distinct directions
Good directions differ in *structure*, not just color. When proposing three, vary the underlying layout model. Common structural models to draw from:
- **List** — a scannable vertical list of items.
- **List-detail (master-detail)** — list on one side/screen, detail on the other.
- **Single-focus / card flow** — one primary thing at a time, minimal chrome.
- **Grid / gallery** — tiles, good for visual or equal-weight items.
- **Dashboard** — summary widgets, KPIs, at-a-glance overview.
- **Wizard / stepper** — sequential steps for complex input.
- **Split / two-pane** — persistent context beside working area.

## Archetype conventions

### List / feed
- Most important attribute leads each row; secondary info muted.
- Provide search and/or filters when lists grow; keep filters compact.
- Show a clear empty state with a next action.
- Consider sticky headers or section grouping for long lists.

### List-detail
- Selecting an item opens detail; provide a clear way back on mobile.
- On wide screens, show list and detail side by side; on narrow, stack/navigate.
- Preserve list scroll position on return.

### Form / wizard
- Group related fields; one logical step per screen for long forms.
- Label clearly, show requirements inline, validate on blur/submit not aggressively.
- Primary action (Submit/Next) is dominant and consistently placed; secondary (Back/Cancel) de-emphasized.
- Show progress for multi-step flows.

### Dashboard
- Most important metric top-left (reading order); support scanning.
- Group by concern; avoid a wall of equal-weight widgets.
- Give each widget a clear title and a single job.

### Settings
- Group into labeled sections; use sensible defaults.
- Toggles for binary, selects for few options, keep destructive actions separate and confirmed.

### Empty / onboarding states
- Explain what goes here and give the primary action to fill it.
- Encouraging, brief; never a dead end.

### Detail view
- Lead with identity (title, key badges/metadata), then primary content, then secondary/related.
- Make the primary action obvious; group related actions.

## Mobile navigation patterns
- **Bottom nav** for 3-5 top-level destinations on mobile (thumb-reachable). Not for desktop-primary apps.
- **Back navigation** must be obvious when drilling into detail.
- Keep primary actions within thumb reach; avoid top-corner-only primary actions on mobile.

## Responsiveness (apply only where layout reflows)
Responsiveness matters when a layout contains elements that rearrange across widths. It does NOT matter for atomic elements — a single button, title, or input looks the same at any size.

Apply responsive thinking when a direction includes:
- **Rows of multiple items** — define wrap behavior (e.g. a 5-across filter row wraps to 2 rows under ~480px).
- **Grids** — define column counts per breakpoint (e.g. 2 cols mobile, 3 tablet, 4 desktop).
- **Tables / wide data** — define horizontal scroll, column hiding, or a card layout on narrow screens.
- **Side-by-side / split panels** — define stacking order when the viewport narrows.
- **Long horizontal control bars** — define wrapping or overflow behavior.

Do not assume mobile-first. Design for the target surface established in discovery (which may be desktop-primary, mobile-primary, or both), and only reason about breakpoints where elements genuinely reflow. State the reflow behavior concretely, not as a generic "it's responsive."
