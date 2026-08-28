---
name: "detect-design-substrate"
description: "Detect a project's UI stack and design substrate (Storybook, component library plus tokens, raw CSS, or nothing) and report it before any design work. Use at the start of every ui-architect task, or when the user asks what design system a project uses or wants a minimal design foundation created."
license: "MIT"
metadata:
  author: "Dean Clegg"
  version: "1.0.0"
---

# Detect Design Substrate

## Overview
Every design or review task starts here. This skill inspects the project to answer two questions — what technology stack is this, and what design substrate is already in place — then reports both back to the user before any design happens. It never guesses silently and never hardcodes component or token names; it discovers them per project. When no design system exists, it offers to create a minimal one matched to the stack rather than over-scaffolding.

## Prerequisites Checklist
- [ ] Read access to the project's source tree and config files
- [ ] The user has asked to design, review, or set up a screen (this skill runs first regardless)

## Step-by-Step Guide

### 1. Detect the stack
Identify the framework and styling technology from config and source files. Look for:

| Signal | Likely stack |
|--------|-------------|
| `package.json` with `react` + `vite` | React + Vite |
| `package.json` with `next` | Next.js |
| `package.json` with `vue` / `nuxt` | Vue / Nuxt |
| `pubspec.yaml` | Flutter |
| `angular.json` | Angular |
| `*.html` + `*.css`, no framework | Plain HTML/CSS |
| `tailwind.config.*` or `@import "tailwindcss"` | Tailwind (note alongside framework) |

Record the framework, the language (TS/JS/Dart/etc.), and the styling approach.

### 2. Detect the design substrate
Classify what design system is present, in this priority order:

1. **Storybook** — a `.storybook/` directory or `*.stories.*` files. Strongest substrate.
2. **Component library + tokens** — a components directory (e.g. `components/ui/`, shadcn, a Flutter widgets folder) and/or a theme/token file (CSS custom properties, a `theme.dart`, a Tailwind theme, design tokens JSON).
3. **Raw CSS / ad-hoc styles** — stylesheets with hardcoded values, no shared token layer.
4. **Nothing** — no discernible shared design layer.

Discover the actual names in use (component export names, token/variable names, theme class names). Do not assume `Button` or `--primary` exist.

### 3. Report to the user (always)
State the findings explicitly and concisely before doing anything else. Example:

> Stack: React + Vite + Tailwind. Substrate: Storybook plus a `cs2-strat-book` CSS-variable theme and a `components/ui/` library. I'll design from those.

If the substrate is a component library or raw CSS, name the key building blocks found so the user can confirm.

### 4. Handle the "nothing found" case
If no design system is found, do not silently scaffold one. Offer a choice:

- **(a) Create a minimal design foundation matched to the stack** — proportional and reversible. Examples:
  - Flutter → a `theme.dart` (or `ThemeData` extension) with color/spacing/text tokens.
  - Plain CSS site → a `theme.css` (custom properties) plus a small `components.css` or components file.
  - React without a library → a tokens file plus a couple of primitive components.
  - **Never** introduce Storybook, a build pipeline, or a large component catalog unless one already exists.
- **(b) Design ad-hoc for now** — proceed without a shared system, keeping the screen self-consistent.

Confirm the file structure with the user before building the minimal foundation.

### 5. Hand off
Once the substrate is known and reported (or created), hand control to `design-new-screen` or `review-screen` with the discovered vocabulary (component names, token names, theme classes) so those skills compose from real building blocks.

## Common Workflows

### Workflow: Existing design system
**Goal:** Lock onto the right substrate.
Detect → report ("found Storybook + tokens, using those") → hand off. No creation step.

### Workflow: Greenfield project
**Goal:** Establish just enough foundation without over-building.
Detect → report ("no design system found") → offer minimal-vs-ad-hoc → confirm structure → create minimal foundation matched to stack (or proceed ad-hoc) → hand off.

## Troubleshooting

### Issue: Multiple substrates present (e.g. Storybook AND raw CSS)
**Solution:** Prefer the strongest (Storybook > component library > raw CSS). Report the choice and note the drift so `review-screen` can flag the raw CSS later.

### Issue: Detection is ambiguous
**Solution:** Report what was found and ask the user to confirm the substrate rather than guessing.

## Best Practices
- Always report detection results before designing — never guess silently.
- Never hardcode component or token names; discover them per project.
- Keep any created design foundation minimal and proportional to the stack.
- Match created file types to the stack (`.dart` for Flutter, `.css` for CSS sites).
- Treat "build a design system" as a conscious, confirmed decision, not a side effect.
