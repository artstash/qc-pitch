# Copilot Instructions — ArtStash QC Agent Pitch Deck

## Project overview

This repo is an **interactive pitch deck** (single-page HTML app) for "Project Gatekeeper" — ArtStash's AI-powered quality control agent for creative asset management. It visualizes the QC workflow, before/after comparisons, and a step-through UI mockup of the product experience.

There are no build tools, package managers, or test suites. The entire application lives in `index.html` with inline CSS, Tailwind, and vanilla JavaScript.

## Architecture

- **`index.html`** — the entire app: markup, styles, and scripts are all inline. There is no bundler or component framework.
- **`UI_STYLE_GUIDE.md`** — canonical design token reference (colors, typography, spacing, shadows). This is the visual source of truth; defer to it when choosing colors or component styles.
- **`Artstash Project Gatekeeper.md`** — product vision, user roles, and the 7-step QC loop narrative. Use it for domain context and copy accuracy.
- **`media/`** — `.webp` images used in the interactive mockup section (logo placement examples).

## Design system — "Agent Workbench" (`aw-*`)

The Tailwind config extends a custom `aw` color namespace. Always use these tokens instead of raw hex values:

| Token | Value | Use |
|---|---|---|
| `aw-bg` | `#121212` | Page background |
| `aw-bg-elevated` | `#1a1a1e` | Cards, panels, top bar |
| `aw-bg-sidebar` | `#0b0b0b` | Sidebar, secondary containers |
| `aw-border` | `#2e2e2e` | Primary borders |
| `aw-border-soft` | `#1f1f23` | Subtle dividers |
| `aw-accent` | `#8b5cf6` | Primary brand accent (purple) |
| `aw-accent-alt` | `#a855f7` | Hover/highlight accent |
| `aw-qc` | `#eab308` | Quality control pillar (yellow) |
| `aw-ua` | `#22c55e` | User acquisition pillar (green) |

Custom CSS classes (`aw-card`, `aw-btn-primary`, `aw-highlight-box`) are defined in the `<style>` block and follow `UI_STYLE_GUIDE.md` section 3. Use these over building one-off utility chains.

## Conventions

- **Dark-only**: There is no light theme. All backgrounds use the `aw-bg` / `aw-bg-elevated` / `aw-bg-sidebar` spectrum. Never use white or light backgrounds.
- **Font**: Inter (400/500/600/700) via Google Fonts CDN. No other fonts.
- **Border radius system**: `8px` (buttons, small elements) → `12px` (cards) → `16px` (large panels, `aw-card-large`).
- **Shadows**: Use the `aw-subtle` / `aw-medium` / `aw-strong` shadow tokens defined in the Tailwind config.
- **Transitions**: `0.2s`–`0.3s` timing. The codebase uses `cubic-bezier(0.4, 0, 0.2, 1)` for interactive node animations and `ease-out` for fade-ups.
- **Interactive sections** are toggled via vanilla JS functions (`setFlow()`, `setMockupStep()`, `selectNode()`) that show/hide elements and swap CSS classes — not framework state. Follow this pattern for new interactive content.
- **Semantic status colors**: Red (`#f43f5e`) = QC Failed, Emerald (`emerald-400/500`) = QC Passed, Blue = In Progress, Yellow = Needs Review. These map to the product's asset status model.
- **Inline everything**: Scripts and styles stay inside `index.html`. Do not extract to separate `.js` or `.css` files unless the file becomes unmanageable.
