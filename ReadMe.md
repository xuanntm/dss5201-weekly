# Project Context: Jupyter Analysis
This project focuses on data analysis and scripting using Jupyter Notebooks (`.ipynb`).

## User Preferences & Rules
- **Commenting Style:** Every code cell MUST include detailed inline comments explaining the "why" behind the logic, not just the "what."
- **Notebook Handling:** When creating or editing `.ipynb` files, ensure a markdown cell precedes each major code block to explain the goal of that section.
- **Execution:** Before finalizing a notebook, use `jupyter nbconvert --execute --inplace [filename].ipynb` to ensure all cells run without error.
- **Libraries:** Always prefer using `pandas`, `matplotlib`, and `seaborn` for data tasks unless otherwise specified.

## Project Structure
- `src/`: Contains all Jupyter Notebook files.
- `data/`: Raw and processed datasets.

## Create custom environment and install necessary libraries
```shell
python3.12 -m venv venv-dss5201
source venv-dss5201/bin/activate
pip install -r requirements.txt
pip freeze > requirements_2026April.txt
```