# GORILLA.BAS - Canvas Edition

A faithful recreation of the classic QBasic GORILLA.BAS (1991) as a single self-contained HTML file using the Canvas API.

**Play it now: [anil.diwi.org/gorilla.html](https://anil.diwi.org/gorilla.html)**

## Features

- 640x350 EGA resolution with pixelated scaling
- 1-player (vs computer) or 2-player mode
- Destructible buildings with permanent holes
- Wind mechanic affecting banana trajectory
- Pixel-accurate collision detection
- PC speaker-style sound effects (Web Audio API square waves)
- Built-in 5x7 bitmap font
- Sun reacts when the banana flies near
- Victory dance animation
- Zero dependencies, single HTML file

## How to Play

1. Open `gorilla.html` in any modern browser
2. Press any key to start, configure players and points-to-win
3. Enter an angle (0-90) and velocity (30-200) to throw a banana at your opponent
4. First to reach the target score wins
5. Press Escape at any time to return to the title screen

## Controls

- **Number keys / period**: Type angle and velocity values
- **Enter**: Confirm input
- **Backspace**: Delete input
- **Escape**: Quit to title screen

## About

The original GORILLA.BAS shipped with MS-DOS 5.0 and QBasic in 1991. This Canvas rewrite preserves the original game mechanics — trajectory physics, building generation patterns, wind effects, and scoring rules — while running natively in the browser with no dependencies.
