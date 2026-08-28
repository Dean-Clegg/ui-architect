# Text Sketch House Style

How to present each design direction as a text sketch so the user can react to structure and flow cheaply, before any code. Three directions by default.

## Anatomy of a direction
Each of the three directions is presented as a labeled block containing, in order:

1. **Title + one-line intent** — e.g. "Direction A — Single-focus roller: one action, zero clutter."
2. **Box/ASCII layout sketch** — the structure and hierarchy (see conventions below).
3. **Theming note (words)** — how it uses the project's tokens/components: what's primary-colored, what's muted, surfaces, emphasis. Reference discovered tokens, not invented ones.
4. **Wording note** — proposed titles, button labels, key microcopy (see microcopy.md).
5. **Responsive note — only if the layout reflows** — concrete reflow behavior. Omit entirely for atomic layouts.
6. **Pros / cons** — short bullets.
7. **Principle(s)** — the named heuristics it leans on (from principles.md / patterns.md).

## Box-drawing conventions
Use simple, consistent ASCII so it renders anywhere:

- Containers/cards: box characters or dashes/pipes.
- Emphasis / primary action: mark with `[[ ... ]]` or note "PRIMARY".
- Muted/secondary: mark with `( ... )` or note "muted".
- Repeated items: show 2-3 then `...`.
- Annotate hierarchy with side notes using `<-`.

### Example sketch
```
+------------------------------------------+
|  Mirage                          (back)  |   <- title dominant, back muted
+------------------------------------------+
|  [ Search strats...              ]       |   <- search input
|  ( All ) ( T ) ( CT )                    |   <- side filter chips
+------------------------------------------+
|  +------------------------------------+  |
|  | T  execute  A          [[ open ]]  |  |   <- card: badges + primary
|  | A Execute                          |  |
|  | Fast A take with smokes...  (muted)|  |
|  +------------------------------------+  |
|  | ... more cards ...                 |  |
+------------------------------------------+
|      [Strats]   Lineups   Random         |   <- bottom nav, active bold
+------------------------------------------+
```

## Making the three distinct
Vary the structural model between directions (see patterns.md), not just the paint. A strong set might be:
- A — single-focus / one dominant action
- B — dense scannable list
- C — split or grouped layout

If the screen genuinely supports only two distinct models, present two and say why. The user can request more.

## Tone of the write-up
- Concise. The sketch carries the layout; prose carries the reasoning.
- Every direction ends with the principle(s) it applies, so the choice is informed and the user absorbs the "why."
- Never include code in this phase. Sketches are cheap and discardable; code comes only after the user picks.
