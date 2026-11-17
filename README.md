# DCSI-522 Group 36: Palmer Penguins Analysis
Authors: Eniola Oladimeji, Rachel Yan, David Zhang, Lareina Lyu

## Summary
In this project, we use the Palmer Penguins data set to build a predictive model
from penguin body measurements, such as bill length, flipper length, and body mass.
Our research question and findings will be added as the analysis progresses.

## Report
The rendered report can be found here.

## Environment Setup
This project uses `uv` for Python dependency management. After cloning the repo, run:
```bash
uv sync
```

## Dataset
The raw dataset is located at `data/raw/penguins.csv`.
The dataset contains measurement of 344 penguins of three species, which are Adélie, Chinstrap, and Gentoo,  collected on three islands in the Palmer Archipelago, Antarctica.

## How to run the analysis
1. Clone this repository and move into it
 ```bash
   git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Group-36-Palmer-Penguins.git
   cd DSCI-522-Group-36-Palmer-Penguins
```
2. Set up the environment
 ```bash
   uv sync
```
tbc

## Dependencies
- uv
- Quarto
- Python packages are listed in `pyproject.toml`
  and pinned to exact versions in `uv.lock`.

## License
The code in this repository is licensed under the MIT License.
The written report, figures, and documentation are licensed under the
Creative Commons Attribution-NonCommercial-NoDerivatives 4.0 International License
(CC BY-NC-ND 4.0).
See [`LICENSE.md`](LICENSE.md) for the full license details.

The penguin data was collected by Dr. Kristen Gorman and the Palmer Station
Long Term Ecological Research Program (Gorman et al., 2014)
and accessed through the palmerpenguins package (Horst et al., 2020).
It is subject to its own license (CC0), and we do not claim ownership of it.

## AI Use Statement
We used AI tools (e.g. Claude, Chatgpt) to support our learning throughout this project.
Specifically, we used them to:
- Help us understand code and commands we were unfamiliar with, for example, Git commands and Quarto syntax
- Explain concepts or errors that we found confusing
- Suggest ideas and possible approaches, such as how to structure our project
  and what to consider when choosing a data set

## Reference