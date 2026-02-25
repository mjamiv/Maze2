# Maze Runner Pro

Retro maze action built in a single HTML file.

## Play

[https://mjamiv.github.io/Maze2/](https://mjamiv.github.io/Maze2/)

## Theme

- Full "GameyBoy" device shell and LCD screen styling
- Classic 4-tone green Game Boy palette (`#0f380f`, `#306230`, `#8bac0f`, `#9bbc0f`)
- Pixel-art entity logos rendered directly on canvas
- Boot animation, scanline effects, and retro UI text styling

### Main Entity Logos

- `@` Player (adventurer/avatar)
- `*` Gem (collectible star)
- `X` Hazard (trap/cross)
- `M` Enemy (monster)

These are rendered as multi-row mini logos (not single letters) using green shade bands inspired by ANSI 256 colors `22/28/70`.

## How to Play

Navigate procedurally generated mazes, collect gems, avoid hazards/enemies, and reach the flag before time runs out.

### Controls

| Key | Action |
|-----|--------|
| Arrow Keys / WASD | Move |
| Space | Attack (destroy adjacent hazard/enemy) |
| E | Reveal map (limited uses) |
| P / Esc | Pause |

Mobile:
- D-pad swipe: Move
- B button: Attack
- A button: Reveal
- Select: Pause

## Core Gameplay

- **Goal (`F`)**: Reach the flag to clear the level
- **Gems (`*`)**: +10 base points, combo multiplier for fast chains
- **Hazards (`X`)**: Damage timer or consume shield
- **Enemies (`M`)**: Patrol and drain time on collision
- **Powerups**: Speed, extra time, shield, map reveal, magnet, freeze
- **Fog of war** with reveal pulse and minimap support

## Difficulty

- **Easy**: 90s start time, more open mazes, fewer hazards/enemies
- **Medium**: 60s start time, balanced default
- **Hard**: 45s start time, tighter mazes and more danger

## Features

- Procedural maze generation with solvability guarantees
- Guided tutorial for first-time players
- Responsive desktop + mobile controls
- Local leaderboard and persistent stats
- Optional Firebase-backed leaderboard reads
- Procedural SFX via Web Audio API + looping background track
- Background music loudness control via Web Audio pre-gain + compressor + limiter

## Security Deployment Note

`frame-ancestors` cannot be enforced from a `<meta http-equiv="Content-Security-Policy">`.
To block framing/clickjacking in production, send CSP as an HTTP response header.

If your static host supports header files, use the repo `_headers` template.
If you deploy on GitHub Pages directly, serve through a proxy/CDN that can set headers.

## Run Locally

Open `index.html` in a modern browser. No build step required.

## Files

- `index.html`: Entire app (markup, styles, logic)
- `vendor/tailwindcss-browser-4.2.0.js`: Local Tailwind browser runtime (no CDN dependency)
- `playdate.mp3`: Background music
- `README.md`: Player-facing overview
- `CLAUDE.md`: Maintainer/assistant architecture notes
