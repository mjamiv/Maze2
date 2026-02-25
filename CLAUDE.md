# CLAUDE.md

This file provides context for AI assistants and maintainers working on this project.

## Project Overview

Maze Runner Pro is a single-file browser game in `index.html` with a retro "GameyBoy" presentation:

- Device shell UI + LCD styling
- 4-tone green Game Boy palette
- Canvas-based maze gameplay with procedural generation
- Desktop and mobile control schemes

No build system is used.

## Runtime Dependencies

- Local Tailwind browser runtime (`vendor/tailwindcss-browser-4.2.0.js`)
- Google Fonts (`Press Start 2P`)
- Optional Firebase Realtime Database endpoint for leaderboard sync
- Local asset: `playdate.mp3`

## File Layout

- `index.html`: Entire application (HTML, CSS, JavaScript)
- `vendor/tailwindcss-browser-4.2.0.js`: Tailwind browser runtime bundle
- `playdate.mp3`: Background music loop
- `README.md`: Player-facing docs

`index.html` is large (4k+ lines). Use section markers (`// ===== ... =====`) as the main navigation anchors.

## Code Architecture (Inside `index.html`)

Major JavaScript sections are explicitly labeled:

- `INDUSTRY-GRADE MOBILE SETUP`
- `HAPTIC FEEDBACK`
- `SCREEN WAKE LOCK`
- `FONT LOADING & APP INITIALIZATION`
- `FIREBASE CONFIG`
- `GAME STATE`
- `DIFFICULTY CONFIG`
- `LEADERBOARD`
- `STATS`
- `AUDIO` and `BACKGROUND MUSIC`
- `MAZE GENERATION`
- `PARTICLES`
- `FOG OF WAR`
- `ENEMIES`
- `MOVEMENT`
- `TUTORIAL SYSTEM`
- `GAME FLOW`
- `RENDERING`
- `GAME LOOP`
- `INPUT`
- `SETUP`

## Theme and Rendering Rules

The game intentionally commits to retro visuals:

- Preserve the Game Boy palette and pixel feel.
- Entity visuals are logo-based mini pixel art, not plain glyphs.
- Main logos are defined in render constants:
  - `ENTITY_LOGOS.player` (`@` avatar style)
  - `ENTITY_LOGOS.gem` (`*` collectible style)
  - `ENTITY_LOGOS.hazard` (`X` trap style)
  - `ENTITY_LOGOS.enemy` (`M` monster style)
- `drawLogoTile()` renders these logos on the canvas tile grid.

When changing entity visuals, update the logo definitions and shared renderer instead of duplicating per-entity drawing logic.

## Security Header Rule

- Keep clickjacking protection in HTTP headers, not meta tags.
- `frame-ancestors` must be sent as a response header to be enforced.
- Runtime frame-busting JS is fallback only, not a header substitute.

## State Model

`state` is the single source of truth for:

- Maze geometry and canvas sizing
- Player movement/animation targets
- Hazards, collectibles, enemies, powerups, particles
- Difficulty, timer, scoring, combo
- Tutorial/progression and transitions
- Fog/minimap/reveal state
- Audio/music flags
- Leaderboard and persistent stats

## Gameplay Notes

- Maze generation guarantees a reachable goal.
- Difficulty is centralized in `DIFFICULTY`.
- Enemy movement cadence depends on difficulty interval.
- Attack can remove adjacent hazards/enemies.
- Tutorial and main game flows are separate entry paths.

## Leaderboard and Persistence

- Local leaderboard/stats use `localStorage`.
- Firebase URL is configured in `FIREBASE_DB_URL`.
- `ALLOW_UNVERIFIED_FIREBASE_WRITES` is intentionally `false` by default.
- Leaderboard display must never replace local scores with online-only data.
- When online data is available, merge `local + online`, dedupe, sort by score desc, then render top 20.
- In read-only online mode (`ONLINE R/O`), remote data is additive for display only; local entries remain visible.

Treat remote writes as untrusted unless server-validated.

## Editing Guidelines

- Keep the single-file architecture unless explicitly asked otherwise.
- Reuse existing section structure and helper functions.
- Prefer minimal, targeted patches over broad rewrites.
- Keep mobile behavior intact (touch input, viewport/safe-area handling, wake lock).
- Maintain retro tone in copy and UI labels.

## Manual Testing

Primary validation is manual in browser:

1. Open `index.html`
2. Verify boot/menu/game screens on desktop and mobile layout
3. Verify movement, collisions, tutorial flow, pause/resume, and audio toggles
4. Confirm entity logos (player/gem/hazard/enemy) render correctly at different tile sizes
5. Save a new local high score, open `SCORES`, and confirm it still appears after online leaderboard loading completes
