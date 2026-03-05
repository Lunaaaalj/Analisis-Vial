# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Traffic intersection analysis project (Analisis-Vial) modeling a specific signalized intersection (Intersección 03). The current focus is a multiagent simulation of vehicle movement through the intersection using the Mesa framework.

## Environment Setup

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt   # requirements.txt does not exist yet — install manually
```

Key installed packages (Python 3.14 venv):
- `mesa` — multiagent simulation framework
- `matplotlib`, `numpy`, `pandas`, `scipy` — data analysis and visualization
- `openpyxl` — reading Excel data files

## Running Notebooks

```bash
source venv/bin/activate
jupyter notebook
```

The main notebook is `notebooks/Angel_Luna.ipynb`. Planning documentation is in `notebooks/planificacion_multiagente.md`.

## Data

Raw traffic count data for Intersection 03 lives in `data/raw/` as Excel files:
- `Int. 03 mañana.xlsx` — morning counts
- `Int. 03 mediodia.xlsx` — midday counts
- `Int. 03 tarde.xlsx` — afternoon counts

A reference layout is at `docs/Croquis-03.pdf`. Raw data should never be modified.

## Architecture

The project follows a data science template structure:

- `data/raw/` — immutable source data (Excel traffic counts)
- `data/processed/` — cleaned/transformed data
- `notebooks/` — exploration and presentation (Jupyter notebooks)
- `src/` — reusable production-ready Python modules (currently empty)
- `models/` — trained model artifacts
- `reports/figures/` — generated visualizations
- `tests/` — unit and integration tests

The multiagent model (`notebooks/planificacion_multiagente.md`) defines:
- `Cruce` class — 2D grid representing the intersection, with marked entry/exit cells and intersection zone
- `Vehiculo` agents — attributes `pos`, `direction` (N/S/E/O), `state` (moving/static)
- Movement rule: one cell per tick; agents wait (`static`) when the target cell is occupied
- No traffic lights in the current phase

Stable code should be refactored from notebooks into `src/`.

## Git Workflow

- Never commit directly to `main`; all changes go through pull requests
- Create branches with prefixes: `feature/`, `bugfix/`, `docs/`, `refactor/`, `test/`
- Open a Draft PR immediately after the first push; mark Ready for review when complete
- Commit message format: `feat:`, `fix:`, `docs:`, `style:`, `refactor:`, `test:`, `chore:`
- Keep commits atomic; use squash-merge for feature branches with many small commits
