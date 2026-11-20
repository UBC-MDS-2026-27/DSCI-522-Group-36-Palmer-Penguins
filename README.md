# Penguin Sex Prediction from Measurements

**DSCI 522, Group 36**

## Authors

- Eniola Oladimeji
- Rachel Yan
- Lareina Lyu
- David Zhang

## Summary

<!-- TODO: Summarize the main findings once the analysis is finished. -->

This project asks: **can we predict a penguin's sex from its physical measurements (e.g., flipper length and bill length)?** The analysis uses the [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins) dataset.

## Rendered Report

The full report is available here: [penguins-analysis.html](https://ubc-mds-2026-27.github.io/DSCI-522-Group-36-Palmer-Penguins/analysis/penguins-analysis.html)

## How to Run the Analysis

### 1. Clone the repository

```bash
git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Group-36-Palmer-Penguins.git
cd DSCI-522-Group-36-Palmer-Penguins
```

### 2. Set up the environment

This project uses [uv](https://docs.astral.sh/uv/) for Python dependency management. From the repository root, run:

```bash
uv sync
```

### 3. Data acquisition

No manual download is needed. Rendering the Quarto report automatically downloads the raw dataset from the palmerpenguins repository into `data/raw/` and saves the cleaned dataset to `data/processed/`.

### 4. Render the report

From the repository root, run:

```bash
uv run quarto render analysis/penguins-analysis.qmd
```

## Dependencies

- [uv](https://docs.astral.sh/uv/) for Python environment management
- [Quarto](https://quarto.org/) for rendering the report
- Python packages listed in `pyproject.toml` (installed by `uv sync`)

## Licenses

- **Code:** <!-- TODO: e.g., MIT License -->
- **Report and written content:** <!-- TODO: e.g., CC BY-NC-ND 4.0 -->

See [LICENSE.md](LICENSE.md) for the full text.

## AI Use Statement

We used generative AI (Claude) in this project to help with Git workflow questions, debug code, and draft documentation. All AI-generated content was reviewed and edited by team members, who take responsibility for the final work.