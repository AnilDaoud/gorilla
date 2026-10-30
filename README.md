# GORILLA.BAS - Canvas Edition

A faithful recreation of the classic QBasic GORILLA.BAS (1991) as a single self-contained HTML file using the Canvas API.

**Play it now: [anil.diwi.org/gorilla.html](https://anil.diwi.org/gorilla.html)**

## Features

- 640x350 EGA resolution with pixelated scaling
- 1-player (vs computer) or 2-player mode
- Destructible buildings with permanent holes
- Wind mechanic affecting banana trajectory
- Pixel-accurate building collision (bounding-box for gorillas, see below), sampled every 2px along the banana's path so fast throws can't tunnel through walls
- Computer opponent that searches for a shot and gets more accurate as it misses
- PC speaker-style sound effects (Web Audio API square waves) with a mute toggle
- Feedback on invalid angle/velocity input
- Built-in 5x7 bitmap font
- Sun reacts when the banana flies near
- Victory dance animation
- Mobile support with on-screen number pad (auto-detected on touch devices)
- Zero dependencies, single HTML file

## How to Play

1. Open `gorilla.html` in any modern browser
2. Press any key except `M` to start (`M` toggles mute instead), then configure players, names and points-to-win (1-99), confirming each field with Enter. Typing in a field replaces its default value
3. Enter an angle (0-90) and velocity (1-200) to throw a banana at your opponent. Out-of-range values are rejected with a message
4. First to reach the target score wins; at game over press `Y` to play again or `N` to return to the title screen
5. Press Escape at any time to return to the title screen

## Controls

- **Number keys / period**: Type angle and velocity values
- **Enter**: Confirm input
- **Backspace**: Delete input
- **M**: Toggle sound mute (not available while typing in the setup screen; the speaker button below the game works everywhere)
- **Y / N**: Play again / back to title at game over
- **Escape**: Quit to title screen

Keyboard input is ignored while the computer is taking its turn.

## Differences from the Original

The core game mechanics (trajectory physics, building generation, wind, scoring) are faithful to the 1991 QBasic original, but collision detection differs slightly:

| | Original GORILLA.BAS | Canvas Edition |
|---|---|---|
| **Hit detection** | Pixel-color sampling (`POINT()`) — banana must overlap an actual gorilla-colored pixel | Buildings: pixel-color sampling of a scene buffer. Gorillas: bounding-box — 26x28 rectangle around the gorilla |
| **Probe points** | 2 points (leading edge + diagonal offset) | 5 points for buildings, 1 point for gorilla, checked every 2px along the banana's path |
| **Near-miss tolerance** | Zero — pixel-perfect, no splash damage | More forgiving (full rectangle including empty corners) |
| **Building explosion radius** | 7 pixels | 25 pixels |
| **Gorilla explosion radius** | 48 pixels | 40 pixels |
| **Floor destruction** | Gorilla floats (no gravity) | Same — gorilla floats |

Both versions have no splash damage: a near-miss that destroys the building next to a gorilla does not count as a hit. Both versions allow gorillas to float in mid-air if the building beneath them is destroyed — there is no falling/gravity code in the original.

## Browser Requirements

Any modern browser with Canvas API, Web Audio API, and CSS Grid support (Chrome 58+, Firefox 52+, Safari 11+, Edge 16+). Older Safari versions use the prefixed `webkitAudioContext`, and if audio is unavailable the game still runs silently. On touch devices an on-screen number pad (with a mute button) is shown automatically.

## About

The original GORILLA.BAS shipped with MS-DOS 5.0 and QBasic in 1991. This Canvas rewrite preserves the original game mechanics — trajectory physics, building generation patterns, wind effects, and scoring rules — while running natively in the browser with no dependencies.
