# 3D---Landmark-81

An interactive, luxury 3D WebGL / Three.js narrative experience exploring **Landmark 81** (Ho Chi Minh City, Vietnam) and the subterranean office level, **"The Floor Below"**.

**Live Production:** [https://landmark-81.vercel.app](https://landmark-81.vercel.app)

---

## Highlights & Features

- **Dual-World Experience:**
  - **The Tower (Exterior):** 461-meter dusk reconstruction of Landmark 81 with procedural day/dusk atmospheric scattering, volumetric fog, dynamic bloom, and orbit exploration.
  - **The Floor Below (Interior):** Atmospheric office complex with dynamic corridor pathfinding, interactive swinging exit doors with red neon illumination, and ambient dust motes.
- **Narrative 3-Stop Scroll Engine:**
  - **Exterior:** Overview $\leftrightarrow$ `01 Central Plaza` $\leftrightarrow$ `02 Sky Lobby` $\leftrightarrow$ `03 Riverside Gate`.
  - **Interior:** `01 The Reception Desk` $\leftrightarrow$ `02 The Exit Door` $\leftrightarrow$ `03 The Long Corridor`.
  - Step-by-step scroll traversal with bi-directional momentum, clean threshold stopping, and zero deadlocks.
- **Mobile & Touch-Optimized:**
  - Vertical finger swipe drives continuous corridor walking.
  - Horizontal drag enables 360° first-person view look.
  - Virtual analog joystick for free-roam interior traversal.
  - Interactive on-screen navigation chevrons (`←` / `→`) and clickable floor ticks for one-tap travel.
- **Cinematic Audio & Lighting:**
  - Procedural soundscapes with Web Audio API synthesizers (exterior wind, fluorescent room tone, rhythmic footsteps, door latches, and hotel elevator chimes).
  - Volumetric doorway spotlight casting through the swinging double fire doors.
  - Dynamic proximity-based EXIT sign hum.
- **Express Elevator Loop:**
  - An interactive brass elevator call station at the end of the east corridor allows you to call the lift (`[E]` key or click) and seamlessly ascend back to the Saigon sky deck.
- **Clean SPA Routing:**
  - Clean HTML5 History URLs (no `#` hash): `/exterior`, `/entrance/1..3`, `/floor/1..3`.
- **Extreme Asset Optimization:**
  - Interior GLB re-encoded with WebP textures: **86.8 MB $\rightarrow$ 6.5 MB** (~92% reduction).
  - Landmark tower GLB optimized: **1.57 MB $\rightarrow$ 932 KB**.

---

## Quick Start (Run Locally)

Because the project loads 3D `.glb` models and uses ES modules, it must be served over an HTTP server.

### Option 1: Python 3 (Recommended, zero install)
```bash
python3 -m http.server 8124
```
Then open [http://localhost:8124](http://localhost:8124) in your browser.

### Option 2: Node.js (npx serve or http-server)
```bash
npx serve . -l 8124
# or
npx http-server . -p 8124
```

---

## Controls & Navigation

### Desktop (Mouse & Keyboard)
| Action | Exterior (Saigon Tower) | Interior (The Floor Below) |
| :--- | :--- | :--- |
| **Mouse Wheel / Trackpad** | Scroll through the 3 entrances | Step-by-step corridor walk |
| **Left Click + Drag** | Orbit around the 461m tower | Look around in first-person (360°) |
| **W, A, S, D / Arrow keys** | — | Free-roam walking |
| **Shift** | — | Sprint / run |
| **1, 2, 3** | Snap to Entrance 1, 2, or 3 | Walk to Threshold 1, 2, or 3 |
| **E** | — | Call express lift (at end of corridor) |
| **Enter** | Enter through selected entrance | — |
| **Double Click** | Reset wide shot view | — |
| **Pill Buttons / Ticks** | Toggle Sound, About, Reset | Click ticks `01`, `02`, `03` to walk |

### Mobile & Touch Devices
- **Swipe Up / Down:** Walks forward and backward through the floor corridors.
- **Drag Left / Right:** Turns camera head to look around the room.
- **On-Screen Joystick:** Located at bottom-left for free movement.
- **HUD Navigation Bar:** Tap `←` or `→` arrows or tap floor ticks `01`, `02`, `03` for instant guided travel.

---

## URL Routes

Every location is deep-linkable and updates seamlessly without page reloads:

| Route | Description |
| :--- | :--- |
| `/exterior` | Wide overview shot of Landmark 81 |
| `/entrance/1` | Entrance 01 — Central Plaza |
| `/entrance/2` | Entrance 02 — Sky Lobby |
| `/entrance/3` | Entrance 03 — Riverside Gate |
| `/floor/1` | Threshold 01 — The Reception Desk |
| `/floor/2` | Threshold 02 — The Exit Door (Swinging doors) |
| `/floor/3` | Threshold 03 — The Long Corridor & Express Lift |

---

## Project Structure

```
landmark-81/
├── index.html            # Complete single-page application (Three.js r160, CSS, shaders, UI)
├── vercel.json           # Vercel SPA routing rewrites & caching headers
├── assets/
│   ├── landmark/
│   │   └── source/
│   │       └── Landmark 81.glb   # 932 KB tower mesh
│   └── backrooms/
│       └── source/
│           └── 514401d.glb       # 6.5 MB compressed WebP interior model
├── .gitignore
├── .vercelignore
└── README.md
```

---

## Deployment (Vercel)

The project includes pre-configured [vercel.json](file:///Users/saif-dc/Dcastalia/Node%20JS%20Projects/landmark-81/vercel.json) with SPA rewrites for `/entrance/*` and `/floor/*`.

To deploy:
```bash
# Install Vercel CLI (if needed)
npm i -g vercel

# Deploy to production
vercel --prod --yes
```

---

## License

Concept 3D architectural & experiential showcase. Models and assets belong to their respective creators.
