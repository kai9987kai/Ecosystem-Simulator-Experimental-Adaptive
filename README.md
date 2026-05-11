# Advanced Ecosystem Simulator – Adaptive AI Evolution Lab

A browser-based artificial life sandbox where autonomous agents learn, survive, mutate, reproduce, and compete inside a dynamic ecosystem. The project combines real-time canvas simulation, TensorFlow.js neural decision-making, evolutionary mutation, environmental pressure, live telemetry, and interactive inspection tools in a single standalone HTML file.

This version keeps the original simulator controls and expands them into a more complete experimental research playground for artificial ecosystems, emergent behaviour, and adaptive agent evolution.

---

## Overview

**Advanced Ecosystem Simulator – Adaptive AI Evolution Lab** simulates a living 2D world containing herbivores, carnivores, food sources, environmental threats, changing weather, seasons, and neural-network-driven agents.

Each agent has:

- Energy, age, role, generation, and fitness
- A small TensorFlow.js brain
- A mutable genome controlling speed, sense, aggression, curiosity, metabolism, fertility, and resilience
- Behaviour that responds to food, threats, nearby agents, weather, crowding, and reproduction pressure
- Inheritable neural weights that mutate when agents reproduce

The goal is not to hard-code perfect behaviour, but to create an environment where interesting patterns can emerge from simple AI decisions, ecological pressure, and evolutionary rules.

---

## Key Features

### Adaptive AI Agents

- TensorFlow.js-powered agent brains
- Herbivore and carnivore roles
- Food seeking, threat avoidance, wandering, predation, and mate-seeking behaviour
- Neural outputs converted into movement and intent
- Brain mutation during reproduction
- Fallback-safe model creation and disposal
- Backend switching between WebGL and CPU

### Evolution System

- Genome inheritance with mutation
- Configurable mutation rate
- Configurable mutation power
- Reproduction threshold control
- Generation tracking
- Fitness scoring
- Diversity metric based on genome variation
- Population cap to prevent runaway browser load
- Meta-evolution mode that refreshes weak populations when average energy collapses

### Ecosystem Simulation

- Food spawning and consumption
- Threat entities that chase agents
- Carnivore predation on herbivores
- Agent energy decay and death
- Weather states: sunny, rain, storm, drought, and fog
- Seasonal cycle: spring, summer, autumn, and winter
- Temperature changes
- Day/night visual overlay
- Dynamic food growth affected by weather and season

### Visual Layers

- Main canvas simulation
- Optional vision-radius display
- Optional movement trails
- Optional heatmap layer
- Optional labels
- Minimap
- Day/night lighting overlay
- Weather visuals
- AI-art inspired decorative panel
- Legend for entity types

### Dashboard and Telemetry

- Live population metrics
- Herbivore and carnivore counts
- Average energy
- Best fitness
- Genetic diversity
- Current weather, season, temperature, and time of day
- Food and threat counts
- FPS display
- TensorFlow tensor count
- Browser memory reporting when available
- Chart.js population chart
- Event log for simulation milestones

### Interaction Tools

- Click agents to inspect them
- Agent inspector panel with role, energy, age, generation, fitness, and genome values
- Pause/resume simulation
- Step one frame while paused
- Reset simulation
- Randomize seed
- Save/load simulation through `localStorage`
- Export CSV of agent data
- Export JSON world snapshot
- Emergency memory cleanup
- Quality toggle for high-DPI rendering

---

## Controls

| Control | Purpose |
|---|---|
| Agent Count | Sets the initial number of agents |
| Threat Level | Controls how many threats exist in the world |
| Food Spawn Rate | Controls how much food appears over time |
| Backend | Switches TensorFlow.js between WebGL and CPU |
| Agent Speed | Adjusts base movement speed |
| Reproduction Threshold | Energy required for agents to reproduce |
| Meta-Evolution | Enables/disables automatic brain refresh for weak populations |
| Canvas BG Color | Changes the simulation background colour |
| Mutation Rate | Chance of genome/brain mutation during reproduction |
| Mutation Power | Strength of mutations |
| Max Agents | Population limit for performance safety |
| Simulation Speed | Runs the world faster or slower |
| Preset | Applies predefined ecosystem configurations |

---

## Visual Toggles

| Toggle | Description |
|---|---|
| Vision | Shows agent sensing radius |
| Trails | Shows movement trails behind agents |
| Heatmap | Shows population/food density style overlays |
| Labels | Shows labels near agents |
| Chart | Shows or hides the live Chart.js telemetry chart |
| Event Log | Shows or hides simulation events |
| AI Art | Shows or hides the decorative ecosystem artwork |
| Quality | Switches between high-quality device-pixel-ratio rendering and lighter rendering |

---

## Keyboard Shortcuts

| Key | Action |
|---|---|
| `Space` | Pause or resume simulation |
| `.` | Step once while paused |
| `R` | Reset simulation |
| `S` | Save simulation to localStorage |
| `L` | Load saved simulation |
| `H` | Toggle heatmap |
| `V` | Toggle vision display |

---

## Entity Types

### Herbivores

Herbivores search for food, avoid threats, reproduce when energy is high enough, and mutate their genome and brain weights across generations.

### Carnivores

Carnivores can hunt herbivores, gain energy through predation, and evolve their own movement and sensing strategies.

### Food

Food appears throughout the world and gives energy to herbivores. Food spawning is influenced by ecosystem settings and environmental conditions.

### Threats

Threats chase nearby agents and penalize or kill them through collisions. The number of threats scales with the selected threat level.

---

## How the AI Works

Each agent owns a lightweight TensorFlow.js model. The model receives a normalized state vector containing information such as:

- Direction and distance to a target
- Direction and distance to the nearest threat
- Direction to a potential mate
- Current energy level
- Local crowding
- Time of day
- Weather and role information

The model outputs movement decisions and an intent signal. These outputs are combined with genome traits and environmental modifiers to create behaviour.

During reproduction, the child receives:

- A mutated copy of the parent genome
- A mutated copy of the parent neural weights
- A new generation value
- Half of the parent's energy investment

This makes the simulation closer to an artificial-life experiment than a basic animation.

---

## Meta-Evolution

When enabled, meta-evolution monitors average population energy. If the ecosystem begins collapsing and average energy falls too low, the simulator selectively refreshes a portion of weak agent brains.

This acts like an experimental recovery mechanism, helping the ecosystem continue producing behaviour instead of permanently dying out too quickly.

---

## Performance Features

The simulator includes multiple performance safeguards:

- Spatial indexing for faster neighbour lookups
- Population cap
- Batched agent processing
- Optional visual layers
- Quality toggle
- TensorFlow.js tensor monitoring
- Manual memory cleanup button
- Agent brain disposal during reset/load
- Reduced canvas pixel ratio option

For best performance, use the WebGL backend when available.

---

## Save, Load, and Export

### Save

Saves the current simulation state to browser `localStorage`, including:

- Agents
- Food
- Threats
- Settings
- Environment state
- Generation/frame data
- Agent genomes and neural weights

### Load

Restores the most recent saved simulation from localStorage.

### Export CSV

Exports a table of agent data for analysis in spreadsheet tools.

### Export JSON

Exports a full ecosystem snapshot for debugging, sharing, or future import experiments.

---

## Running the Project

Because the simulator is a standalone HTML file, it can be opened directly in a modern browser.

### Option 1: Open Directly

1. Download or clone the project.
2. Open the HTML file in Chrome, Edge, Firefox, or another modern browser.
3. Start experimenting with the controls.

### Option 2: Run with a Local Server

Some browsers handle local files more strictly. A local server is recommended for the most reliable experience.

```bash
python -m http.server 8000
```

Then open:

```text
http://localhost:8000
```

---

## Recommended Browser

Chrome or Edge is recommended because they generally provide strong support for:

- Canvas rendering
- TensorFlow.js WebGL backend
- `performance.memory` reporting
- High-DPI canvas rendering
- Fast JavaScript execution

Firefox should also work, but some memory metrics may not be available.

---

## File Structure

A minimal version of the project can be as simple as:

```text
advanced-ecosystem-simulator/
├── index.html
└── README.md
```

The simulator currently keeps HTML, CSS, and JavaScript together for easy portability.

---

## Dependencies

Loaded from CDN:

- [TensorFlow.js](https://www.tensorflow.org/js)
- [Chart.js](https://www.chartjs.org/)

No build step is required.

---

## Customization Ideas

You can extend the simulator by adding:

- More species types
- Poison food or medicinal food
- Terrain zones such as water, forest, desert, and mountains
- Lineage tree viewer
- Agent memory or recurrent neural networks
- Reinforcement learning reward charts
- Importable/exportable genome presets
- Web Worker simulation loop
- Multiplayer observation mode
- More advanced predator/prey balancing
- Save slots instead of a single save
- Replay system for ecosystem history
- Procedural map generation

---

## Research and Experiment Ideas

Try experimenting with:

- High mutation rate vs. low mutation rate
- High food rate vs. drought-heavy worlds
- Carnivore-heavy vs. herbivore-heavy ecosystems
- Different reproduction thresholds
- Disabling meta-evolution to observe natural collapse
- Reducing max agents to study small-population drift
- Increasing threat level to test survival pressure
- Comparing WebGL and CPU backend performance

---

## Known Limitations

- This is an experimental browser simulation, not a scientific-grade ecological model.
- TensorFlow.js models are intentionally small for real-time browser performance.
- Agent learning is evolutionary/mutational rather than full supervised or reinforcement training.
- Long sessions with very high populations may still increase memory usage.
- Browser support for detailed memory metrics varies.
- The AI-art panel is a decorative embedded SVG placeholder, not a live image-generation API integration.

---

## Troubleshooting

### The simulation feels slow

Try lowering:

- Agent count
- Max agents
- Food spawn rate
- Threat level

Also disable:

- Trails
- Heatmap
- Vision display
- Labels
- Chart
- High-quality rendering

### TensorFlow backend is not working

Use the backend selector and switch between WebGL and CPU. WebGL is usually faster, but CPU can be more stable on older devices.

### Browser memory increases over time

Use **Emergency Memory Cleanup** or reset the simulation. The simulator disposes agent brains during reset/load, but very long sessions with lots of neural mutations can still stress the browser.

### Save data will not load

The save format may change between versions. Clear browser localStorage or create a fresh save.

---

## Suggested GitHub Description

> A standalone browser-based artificial life simulator with TensorFlow.js neural agents, evolutionary mutation, predator-prey dynamics, weather, seasons, live telemetry, save/load, and interactive ecosystem inspection.

---

## Suggested Topics

```text
artificial-life
ecosystem-simulator
tensorflow-js
evolutionary-algorithms
agent-based-simulation
canvas
chartjs
neural-networks
predator-prey
browser-game
simulation
ai-agents
```

---

## License

Choose a license that matches how you want others to use the project. MIT is a good option for open-source browser experiments.

Example:

```text
MIT License
```

---

## Credits

Built as an experimental AI ecosystem simulator using browser-native technologies, Canvas, TensorFlow.js, and Chart.js.

