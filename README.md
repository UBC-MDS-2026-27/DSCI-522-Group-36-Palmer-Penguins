Credit Card Fraud Detection (DCSI-522 Group 36)
Authors
Eniola Oladimeji
Rachel Yan
Lareina Lyu
David Zhang

<!-- TODO: fill in once the analysis is finished. -->

We asked the question: Can we predict a penguin’s sex from its measurements (flipper length, bill length)


How to Run the Analysis
1. Clone the repository
bash
git clone https://github.com/UBC-MDS-2026-27/DSCI-522-Group-36-Palmer-Penguins.git
cd DSCI-522-Group-36-Palmer-Penguins

2. Set up the environment

This project uses uv for Python dependency management. From the repository root, run:
bash
uv sync

3. Data acquisition
No manual download is needed. Running the Quarto report automatically 
downloads the raw dataset from the palmerpenguins repository into data/raw/ and saves the cleaned dataset to data/processed/.


4. Render the report

From the repository root, run:

bash
uv run quarto render analysis/penguins-analysis.qmd



Dependencies
uv for Python environment management
Quarto for rendering the report
Python packages are listed in pyproject.toml and installed by uv sync
Licenses
Code: [e.g., MIT License]
Report and written content: [e.g., CC BY-NC-ND 4.0]

See LICENSE.md for the full text.


AI Use Statement

We used generative AI (Claude) in this project to help with Git workflow questions, debug code, and draft documentation. All AI-generated content was reviewed and edited by team members, who take responsibility for the final work.

Rendered Report

https://ubc-mds-2026-27.github.io/DSCI-522-Group-36-Palmer-Penguins/analysis/penguins-analysis.html 