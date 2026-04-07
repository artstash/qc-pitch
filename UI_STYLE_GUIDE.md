# Search Concierge UI Style Guide (Match Agent Workbench)

This guide captures the core visual language used in Agent Workbench so the Search Concierge chat page can look consistent with this project.

## 1) Design tokens

### Typography
- Primary font: `Inter, sans-serif`
- Weights used: `400, 500, 600, 700`
- Source pattern: Google Fonts import in global UI CSS

### Core colors
- App background: `#121212`
- Sidebar background: `#0b0b0b`
- Top bar / elevated panel background: `#1a1a1e`
- Primary border: `#2e2e2e`
- Secondary border/divider: `#1f1f23`, `#333`
- Primary text: `#ffffff`
- Secondary text: `#d1d1d6`, `#d1d5db`, `#e5e7eb`
- Muted text: `#9ca3af`, `#666`

### Brand accent
- Primary accent: `#8b5cf6`
- Accent alt (headers/highlights): `#a855f7`
- Accent metric: `#a78bfa`

### Semantic accents (pillars)
- Universe / lore: `#8b5cf6`
- Quality control: `#eab308`
- User acquisition: `#22c55e`

### Effects
- Card radius: `8px` or `12px` (larger panels use `16px`)
- Panel shadows:
  - subtle: `0 4px 12px rgba(0,0,0,0.1)`
  - medium: `0 4px 15px rgba(0,0,0,0.3)`
  - strong: `0 10px 25px rgba(0,0,0,0.5)`
- Transition timing: `0.2s` to `0.3s`

## 2) Layout language

- Dark-first app shell.
- Left navigation rail (around 260px equivalent width).
- Fixed top header bar with thin bottom border.
- Main content uses card sections with subtle borders and soft contrast fills.
- Avoid pure black cards against black background; use `#1a1a1e` or translucent dark fills.

## 3) Component patterns to mirror in chat UI

### Page shell
- Background: `#121212`
- Font: `Inter`
- Header row: `#1a1a1e` with `1px` bottom border `#2e2e2e`
- Optional radial gradient for login/hero states:
  - `radial-gradient(circle at top right, #1a1a2e, #121212)`

### Buttons
- Primary button:
  - background/border `#8b5cf6`
  - text `#ffffff`
- Secondary button:
  - transparent background
  - `1px solid #4b5563`
  - text `#e5e7eb`

### Cards and panels
- Default card:
  - background: `rgba(25, 25, 35, 0.5)` or `#1a1a1e`
  - border: `1px solid #333` (or `#2e2e2e`)
  - radius: `12px`
- Highlight/guidance box:
  - background: `rgba(139, 92, 246, 0.05)`
  - border: `1px solid rgba(139, 92, 246, 0.2)`
  - heading accent: `#a855f7`

### Status and tags
- Muted label: uppercase, letter spacing, `#666`
- Accent tag chip:
  - text: `#a855f7`
  - bg: `rgba(168, 85, 247, 0.15)`
  - radius: `4px`

### Chat affordance
- Floating chat action style (if used):
  - circle `60x60`
  - accent background `#a855f7`
  - shadow `0 4px 15px rgba(0,0,0,0.3)`

## 4) Suggested CSS token block

```css
:root {
  --aw-bg: #121212;
  --aw-bg-sidebar: #0b0b0b;
  --aw-bg-elevated: #1a1a1e;
  --aw-border: #2e2e2e;
  --aw-border-soft: #1f1f23;
  --aw-text: #ffffff;
  --aw-text-secondary: #d1d1d6;
  --aw-text-muted: #9ca3af;
  --aw-accent: #8b5cf6;
  --aw-accent-alt: #a855f7;
  --aw-accent-metric: #a78bfa;
  --aw-qc: #eab308;
  --aw-ua: #22c55e;
}
```

## 5) Chat page implementation checklist

1. Apply `Inter` globally and remove default font stack mismatches.
2. Use dark shell (`#121212`) + elevated chat containers (`#1a1a1e`).
3. Replace current primary CTA color with `#8b5cf6`.
4. Standardize borders to `#2e2e2e` and dividers to `#1f1f23`.
5. Use muted typography (`#9ca3af` / `#666`) for metadata and timestamps.
6. Use pillar semantic accents (`#8b5cf6`, `#eab308`, `#22c55e`) consistently for badges/states.
7. Keep corner radii in the 8/12/16px system.
8. Use subtle shadows only on key panels and floating actions.

## 6) Source of truth in this repo

- `web_app/app.py` (global app shell, sidebar, top bar, cards, buttons, timeline, semantic color usage)
- `web_app/auth.py` (login gradient, login card styling, accent treatment)

If UI token conflicts occur, follow this order:
1. `web_app/app.py` global styles
2. `web_app/auth.py` login/entry visual patterns
