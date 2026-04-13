# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Development Workflow

This is a pure HTML5 Canvas + vanilla JavaScript project with no build step or dependencies.

- **Open the game:** Open `snake-game.html` in a web browser
- **Live reload:** Use any local server (e.g., `npx serve .` or VS Code Live Server) for auto-refresh during development

## Git Workflow

Always commit changes with descriptive messages and push to GitHub:

```bash
git add .
git commit -m "Description of changes"
git push origin master
```

## Architecture

**Single-file structure:** All game code (HTML, CSS, JavaScript) is in `snake-game.html`.

**Game Loop:** Uses `setInterval(gameStep, delay)` where delay decreases as score increases (speeds up every 50 points, minimum 50ms).

**Grid System:** 20x20 pixel cells on a 600x600 canvas = 30x30 grid (`tileCount`).

**State Management:** Global variables tracked in memory:
- `snake[]` - Array of {x, y} segments, index 0 is head
- `food` - {x, y} position
- `dx, dy` - Direction vector (-1, 0, or 1)
- `score, isPaused, isGameOver`

**Input Handling:** `keydown` event listener prevents default on arrow keys/space to avoid page scrolling.

**Collision Detection:**
- Wall: head.x/y < 0 or >= tileCount
- Self: head position matches any segment position

**Visual Effects:** Uses `ctx.shadowBlur` and `ctx.shadowColor` for neon glow effects on snake head and food.
