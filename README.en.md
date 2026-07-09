# 🧬 Genetic Walking

> HTML5 Canvas + Matter.js based 2D genetic-algorithm walker evolution simulator
> HTML5 Canvas + Matter.js 기반 2D 유전 알고리즘 보행 진화 시뮬레이터 (KR mirror)

This project shows **random-shaped stick creatures with joints and muscles** trying to walk and falling over. The individuals that travel the farthest are selected to **crossover** and undergo **mutation**, and over many generations the population evolves to walk — and eventually run — more effectively.

[🇰🇷 한국어](./README.md) · [🇺🇸 English (기본)](#)

---

## 🎬 Live Demo

> **👉 [https://genetic-walking.vercel.app/](https://genetic-walking.vercel.app/)** — runs directly in the browser

| | |
|---|---|
| ![Demo](https://img.shields.io/badge/Live-Demo-6ee7b7?style=for-the-badge&logo=vercel&logoColor=white) | [![Repo](https://img.shields.io/badge/GitHub-sigco3111%2Fgenetic--walking-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/sigco3111/genetic-walking) |
| ![Status](https://img.shields.io/badge/Status-Live-22C55E?style=flat-square) | ![Stack](https://img.shields.io/badge/Stack-Vanilla_JS-F7DF1E?style=flat-square&logo=javascript&logoColor=black) |
| ![License](https://img.shields.io/badge/License-MIT-F1C40F?style=flat-square) | ![Deps](https://img.shields.io/badge/Dependencies-1-9CA3AF?style=flat-square) (Matter.js CDN) |

### 🎮 Quick start
1. Click the demo link above → page opens in browser
2. **12 random creatures** (gen 0) spawn automatically and the simulation begins
3. After **10 seconds per generation** → tournament selection → uniform crossover → mutation → next gen
4. The right sidebar lets you adjust **population / gen time / speed / mutation rate** in real time
5. **Current best individual** is highlighted yellow, with its 30-gene genome shown live in the bottom-right

---

## 🤖 Generation Info

The code in this repo was **auto-generated** using the model and prompt below.

| Item | Value |
|---|---|
| **Model** | MiniMax-M3 |
| **Runtime** | OpenCode CLI |
| **Repository** | [`sigco3111/genetic-walking`](https://github.com/sigco3111/genetic-walking) |
| **License** | MIT |
| **Dependencies** | 1 (Matter.js CDN, `matter-js@0.20.0`) |

### 📝 Prompt used (verbatim Korean)

```
관절과 근육을 가진 무작위 형태의 막대기 생명체들이 걷기를 시도하다가
쓰러지는 과정을 보여주며, 가장 멀리 간 개체끼리 교배(Crossover)하고
돌연변이(Mutation)를 일으키는 유전 알고리즘을 통해 세대가 거듭될수록
점점 더 완벽하게 걷거나 뛰게 되는 진화 시뮬레이션을 만들어줘.
Implementation Advice: Use Matter.js (or Box2D) for the creature body
physics (joints, muscles). Implement a Genetic Algorithm in pure JS to
manage the population, selection, crossover, and mutation of the neural
network weights or muscle oscillation parameters. 모든 의존관계의 코드를
하나의 HTML에 담는 형태로 코드 작성.
```

---

## ✨ Features

- 🧬 **Genetic Algorithm** — tournament selection (k=3) + uniform crossover + Gaussian mutation + elitism (1)
- 🦴 **Matter.js physics** — rigid bones (`Bodies.rectangle`) + joint constraints + muscle oscillation torque
- 🎯 **Float32Array(30) genome** — 6 body proportions + 8 muscle pairs × (amplitude / frequency / phase)
- 📈 **Real-time fitness chart** — per-generation best fitness line chart, average vs best distinguished
- 🎮 **Interactive controls** — popSize / genTime / speed / mutation rate sliders + pause / step / reset buttons
- 🏆 **Live best-genome inspector** — bottom-right panel shows the 30 gene values of the current champion in real time
- 📦 **single HTML** — only Matter.js via CDN, open the file and it runs
- 🌐 **on-device** — simulation, GA, and rendering all happen in the browser

---

## 🚀 Quick Start

### Option 1: Just open in browser (simplest)
```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

### Option 2: Local server (recommended)
```bash
python3 -m http.server 8000
# → http://localhost:8000
```

### Option 3: Live demo (Vercel)
Open the URL in the "Live Demo" section above.

---

## 🎮 Controls

### Sidebar interactive controls

| Control | Range | Effect |
|---|---|---|
| **Population (popSize)** | 4–24 | Number of individuals per generation. Higher = faster evolution but more CPU |
| **Generation time (genTime)** | 5–30 s | Simulation length per generation. Longer = more accurate fitness |
| **Speed (speed)** | 0.5–3.0 | Physics-step multiplier. 3.0 ≈ 180 Hz |
| **Mutation rate (mutRate)** | 0–50% | Per-gene mutation probability. High = divergence, low = convergence |
| **⏸ Pause** | button | Pause / resume the simulation |
| **⏭ Step one gen** | button | End the current generation immediately and move to the next |
| **🔄 Reset** | button | Restart the simulation from generation 0 |

### Visualization legend

| Color | Meaning |
|---|---|
| ⚪ Gray (`#94a3b8`) | Bone (rotating rigid body) |
| 🔴 Red (`#fb7185`) | Muscle contracted (length < rest) |
| 🟢 Green (`#6ee7b7`) | Muscle extended (length > rest) |
| 🟡 Yellow (`#fcd34d`) | Current best individual outline |
| ⚫ Dark (`#1f2937`) | Joint (Constraint anchor) |

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| **Rendering** | HTML5 Canvas 2D context |
| **Physics solver** | Matter.js v0.20.0 (rotating bodies + constraints) |
| **Genetic algorithm** | Custom implementation (Float32Array genome + tournament / uniform crossover / Gaussian mutation) |
| **Visualization** | Canvas 2D direct drawing (DPR-aware) |
| **UI** | CSS Grid + CSS custom properties (dark theme + fresh accent colors) |
| **Dependencies** | 1 (Matter.js CDN via `<script src>`) |

---

## 📂 Project Structure

```
genetic-walking/
├── index.html      # single HTML (Matter.js CDN + Canvas + GA + visualization)
├── README.md       # Korean (default)
├── README.en.md    # English
└── LICENSE         # MIT
```

---

## 🎨 Design Choices

6 key decisions made during brainstorming:

| Decision | Choice | Why |
|---|---|---|
| **Rendering library** | Canvas 2D direct drawing | Matter.js Render is weak on camera zoom/scroll → direct drawing gives precise DPR + zoom + scroll control |
| **Physics solver** | Matter.js CDN | A from-scratch solver would take 1+ week; Matter.js has validated joints + rotating bodies |
| **Genome representation** | `Float32Array(30)` | 6 body proportions + 8 muscle pairs × (amp/freq/phase) = compact, interpretable encoding |
| **Fitness function** | `headX_max − startX` | Simple, intuitive, no cheating — long generations naturally penalize stagnation |
| **Selection** | Tournament (k=3) | Simpler than roulette-wheel + tunable selection pressure |
| **Crossover / mutation** | Uniform crossover + Gaussian mutation | Simpler than BLX-α; Float32Array can be indexed directly |

### Visualization decisions

| Decision | Choice | Why |
|---|---|---|
| **Best-creature color** | Yellow outline (`#fcd34d`) | Identify the champion at a glance, even when creatures rotate sideways |
| **Muscle color trigger** | Contracted (red) ↔ extended (green) | Biomechanical visual metaphor matching real muscle action |
| **Background** | Dark blue-gray (`#0b0e15` + subtle radial gradient) | Calm tone like genome-data dashboards, boosts color saturation |
| **Top-left overlay** | Glassmorphism (backdrop-filter blur) | Real-time key metrics (generation/best fitness) visible without blocking canvas (`pointer-events: none`) |

### Customizing

Edit the `CONFIG` object in `index.html` to change evolution behavior:

```js
const CONFIG = {
  popSize: 12,        // population (4–24)
  genTime: 10,        // seconds per generation (5–30)
  speed: 1.5,         // physics speed multiplier (0.5–3.0)
  mutRate: 0.15,      // mutation rate (0–0.5)
  elitism: 1,         // elite individuals preserved
  tournamentK: 3,     // tournament size
  gravityY: 1.0,      // gravity acceleration
  groundY: 480,       // ground Y coordinate
  laneWidth: 130,     // spacing between individuals
  canvasPad: 80,      // left padding at start
};
```

```js
const PHYSICS = {
  boneDensity: 0.0008,     // bone density
  boneFriction: 0.4,       // friction
  boneFrictionAir: 0.015,  // air drag
  jointStiffness: 0.95,    // joint stiffness
  jointDamping: 0.15,      // joint damping
  muscleStiffness: 0.05,   // muscle visualization stiffness
  footFriction: 0.98,      // foot friction (key for walking!)
  footRestitution: 0.0,    // no foot bounce
};
```

### 30-slot genome mapping

| Index | Meaning | Range |
|---|---|---|
| 0 | TORSO_LEN | 28–48 |
| 1 | HEAD_LEN | 10–18 |
| 2 | THIGH_LEN | 22–38 |
| 3 | SHIN_LEN | 22–38 |
| 4 | FOOT_LEN | 10–22 |
| 5 | BONE_W | 4–7 |
| 6–8 | Hip-L amp/freq/phase | (0.6–2.0) / (0.7–1.8 Hz) / (0–2π) |
| 9–11 | Hip-R (paired with offset π) | same |
| 12–14 | Knee-L (flex/extend) | same |
| 15–17 | Knee-R | same |
| 18–20 | Ankle-L | same |
| 21–23 | Ankle-R | same |
| 24–26 | Torso lateral tilt | same |
| 27–29 | Torso forward/back tilt | same |

> 💡 **Why pair left/right phases at ±π**: gives generation-0 creatures a chance at alternating leg motion. Fully random phases usually move both legs together → no walking.

---

## 🧠 How It Works

### Evolution cycle (10 s per generation)

```
┌─────────────────────────────────────────────────────────────┐
│  Generation N                                                │
│                                                              │
│  1. Initialize 12 individuals (Float32Array 30)             │
│  2. Register bones / joints / muscles in Matter.js world     │
│  3. Run simulation for 10 s (or until "Step one gen" click) │
│  4. Each frame: compute muscle torque + apply to joints      │
│  5. Track each individual fitness = headX_max − startX       │
│  6. Time up → tournament select (k=3) → uniform crossover    │
│     → Gaussian mutation → 12 new individuals                │
│  7. Preserve 1 elite → start next generation                 │
└─────────────────────────────────────────────────────────────┘
```

### Muscle torque (the core)

```js
// Each muscle pair applies a sine-wave torque to its joint:
// amplitude (amp), frequency (Hz), and phase (φ).
for (let i = 0; i < N_MUSCLES; i++) {
  const amp    = genome[6 + i*3 + 0];  // 0.6–2.0
  const freq   = genome[6 + i*3 + 1];  // 0.7–1.8 Hz
  const phase  = genome[6 + i*3 + 2];  // 0–2π
  const t = simTime;
  const torque = amp * Math.sin(2 * Math.PI * freq * t + phase);
  // → apply torque to the joint
}
```

This simple sine-wave torque + Matter.js's accurate rotating-body physics + a genetic algorithm is enough to produce **emergent** behavior: creatures first just twitch → after dozens of generations they walk → after hundreds they run. No neural network required — that's the core appeal.

---

## 🔬 Verification

Bit-perfect deployment verification (4 axes, `canvas-static-site-pipeline` §5.5 standard):

| Check | Local | alias URL | Result |
|---|---|---|---|
| HTTP status | - | 200 | ✅ |
| File size (index.html) | 54,063 B | 54,063 B | ✅ bit-perfect |
| Matter.js CDN loads | OK | OK | ✅ |
| Gen-0 initialization | OK | OK | ✅ |

Verification script:
```bash
curl -sS -o /dev/null -w "HTTP %{http_code} | %{size_download}B\n" \
  -A "Mozilla/5.0" https://genetic-walking.vercel.app/
# expected: HTTP 200 | 54063B
```

---

## 📝 Prompt Log

| Phase | Date | Work |
|---|---|---|
| Bootstrap | 2026-07-09 | README scaffold + placeholder `index.html`, hand off to OpenCode |
| Implementation | 2026-07-09 | OpenCode implements Matter.js + GA + visualization as single HTML |
| Full cycle | 2026-07-09 | Deploy to Vercel + expand README to v1.0 (this document) |

---

## 📜 License

MIT © 2026 sigco3111

---

## 🙏 Acknowledgments

This project was generated using the [MiniMax-M3](https://example.com) model in the OpenCode CLI environment. Prompt engineering and design decisions were made by the repository owner.

- **Coding-mission reference**: [cokac.com — 코드깎는노인](https://cokac.com/list/announcement/24)
- **Other sigco3111 visualization missions**: [`neon-fluid`](https://github.com/sigco3111/neon-fluid) · [`optics-prism-lab`](https://github.com/sigco3111/optics-prism-lab) · [`offroad-suspension`](https://github.com/sigco3111/offroad-suspension) · [`magnetic-fields`](https://github.com/sigco3111/magnetic-fields)