# Maze Runner Pro

A fun maze game to play during vibe coding wait times.

## Access
https://mjamiv.github.io/Maze2/

## How to Play

Navigate through procedurally generated mazes, collect gems, avoid hazards, and reach the goal before time runs out!

### Controls

| Key | Action |
|-----|--------|
| Arrow Keys / WASD | Move |
| Space | Destroy adjacent hazard |
| E | Reveal map (limited uses) |
| P / Esc | Pause game |

### Game Elements

- **Goal** - Reach the green flag to complete the level
- **Gems** - Collect for +10 points (combo multiplier for quick collection)
- **Speed Boost** - Temporarily increases movement speed
- **Time Bonus** - Adds extra seconds to the clock
- **Hazards** - Avoid or destroy them with Space

### Difficulty Levels

- **Easy** - 90 seconds, more paths, fewer hazards
- **Medium** - 60 seconds, balanced gameplay
- **Hard** - 45 seconds, fewer paths, more hazards

## Features

- Procedurally generated mazes that are always solvable
- Game Boy-style boot screen with credits on every launch
- First-time tutorial with guided training steps
- Multiple character choices
- Enemies with patrol AI, fog of war, shield/magnet/freeze powerups
- Combo system for consecutive gem collection
- Background music with mute toggle
- Procedural sound effects via Web Audio API
- Mobile touch controls (D-pad swipe + A/B buttons)
- Local high score tracking
- Progressive difficulty across levels (Easy/Medium/Hard)

## Running the Game

Simply open `index.html` in a modern web browser. No build step or server required.

## Files

- `index.html` - Complete game (HTML, CSS, JavaScript)
- `playdate.mp3` - Background music
