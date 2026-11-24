# Penguin Sex Prediction from Measurements

**DSCI 522, Group 36**

## Authors

- Eniola Oladimeji
- Rachel Yan
- Lareina Lyu
- David Zhang

## Summary
This project asks: **can we predict a penguin's sex from its physical measurements (e.g., flipper length and bill length)?** The analysis uses the [Palmer Penguins](https://github.com/allisonhorst/palmerpenguins) dataset.

We trained a separate k-nearest neighbours model for each species and found that it predicted sex with high accuracy for all three species, well above the baseline of always guessing the more common sex.
This suggests that simple body measurements could be used as a quick first estimate of penguin sex in the field, although our test sets were small.

## Rendered Report

The full report is available here: [penguins-analysis.html](https://ubc-mds-2026-27.github.io/DSCI-522-Group-36-Palmer-Penguins/analysis/penguins-analysis.html)

## How to Run the Analysis

### 1. Clone the repository

```bash
git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Group-36-Palmer-Penguins.git
cd DSCI-522-Group-36-Palmer-Penguins
```
> **Important:** Do not skip step 2. Without an existing key file, Docker will automatically create an empty folder named `~/.ssh/id_ed25519.pub`, and SSH connections into the container will fail until you delete that folder and run `ssh-keygen -t ed25519`.

### 2. Create an SSH key (if you don't already have one)

You can check if you already have an Ed25519 key by running `ls ~/.ssh/id_ed25519.pub` in your terminal. If the file does not exist, create one by running the command below and pressing **Enter** at each question:
```bash
ssh-keygen -t ed25519
```

### 3. Download docker image 
From the repository root, pull the pre-built analysis container image:
``` bash
docker compose pull
```

### 4. Render the report
From the repository root, run the analysis inside the container:
```bash
docker compose run --rm analysis-env uv run quarto render analysis/penguins-analysis.qmd
```

No manual data download is needed—rendering the Quarto report automatically downloads the raw dataset from the `palmerpenguins` repository into `data/raw/` and saves the cleaned and split datasets to `data/processed/`.

### 5. How to stop the container 
Because the render command uses the `--rm` flag, the container stops and is removed automatically by itself as soon as the render finishes. *(If you start the container in the background with `docker compose up -d`, run `docker compose down` to stop and remove it.)*

## Contributing

Want to make changes to the project? Please see [CONTRIBUTING.md](CONTRIBUTING.md) for instructions on setting up your development environment and submitting changes.

## Dependencies

- [Docker](https://docker.com) (with Docker Compose) to run the containerized analysis environment
- Inside the container: [uv](https://docs.astral.sh/uv/), [Quarto](https://quarto.org/), Python, and the packages listed in `pyproject.toml` and `uv.lock`

## Licenses

- **Code:** MIT License
- **Report and written content:** CC BY-NC-ND 4.0

See [LICENSE.md](LICENSE.md) for the full text.

## AI Use Statement

We used generative AI (Claude) in this project to help with Git workflow questions, debug code, and draft documentation. All AI-generated content was reviewed and edited by team members, who take responsibility for the final work.