# Stellar Cartographer

A self-contained 3D space exploration game built with HTML5 and [Three.js](https://threejs.org/). Chart a procedurally generated Milky Way, target star systems, and hyperspace-jump into their local systems — all from a single `index.html` file with no build step.

## Play it

Open `index.html` in any modern browser, or serve the repo (e.g. with GitHub Pages) and visit it directly.

- **Drag** to orbit the galaxy, **scroll / pinch** to zoom, **right-drag** (or shift-drag) to pan, or use the on-screen +/−/reset controls.
- **Click a star** to target it and open its survey panel: name, spectral class, distance from Sol, and resource potential.
- **Initiate Hyperspace Jump** to warp into that system's local view — a central star with procedurally generated orbiting planets — then **Return to Galactic Map** to head back out.

## Galaxy generation

The galaxy is built from a logarithmic spiral, `R = A · e^(B·θ)`, with a Gaussian profile scattering stars across each arm's width and the disk's thickness (Z axis):

| Arm | Angle offset | Color | Star density |
|---|---|---|---|
| Perseus Arm | 0.0 rad | `#a1c4fd` | 0.8 |
| Scutum-Centaurus Arm | 3.14 rad | `#ffd1ff` | 0.8 |
| Sagittarius Arm | 1.57 rad | `#c2fed9` | 0.5 |
| Orion Cygnus Spur (Sol's home) | 0.8 rad | `#fff176` | 0.3 |

Galactic radius: 50,000 ly · Core radius: 10,000 ly · Disk thickness: 3,000 ly.

Everything — the dust field, the curated clickable star systems, and each local system's planets — is generated at load time from a seeded PRNG, so the layout is stable across reloads.

## Deployment

Deployed on [Vercel](https://vercel.com/) as a zero-config static site. The project is connected to this repository's `main` branch, so every push here triggers an automatic redeploy.
