---
name: "detect-design-substrate"
description: "Detect a project's UI stack and design substrate (Storybook, component library plus tokens, raw CSS, or nothing) and report it in one line before any design work. Runs first on every ui-architect task, gated behind a quick confirmation so it never scans unprompted. Use at the start of any design or review task, or when the user asks what design system a project uses or wants a minimal design foundation created."
license: "MIT"
metadata:
  author: "Dean Clegg"
  version: "1.1.0"
---

# Detect Design Substrate

## Overview
The entry point for every task. It gates behind a quick confirmation, then inspects the project to answer two questions — what stack is this, and what design substrate exists — and reports both in one line before anything else happens. It never guesses silently and never hardcodes component or token names; it discovers them per project. When no design system exists, it offers a minimal one matched to the stack rather than over-scaffolding.

Follow the shared [working-agreement.md](../design-new-screen/references/working-agreement.md) for the activation gate, conversation flow, and scope rules. Keep spoken output terse.

## Prerequisites Checklist
- [ ] Read access to the project's source and config files
- [ ] The user has agreed to begin (activation gate passed)

## Step-by-Step Guide

### 1. Activation gate
On activation, announce (including the power version, currently **v1.2.0**) and wait — do not scan yet:
> "ui-architect v1.2.0 activated. Want me to start by gathering the project's theme/styling context?"
Proceed only on yes.

### 2. Detect the stack
From config/source, identify framework, language, and styling approach:

| Signal | Stack |
|--------|-------|
| `package.json` + `react` + `vite` | React + Vite |
| `package.json` + `next` | Next.js |
| `package.json` + `vue` / `nuxt` | Vue / Nuxt |
| `pubspec.yaml` | Flutter |
| `angular.json` | Angular |
| `*.html` + `*.css`, no framework | Plain HTML/CSS |
| `tailwind.config.*` / `@import "tailwindcss"` | Tailwind (note alongside framework) |
| Kendo / MUI / Chakra / etc. in deps | Note the component library |

### 3. Detect the substrate (priority order)
1. **Storybook** — `.storybook/` or `*.stories.*`.
2. **Component library + tokens** — a components dir and/or a theme/token file (CSS vars, `theme.dart`, Tailwind theme, tokens JSON).
3. **Raw CSS / ad-hoc styles** — stylesheets with hardcoded values, no shared tokens.
4. **Nothing.**

Discover the real names in use (components, tokens, theme classes). Never assume `Button` or `--primary` exists.

### 4. Report in one line
State it simply, then move on:
> "Found: Storybook + a `cs2-strat-book` CSS-variable theme and a `components/ui/` library. I'll build from those."

If a component library or raw CSS, name the key building blocks so the user can confirm.

### 5. If nothing found
Offer, don't scaffold silently:
- **(a) Minimal foundation matched to the stack** — proportional, reversible. Flutter → `theme.dart`; CSS site → `theme.css` + small components file; React without a lib → tokens + a couple of primitives. Never add Storybook or a big catalog unless one exists.
- **(b) Design ad-hoc for now.**
Confirm file structure before creating anything.

### 6. Ask scope, then hand off
Ask what to work on (whole project / screen / section / component / something new), steering away from whole-project work per the working agreement. Then hand off to `design-new-screen` or `review-screen` with the discovered vocabulary.

## Troubleshooting

### Issue: Multiple substrates (e.g. Storybook AND raw CSS)
**Solution:** Prefer the strongest (Storybook > component library > raw CSS). Report the choice; note the drift for `review-screen` to flag later.

### Issue: Detection ambiguous
**Solution:** Report what was found and ask the user to confirm rather than guessing.

## Best Practices
- Gate before scanning; report before designing. Never guess silently.
- One-line reports. Depth stays in the reference files, not the chat.
- Never hardcode component or token names.
- Any created foundation is minimal and matched to the stack.
