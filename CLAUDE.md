# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Environment Setup

```shell
python3.12 -m venv venv-dss5201
source venv-dss5201/bin/activate
pip install -r requirements.txt
```

## Running Notebooks

Execute a notebook in-place (runs all cells and saves output). Must use the venv's Python directly — the system `jupyter` binary uses a different Python and will fail:
```shell
cd src
../venv-dss5201/bin/python -m nbconvert --execute --inplace [filename].ipynb
```

Notebooks load datasets from `../data/` (the root `data/` folder) since they run from within `src/`.

## Code Style Rules

- Every code cell must include detailed inline comments explaining the **why**, not just the what.
- Each major code block must be preceded by a markdown cell explaining the goal of that section.
- Prefer `pandas`, `matplotlib`, and `seaborn` for data tasks unless `plotnine` is specifically required.

## Local AI Assistant (aider + Ollama)

Aider is installed in the venv and configured to use a local Ollama model. Start it from the project root:

```shell
source venv-dss5201/bin/activate
aider src/week10_lecture.ipynb   # work on a specific notebook
aider                            # open with no files, add them interactively
```

Config is in `.aider.conf.yml`. Model: `qwen2.5-coder:7b` (~5GB, runs comfortably on 18GB).
To switch model: edit the `model:` line in `.aider.conf.yml`.

Ollama resource caps (set via launchctl, survive restarts):
- `OLLAMA_MAX_LOADED_MODELS=1` — only one model in RAM at a time
- `OLLAMA_NUM_PARALLEL=1` — no concurrent inference requests
- `OLLAMA_NUM_THREAD=6` — leaves 2 CPU cores free for the OS
- `OLLAMA_FLASH_ATTENTION=1` — more efficient attention, reduces peak memory

## Architecture

- `src/` — All Jupyter notebooks (`weekNN_lecture.ipynb`) and their rendered HTML exports.
- `data/` — Raw datasets (CSV and Excel). This directory is gitignored and not version-controlled.

Notebooks follow a weekly lecture structure. Each notebook is self-contained and loads its datasets from `../data/` relative to `src/`.
