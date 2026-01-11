# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a collection of interactive visualizations built with vanilla HTML5, CSS3, and JavaScript. All visualizations are self-contained HTML files with no external dependencies or build process required.

## Running Visualizations

To view any visualization, simply open the HTML file in a browser:

```bash
open particle-galaxy.html
```

Or double-click the file in Finder/Explorer.

## Architecture

### Self-Contained HTML Files

Each visualization is a complete, standalone HTML file containing:
- Embedded CSS in `<style>` tags
- Embedded JavaScript in `<script>` tags
- No external dependencies or frameworks

This architecture enables:
- Zero-config deployment (upload anywhere)
- Easy sharing (single file contains everything)
- Browser-only execution (no build tools needed)

### Particle Galaxy Structure

The particle-galaxy.html visualization demonstrates the standard pattern:

**Core Components:**
- `Particle` class: Encapsulates particle state (position, velocity, color, radius) and behavior (draw, update, collision detection)
- `init()`: Initializes particle array with randomized properties
- `animate()`: Main render loop using `requestAnimationFrame` for smooth 60fps animation
- `connectParticles()`: Calculates distances between particles and draws connection lines

**Event System:**
- `mousemove`: Updates mouse position for interaction tracking
- `mouseout`: Clears mouse state when cursor leaves window
- `click`: Spawns explosion effects at cursor position
- `resize`: Reinitializes canvas dimensions and particles

**Canvas Pattern:**
All visualizations use HTML5 Canvas 2D context for rendering. The standard pattern is:
1. Clear/fade previous frame with semi-transparent overlay
2. Update particle positions and states
3. Draw particles and connections
4. Request next animation frame

## Adding New Visualizations

When creating new visualizations, follow these patterns:

**File Naming:** Use descriptive kebab-case names (e.g., `wave-simulator.html`, `3d-cube-rotation.html`)

**Color Schemes:** Use HSL for dynamic rainbow effects: `hsl(${hue}, 100%, 60%)` where hue varies 0-360

**Performance:** Keep particle counts reasonable (<500) and use distance checks to limit connection calculations

**Interaction:** Include visual feedback for mouse/touch interactions to enhance engagement

**Responsive:** Handle window resize events by reinitializing canvas dimensions
