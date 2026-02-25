# TODO

- [x] **Fix B/A button positioning** — The B and A action buttons are slightly conflicting with the game screen. Adjust `.action-btn` positioning/margins so they don't overlap or interfere with the canvas display. *(Fixed: added mt-3/mt-4 to push buttons down, reduced A button -mt-4 to -mt-3, added z-index to screen bezel, overflow:hidden on controls-area)*

## Session Leave-Behind (2026-02-21)

- [x] **Entity logo refresh** — Replaced in-game single-glyph rendering for player/gem/hazard/enemy with multi-row retro logo sprites and ANSI-inspired green shade bands.
- [x] **Character selection sync** — Updated menu character cards to use logo sprites and ensured selected character visuals now propagate to gameplay.
- [x] **Character differentiation fix** — Added per-character player logos (`W/F/R/G`) so avatar choices are visually distinct in both selection and in-game rendering.
- [x] **Bezel label alignment** — Reworked `DOT MATRIX WITH STEREO SOUND` styling/placement to sit cleanly within the bezel.
- [x] **Button look enhancement** — Improved tactile Game Boy-style button visuals with restrained gradients, texture overlays, and press-depth shadows.
- [x] **SELECT button reliability** — Removed duplicate pointer/click trigger path that could cause unstable pause toggling on touch/pointer devices.
- [x] **Leaderboard overwrite bug fix** — Stopped online load from replacing local scores; scoreboard now merges local + online entries with dedupe and sorted top-20 rendering.
- [x] **Maintenance guardrail** — Updated `CLAUDE.md` with a permanent rule and test step to prevent future local-score overwrite regressions.
