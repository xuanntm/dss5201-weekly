# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Environment Setup

```shell
cd src
python3.12 -m venv venv-dss5201
source venv-dss5201/bin/activate
pip install -r requirements.txt
```

## Running Notebooks

Execute a notebook in-place (runs all cells and saves output). Must use the venv's Python directly — the system `jupyter` binary uses a different Python and will fail:
```shell
cd src
venv-dss5201/bin/python -m nbconvert --execute --inplace [filename].ipynb
```

A `data/` symlink exists inside `src/` pointing to `../data/` so notebooks can resolve `data/` paths correctly when executed from `src/`.

## Code Style Rules

- Every code cell must include detailed inline comments explaining the **why**, not just the what.
- Each major code block must be preceded by a markdown cell explaining the goal of that section.
- Prefer `pandas`, `matplotlib`, and `seaborn` for data tasks unless `plotnine` is specifically required.

## Architecture

- `src/` — All Jupyter notebooks (`weekNN_lecture.ipynb`) and their rendered HTML exports.
- `data/` — Raw datasets (CSV and Excel). This directory is gitignored and not version-controlled.

Notebooks follow a weekly lecture structure. Each notebook is self-contained and loads its datasets from `../data/` relative to `src/`.
