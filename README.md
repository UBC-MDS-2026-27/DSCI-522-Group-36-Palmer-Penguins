# DCSI-522 Group 36: Palmer Penguins Analysis
**Authors: Eniola Oladimeji, Rachel Yan, David Zhang, Lareina Lyu**

## Summary
In this project, we asked whether we can predict a penguin's sex
from its physical measurements, such as flipper length, bill length,
bill depth, and body mass.
We found that a k-nearest neighbours model predicted sex with high accuracy for all three species.
This suggests that simple body measurements could help researchers
identify penguin sex in the field, although our test sets were small.


## Dataset
The raw dataset is located at `data/raw/penguins.csv`.
The dataset contains measurement of 344 penguins of three species, which are Adélie, Chinstrap, and Gentoo,  collected on three islands in the Palmer Archipelago, Antarctica.

## How to run the analysis
1. Install [Git](https://git-scm.com/downloads),
   [uv](https://docs.astral.sh/uv/getting-started/installation/),
   and [Quarto](https://quarto.org/docs/get-started/).

2. Install TinyTeX, which Quarto needs to render the report to PDF:

   ```bash
   quarto install tinytex
   ```

3. Clone this repository and move into it
 ```bash
   git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Group-36-Palmer-Penguins.git
   cd DSCI-522-Group-36-Palmer-Penguins
```
4. Set up the environment
 ```bash
   uv sync
```
5. Render the report:

   ```bash
   uv run quarto render analysis/penguins-analysis.qmd
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