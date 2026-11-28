# Alessio Gatto — Interactive 3D CV (`about_me`)

[![Live Demo](https://img.shields.io/badge/Live%20Demo-GitHub%20Pages-00e5ff?style=for-the-badge)](https://alessiogatto.github.io/about_me/)
[![Three.js](https://img.shields.io/badge/Three.js-r187-ff2a85?style=for-the-badge)](https://threejs.org/)
[![Single File](https://img.shields.io/badge/Architecture-Single%20HTML-ffd32a?style=for-the-badge)](./index.html)
[![Version](https://img.shields.io/badge/Version-1.0-00ff9d?style=for-the-badge)](./index.html)

A playable, single-file **3D Neon Tokyo Expressway driving experience** built with Three.js WebGL that turns my curriculum vitae into an interactive nighttime circuit. Prefer a classic document view? Open the built-in **📄 FULL CV** modal at any time.

> **Play live:** https://alessiogatto.github.io/about_me/

---

## Highlights

- **Rosso Corsa Italian Tricolore Supercar**: Sculpted cockpit, **Verde · Bianco · Rosso** racing stripes, Giallo Modena calipers & fender shields, triple Tricolore exhaust jets, and an illuminated **`I · ALESSIO`** rear EU plate.
- **74m Helical 360° Vertical Loop**: Seamless $C^2$ clothoid entry and exit built with a 3,600-sample parallel-transport frame lookup table, boosted entrance chevrons, and gimbal-lock-free upside-down chase camera tracking.
- **Classic Nitro Speed Rush**: Activating Nitro (`Shift` / `🔥`) engages an 8-tap WebGL linear-HDR radial zoom motion blur pass (keeping the car sharp in the center while streaking neon signs and skyscrapers outward), crimson 3D taillight light-trail ribbons, lengthened exhaust jets, and dynamic FOV pull-back.
- **Speedbreaker Milestone Cutscenes**: Spotting each of the 6 chronological CV billboards on Lap 1 smoothly dilates world time into bullet-time (`0.025×`) with a 3D Bezier crane sweep, a minimal bottom continue pill, and Web Audio Speedbreaker swells—returning cleanly along a Bezier arc with zero velocity hitch.
- **Click-to-Inspect 3D CV Megaboards & Guided Tour**: Click any 3D roadside billboard (or press `F` / `◀ PREV` / `NEXT ▶` / `1–6`) to hide HUD bars and zoom full-frame onto 2K CanvasTextures, then press `Space` (`▶ CLICK SPACEBAR TO CONTINUE`) or click the bottom pill (or `F`) to resume driving, toggle **▶ GUIDED TOUR** for hands-free cruising, or open **📄 FULL CV** for the complete document and Core Technical Arsenal.
- **Cross-Device Ready**: Adaptive Super Retina DPR rendering (`2.0×–2.5×` on phones, `AUTO` / `HIGH` / `LITE` presets), two-thumb split mobile/iPad landscape HUD with a unified bar-free focused panel pill & swipe navigation, horizon-verified gyroscope steering & tilt-back braking, `es-module-shims` import-map polyfill, and an HTML CV fallback if WebGL is unavailable.

---

## Career & Education Milestones (6 Stages)

| Stage | Timeline | Role / Degree | Highlight |
| :--- | :--- | :--- | :--- |
| **01** | Jul 2016 | **Liceo Classico "Giacomo Leopardi"** | Classical Studies Diploma · Recanati, Italy |
| **02** | Oct 2016 – Feb 2020 | **B.Sc. Computing & Automation Engineering (UNIVPM)** | `102/110` · Synthetic optical holography imaging software thesis |
| **03** | May 2021 – Jul 2021 | **GrottiniLab S.r.l. — Deep Learning Intern** | TensorFlow retail CNN on AWS SageMaker · `30,000+` labeled images |
| **04** | Mar 2020 – Oct 2021 | **M.Sc. Computing & Automation Engineering (UNIVPM)** | `110/110 Cum Laude` · Deep learning product recognition thesis |
| **05** | Sep 2021 – Nov 2021 | **GrottiniLab S.r.l. — Deep Learning Engineer** | Rewrote Docker Shelf Management backend (`~10×` speedup) & `~50k` dataset |
| **06** | Jun 2022 – Present | **Texas Instruments Deutschland GmbH — Application Developer** | Automated SAP customs declarations for Frankfurt PDC (multi-million-dollar savings) & B2B systems |

---

## Controls

### Desktop (Keyboard & Mouse)

| Input | Action |
| :--- | :--- |
| `W` / `S` or `↑` / `↓` | Accelerate / ABS Brake & Reverse |
| `A` / `D` or `←` / `→` | Steer & Drift (builds Nitro charge) |
| `Shift` | Fire **Nitro** (`radial blur + taillight trails`) |
| `Space` | Jump & 360° Backflip / Barrel Roll (`Space + A/D`) · Close open panel (`CLICK SPACEBAR TO CONTINUE`) |
| Click 3D Panel / Pill (or `F`) | Zoom onto 3D panel / Press `Space` or click bottom pill (or `F`) to close |
| `1` – `6` / `◀` `▶` | Warp to milestone stage `1–6` / step panels |
| `G` / `C` / `M` / `P` | Guided Tour / Camera POV / Audio Mute / Pause & FX Preset |
| `R` | Restart circuit |

### Mobile & iPad (Landscape)

- **Gyroscope Mode (`🧭 START WITH GYROSCOPE`)**: Auto-accelerates while steering via horizon tilt left/right; tilt upright to brake or tap **🛑**.
- **Touch Controls Mode (`👆 START WITH TOUCH CONTROLS`)**: Two-thumb layout with steering (`◀` / `▶` + `🎥` POV) on the left and `🛑` Brake, `▲` Gas, `🔥` Nitro, and `🚀` Flip on the right, plus swipeable bar-free 3D panel inspection.

---

## Technical Architecture

Everything lives self-contained inside [`index.html`](./index.html) with zero build tools required:

- **Procedural Spline & Mesh Pipeline**: 18-point closed Catmull-Rom circuit with `3600` arc-length divisions, $C^2$ smoothed banking, adaptive highway tessellation, and track-conforming loop booster chevrons.
- **Draw-Call Optimization**: Static buildings, crowns, spires, beacons, neon ribs, launch ramps, Nitro canisters, sky rings, skill orbs, flying traffic spinners, and Tricolore sparks batched via `THREE.InstancedMesh` and frozen static matrices (`matrixAutoUpdate = false`).
- **Async Paint-Yielded Preloader**: `requestAnimationFrame` GPU `scaleX` progress bar with offscreen GPU pipeline pre-warming (`prewarmGPUPipelines`) into both the Nitro HDR render target and main framebuffer across yielded frame checkpoints before fading out.
- **Zero-Asset Procedural Audio**: Web Audio API synthesizer (`SoundEngine`) for V8/V10 engine pitch, Nitro ignition, Speedbreaker sweeps, stunt jumps, and stage chimes.

---

## Run Locally

Because [`index.html`](./index.html) uses ES module imports (`importmap`), serve the folder over HTTP:

```bash
python3 -m http.server 8128
```

Then open **http://localhost:8128/index.html** in your browser.

### Deployment

Pushing to `main` (or `master`) automatically deploys `index.html` to **GitHub Pages** via [`.github/workflows/pages.yml`](./.github/workflows/pages.yml).

---

## Repository Contents

- [`index.html`](./index.html) — Complete interactive 3D CV application (HTML, CSS, Three.js scene, WebGL shaders, Web Audio synth, and Full CV modal)
- [`.github/workflows/pages.yml`](./.github/workflows/pages.yml) — GitHub Actions workflow for GitHub Pages deployment
- [`README.md`](./README.md) — Project documentation

---

## Contact

- **Location**: Freising (Munich), Germany
- **Email**: [alessiogatto@live.it](mailto:alessiogatto@live.it)
- **GitHub / GitLab / LinkedIn**: `@alessiogatto`
