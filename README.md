# Airport Luggage Robot Planning

Airport Luggage Robot Planning is a Python notebook project that simulates a multi-robot baggage transport workflow inside an airport. The system coordinates three robots across a grid-based airport map while comparing baseline Q-learning, PSO-optimized Q-learning, and GWO-based swarm-mode Q-learning policies.

The project focuses on reinforcement learning for discrete robot navigation, route coordination, dynamic obstacle avoidance, and policy comparison across multiple training strategies.

## Features

- **Three-robot baggage pipeline:** Robot 1 moves luggage from check-in to sorting, Robot 2 moves it from sorting to the assigned gate, and Robot 3 moves it from the gate to baggage claim.
- **Airport grid environment:** Includes check-in, sorting, gates, baggage claim, waiting areas, a coffee shop, walls, and restricted zones.
- **Dynamic obstacles:** Simulates moving people or blocked paths that robots must avoid during navigation.
- **Baseline Q-learning:** Trains destination-specific Q-tables using a simple reward structure.
- **PSO-optimized Q-learning:** Uses Particle Swarm Optimization to tune Q-learning hyperparameters before retraining improved policies.
- **GWO swarm mode:** Uses Grey Wolf Optimizer logic to tune a swarm-mode learning setup.
- **Offline diagnostics:** Compares routes with success/failure status, step counts, revisits, and path length.
- **Pretrained policies included:** The repository includes the trained Q-tables needed to run the notebook without retraining everything from scratch.

## Project Structure

```text
airport_luggage_robot_planning.ipynb   Final notebook implementation
airport_q_baseline.pkl                 Baseline Q-learning Q-tables
airport_q_tables.pkl                   PSO-optimized Q-learning Q-tables
airport_swarm_q_tables.pkl             GWO/swarm-mode Q-learning Q-tables
assets/                                Runtime image assets used by the Pygame simulation
requirements.txt                       Python dependencies
```

## Learning Approaches

| Mode | Method | Purpose |
| --- | --- | --- |
| Baseline | Q-learning | Learns simple destination policies using fixed hyperparameters. |
| Optimized | Q-learning + PSO | Uses Particle Swarm Optimization to tune alpha, gamma, epsilon decay, and minimum epsilon. |
| Swarm | Q-learning + GWO | Uses Grey Wolf Optimizer-inspired tuning for the swarm-mode policy setup. |

## Algorithm Flow

![Airport luggage robot planning algorithm flow](docs/assets/algorithm-flow.svg)

## Reported Results

The submitted project report compared the three modes over an approximately 100-second simulation window:

| Mode | Completed Cycles | Total Robot Steps |
| --- | ---: | ---: |
| Baseline Q-learning | 8 | 1273 |
| PSO-optimized Q-learning | 9 | 1280 |
| GWO swarm mode | 9 | 1259 |

The baseline policy was functional, while the optimized and swarm modes completed more cycles in the reported run. The swarm mode achieved the same number of cycles as the optimized mode with fewer total robot steps.

## Setup

Create and activate a virtual environment:

```bash
python -m venv .venv
.\.venv\Scripts\activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Open the notebook:

```bash
jupyter notebook airport_luggage_robot_planning.ipynb
```

Run the GUI/environment cell first. The notebook expects the `assets/` folder and the three Q-table `.pkl` files to remain in the repository root next to the notebook.

## Implementation Notes

- The Pygame simulation has three selectable modes: Baseline, Optimized, and Swarm.
- The notebook includes training cells, optimization cells, offline policy tests, and diagnostics.
- The included `.pkl` files are trained Q-table artifacts used by the simulation modes.

## Concepts Demonstrated

- Reinforcement learning
- Q-learning
- Multi-agent robot coordination
- Discrete path planning
- Dynamic obstacle avoidance
- Hyperparameter optimization
- Particle Swarm Optimization
- Grey Wolf Optimizer
- Pygame simulation
