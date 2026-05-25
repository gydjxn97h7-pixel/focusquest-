# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

FocusQuest is a single-file browser app (`index.html`) — no build step, no bundler, no dependencies. Open the file directly in a browser to run it.

```
open index.html
```

## Architecture

Everything lives in `index.html`: CSS in `<style>`, markup in `<body>`, logic in `<script>`. There is no separation of concerns across files by design.

**Screens** are `<div>` elements with class `scene`. Visibility is toggled by adding/removing the `active` class via `showScene(id)`. Currently only `#startScreen` exists; `#focusScreen` and `#endScreen` will be rebuilt later.

**Assets** sit alongside `index.html`:
- `Hintegrundbild.jpg` — full-viewport background image, applied to `body`
- `Boden_1Welt.png` — ground strip for the scroll animation (focus screen, not yet rebuilt)

## Design tokens

Defined as CSS custom properties on `:root`:

| Token | Value | Use |
|---|---|---|
| `--chalk` | `#f5f0e8` | Primary light text |
| `--gold` | `#c8a96e` | Accent, borders, ornaments |
| `--warm-ink` | `#2c1f10` | Dark text on light glass |
| `--glass-bg` | `rgba(245,240,232,0.26)` | Panel backgrounds |
| `--glass-edge` | `rgba(200,169,110,0.32)` | Panel borders |

## Typography

Two fonts loaded from Google Fonts:
- **Press Start 2P** — used only for the `h1.main-title` (FOCUSQUEST title)
- **Josefin Sans** (weights 100–400) — all other text

## Design language

- Glass panels: light, warm, airy — never dark. `backdrop-filter: blur(24-26px)` on all panels.
- Buttons: pill shape (`border-radius: 50px`), light chalk glass background, gold border, warm gold `box-shadow` glow on hover.
- No dark overlays, no navy, no cold colors anywhere.

## Product concept

Hub-System: the user has a central base (train, camper van, or house — not yet decided) that represents their progress. Focus time is the only currency — it builds the base and unlocks new worlds.

Core loop: Start focus → collect time → earn resources → upgrade hub or unlock worlds → start again.

## Worlds

- Sunlit Dunes (first world, pixel-art background already exists as Gemini_Generated_Image_tr0sj5tr0sj5tr0s.png)
- Planned: Fantasy, Solarpunk, Steampunk, Modern Minimalistic, Mountains, Floating Gardens, Rainglass House

## Focus screen (to be rebuilt)

- Three equal thirds: timer top, pixel-art world middle, buttons bottom
- Middle third: pixel-art image scrolls seamlessly left in a loop (two copies side by side, translateX -50%)
- Ground strip (Boden_1Welt.png) scrolls below the pixel-art at the same speed

## Technical debt

- Remove bg-world element from HTML (leftover, does nothing)
- Introduce state system when loot, XP, inventory or multiple worlds are added

## Workflow note

Anton has no coding knowledge. Always explain what to do step by step. Write complete code blocks, never partial snippets without context.
