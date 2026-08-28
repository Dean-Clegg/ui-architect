# Microcopy Principles

"Microcopy" is the text inside the UI — button labels, titles, placeholders, empty-state messages, errors, tooltips, help text. Good wording is a large, cheap UX win. When designing or reviewing a screen, propose better wording alongside layout, and suggest where a help icon or tooltip reduces confusion.

These are principles, not a fixed word list — the right vocabulary differs per project. Build a small per-project glossary during discovery (note the terms the project already uses) and stay consistent with it.

## Voice & tone
- Match the product's context. A glanceable, mid-task tool (used quickly, under pressure) wants terse, direct copy. A relaxed consumer app can be warmer.
- Be consistent in tone across the screen. Don't mix formal and playful.

## Action labels (buttons, links)
- Use verbs that state what happens: "Delete strat," "Save changes," "Roll" — not "OK," "Submit," "Click here."
- Keep them short. One or two words is ideal for primary actions.
- The label should match the user's goal, not the system's internal operation.

## Titles & headings
- Say what the screen/section is in plain terms. Prefer nouns the user recognizes.
- Keep them short and scannable; avoid redundant words.

## Placeholders & hints
- Placeholders show format or example, not the label ("Search lineups..." not "Type here").
- Don't use placeholder text as the only label for inputs (accessibility issue).

## Empty states
- Explain what belongs here and give the next action: "No lineups yet — pick a map to start."
- Never a bare "No data" or "Error: null."

## Errors & validation
- Be specific and human: what went wrong and how to fix it.
- Avoid codes and jargon in user-facing text; keep those in logs.

## Consistency & terminology
- Pick one term per concept and use it everywhere (e.g. always "strat," not sometimes "strategy").
- Match capitalization style consistently (sentence case is usually friendliest).
- Reuse the project's established vocabulary; record it in the per-project glossary.

## Help & guidance
- Suggest a help icon or tooltip where a term or control is non-obvious, rather than crowding the screen with explanation.
- Prefer inline clarity over help text when possible — the best microcopy needs no footnote.

## How to use this in a proposal
For each design direction, include a short "wording note" with the proposed title, primary action label, and any key messages (empty state, primary hint). In a review, flag specific weak strings and propose better ones with a one-line reason.
