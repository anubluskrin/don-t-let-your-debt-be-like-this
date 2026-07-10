# Stack-it

Stack-it is a browser-based 3D block-stacking game built with Three.js for rendering and Cannon.js for real-time physics simulation. Players stack blocks on top of each other with precise timing; any overhanging portion of a misaligned block is sliced off and falls away under realistic physics, while the aligned portion becomes the base for the next block.

##

Stack-it recreates the core mechanic popularized by mobile stacking games, implemented from scratch in vanilla JavaScript. Each block moves back and forth along an axis, and the player must trigger a drop (via click, tap, or the space bar) at the moment it aligns with the block below. Any overhang beyond the aligned area is computed geometrically, split into a separate physics body, and released into the Cannon.js physics world, where gravity and collision cause it to fall away naturally. The camera follows the stack upward as it grows, and the game ends once a block misses the stack entirely.

The project also includes a built-in autopilot mode that plays the game automatically with configurable imprecision, useful both as an idle demo and as a reference for the game's timing and alignment logic.

## Features

- Real-time 3D rendering using Three.js with an orthographic camera
- Physics-based gameplay powered by Cannon.js, including gravity and rigid-body collisions
- Precise overhang detection: misaligned block portions are split and dropped independently
- Dynamic camera tracking that follows the stack height as the game progresses
- Score tracking displayed on screen, incrementing with each successfully placed block
- Autopilot mode with randomized precision, useful for demos or automated testing of game logic
- Multiple input methods: mouse click, touch tap, and keyboard (space bar)
- Game reset via keyboard (R key) after a miss
- Responsive canvas that adjusts to window resizing

## Tech Stack

| Category | Technology |
|---|---|
| 3D Rendering | Three.js (r134) |
| Physics Engine | Cannon.js (v0.6.2) |
| Language | Vanilla JavaScript |
| Markup & Styling | HTML5, CSS3 |

Both Three.js and Cannon.js are loaded via CDN, so no build tools or package managers are required.

## Project Structure

```
Stack-it/
├── index.html      # Page markup and script/library includes
├── style.css        # UI styling (overlays, score display, instructions)
├── main.js           # Game logic: rendering, physics, input handling, scoring
└── README.md
```

## How It Works

1. On load, the scene is initialized with a foundation block and a first moving layer, along with ambient and directional lighting.
2. Each new layer moves continuously along the x or z axis (alternating per layer).
3. When the player triggers a drop, the moving block's position is compared against the block beneath it to determine the overlapping region.
4. The overlapping region becomes the new solid layer; any non-overlapping portion is converted into a separate mesh and physics body that falls away under gravity.
5. If there is no overlap at all, the game ends and the results screen is displayed.
6. The camera height is gradually increased to keep the top of the stack in view as it grows.

## Getting Started

No build process or dependencies are required.

1. Clone or download this repository.
2. Open `index.html` directly in a browser, or serve it via any static file server.

## Usage

- Click, tap, or press the space bar to start the game from the instructions screen.
- Click, tap, or press the space bar again to drop each block when it aligns with the stack below.
- Try to reach the blue-colored blocks for a visual milestone.
- After a miss, press `R` to reset the game.

## Customization

- **Box size and height**: adjust `originalBoxSize` and `boxHeight` at the top of `main.js`.
- **Movement speed**: adjust the `speed` value used when translating each layer.
- **Autopilot precision**: adjust the range in `setRobotPrecision()` to make the autopilot more or less accurate.
- **Camera type**: an alternative perspective camera setup is included as a commented block in `init()` for experimentation.

## License

This project is free to use for learning and personal or commercial projects.
