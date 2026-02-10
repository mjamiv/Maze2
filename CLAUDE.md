# Claude.md

This file provides context for AI assistants working on this project.

## Project Overview

Maze Runner Pro is a single-file HTML5 maze game. All game logic, styling, and markup are contained in `index.html` with no external dependencies except for Tailwind CSS (loaded via CDN).

## Architecture

### Single File Structure

The game is intentionally kept as a single HTML file for simplicity and portability:

- **HTML** (lines 1-141): Game UI structure including menu, game screen, overlays
- **CSS** (lines 8-23): Custom animations and styles (Tailwind handles the rest)
- **JavaScript** (lines 143-873): All game logic in a single script block

### Key Components

**State Object** (`state`): Central game state containing:
- Canvas and rendering context
- Maze data and dimensions
- Player position and animation
- Game entities (hazards, collectibles, powerups, particles)
- Game flow flags (started, paused, over)
- Score, level, timer, combo
- Audio context and music state

**Core Systems**:
- Boot screen with staggered credit animations (`startBootSequence()` / `endBootSequence()`)
- Maze generation using recursive backtracking algorithm
- Pathfinding validation to ensure solvability
- Tutorial system for first-time players (5 guided steps)
- Enemy patrol AI, fog of war, powerup system (shield, magnet, freeze)
- Particle system for visual effects
- Web Audio API for sound effects
- HTML5 Audio for background music

### Audio

- **Sound Effects**: Generated procedurally using Web Audio API oscillators
- **Background Music**: `playdate.mp3` loaded via HTML5 `<audio>` element with loop

## Development Notes

### Adding New Features

When adding features, keep everything in `index.html` to maintain the single-file approach. The code is organized into clearly labeled sections:
- `// ===== SECTION NAME =====`

### Browser Compatibility

- Uses standard Web APIs (Canvas, Web Audio, LocalStorage)
- Tailwind CSS loaded from CDN
- Mobile support via touch controls

### Testing

Open `index.html` directly in a browser. No build process required.

## Common Tasks

### Adding New Power-ups

1. Add power-up type in `generateMaze()` function
2. Handle collection in `movePlayer()` function
3. Add visual indicator if needed
4. Apply effect in game loop

### Modifying Difficulty

Adjust parameters in:
- `generateMaze()` - hazard count, extra paths
- `startGame()` - initial time
- `nextLevel()` - time reduction per level

### Adding Sound Effects

Use the `playTone(freq, duration, type, volume)` function or create a new helper similar to `playCollect()`, `playMove()`, etc.
