# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Academic multiagent traffic simulation of a real-world Y-shaped intersection (Intersection 03 — "Av. Fernando García Roel / Ahuehuetes / Nogales" in Monterrey). The project models vehicle flow and traffic light control using agent-based simulation.

## Development Environment

### Setup

```bash
# Activate virtual environment
source venv/bin/activate

# Install dependencies (not yet in requirements.txt — install manually)
pip install agentpy numpy scipy matplotlib seaborn pandas networkx
```

### Running Notebooks

```bash
# Launch Jupyter
jupyter notebook notebooks/
```

There is no build, lint, or test command infrastructure yet. All code lives in Jupyter notebooks.

## Architecture

### Primary Code: Jupyter Notebooks

All simulation logic is in `notebooks/`. There is no production code in `src/` yet.

- **`Tarea_Cruce_Basico_CORREGIDO.ipynb`** — Basic intersection model without traffic lights. Models 4 access points (W, E, NW, NE) with real survey geometry, cubic spline road paths, capsule polygon collision detection, and Poisson vehicle arrivals.

- **`Cruce_Semafórico_Version_1.ipynb`** — Adds traffic signal control (v1). Key classes:
  - `StatsCollector`: Tracks throughput, queue lengths, wait times, travel times, and green-time efficiency per phase.
  - `TrafficLightController` (`ap.Agent`): 4-phase signal controller with configurable green/yellow/all-red timing (min_green=10, max_green=50, yellow=3, all_red=1 steps per default).
  - Vehicle state machine: spawn → approach → wait_light → exit.

### Simulation Parameters (PARAMS dict in notebooks)

- 600 simulation steps
- Poisson arrival rates: 0.07–0.20 vehicles/step per direction
- Free-flow velocity: 7.0 units/step; headway: 8.0 units
- Intersection geometry: length=80, width=3.5, stop distance=15.0 units

### Data

`data/raw/` contains empirical traffic counts for Intersection 03 across three time periods (morning, midday, afternoon) in Excel format — used for model validation.

## Git Workflow

Per `CONTRIBUTING.md`:
- Branch naming: `feature/`, `bugfix/`, `docs/`, `refactor/`, `test/` prefixes
- Commit message format: `feat:`, `fix:`, `docs:`, `style:`, `refactor:`, `test:`, `chore:`
- `main` is protected — all changes go through PRs
- Team members each have their own branches; this session is on branch `alan`

## Language

All code comments, variable names in domain context, and documentation are in Spanish. Maintain Spanish in new code and docs.
