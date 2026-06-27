# Galaxy Generator

> A generative 3D spiral galaxy you can sculpt in real time — built with Three.js particle systems. No AI, no backend, pure creative coding.

## Live Demo
https://nzjulien.github.io/galaxy-generator

## What it does

Generates a unique procedural spiral galaxy out of up to 200,000 particles,
using the classic branch-angle + spin-angle technique with power-curve
randomness for natural-looking density falloff toward the core.

## Controls
- **Stars** — particle count (5K – 200K)
- **Radius** — galaxy size
- **Spiral Arms** — number of branches (2–9)
- **Spin** — how tightly the arms twist
- **Randomness** — scatter amount per particle
- **Star Size** — point size
- **Core / Edge color** — gradient from center to rim
- 🎲 **Random Galaxy** — instantly generates a new galaxy with randomized parameters and palette
- 📸 **Save PNG** — exports the current view as an image
- ⏸ **Pause Spin** — freeze rotation for a clean screenshot

## Technique

Each star's position is computed from:
1. A random radius (power curve, denser near the core)
2. A branch angle (`2π * branchIndex / totalBranches`)
3. A spin angle proportional to radius (creates the spiral twist)
4. Randomized X/Y/Z jitter using a power-curve random sign, for that classic
   "wispy" galaxy-arm look rather than a uniform scatter

Colors are linearly interpolated between a core color and an edge color
based on each star's distance from center, then rendered with
`AdditiveBlending` for a natural glow where particles overlap.

## Stack
- Three.js r128 (`BufferGeometry`, `Points`, `PointsMaterial`, `OrbitControls`)
- Vanilla HTML/CSS/JS, zero build step
- Geometry and material are disposed and rebuilt on every parameter change
  to avoid GPU memory leaks

Made by NzJulien
