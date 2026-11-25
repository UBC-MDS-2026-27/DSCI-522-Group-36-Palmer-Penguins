# Contributing

Thank you for your interest in contributing to our Palmer Penguins analysis! We welcome bug reports, suggestions, and improvements from everyone.

Please read our [Code of Conduct](CODE_OF_CONDUCT.md) before contributing.

## Reporting a Bug
If you find a bug (for example, the report does not render or any result looks wrong), please [open an issue](https://github.com/UBC-MDS-2026-27/DSCI-522-Group-36-Palmer-Penguins/issues) and include:
- A short, descriptive title
- The steps to reproduce the problem
- What you expected to happen and what actually happened
- Your operating system 

## Suggesting a Change
If you have an idea to improve the analysis or the documentation, please [open an issue](https://github.com/UBC-MDS-2026-27/DSCI-522-Group-36-Palmer-Penguins/issues) that describes your idea and why it would be useful.

We will discuss it in the issue before any work begins.
If you only want to fix a small typo, you can edit the file directly on GitHub.
Please change the Quarto source (`analysis/penguins-analysis.qmd`)
rather than the rendered HTML or PDF, since those are regenerated every time the report is rendered.

## Setting Up the Project
We all work in the same Docker container that users run, so everyone has
the same environment.

Before you begin, install [Docker Desktop](https://www.docker.com/products/docker-desktop/)
and make sure it is running.
Then follow the steps in the [README](README.md) to clone this repository,
make an ssh key, and download the image with `docker compose pull`.
Run all commands below from the root of the repository.

## Working in the Container with Positron
We use Positron to connect to the container over ssh.
Inside the container, the project folder is available at `/workspace`,
so any file you change there also changes on your computer.

### First-time Setup
1. Download and install [Positron](https://positron.posit.co/download.html).
   Remote SSH support is already included, so no extra extension is needed.
2. Complete the setup steps in the [README](README.md),
   so that you have an ssh key and a local copy of our image.
3. Make sure Git has your name and email:

   ```bash
   git config --global user.email
   ```

   If nothing is printed, add them (use the email linked to your GitHub account):

   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "you@example.com"
   ```

   The container reads these settings from your computer,
   which means commits you make from inside it are credited to you.

### Starting a Work Session
1. Open Docker Desktop and wait until it is running.
   Then, from the project folder in your terminal, launch the container in the background:

   ```bash
   docker compose up -d
   ```

   You can confirm it started with `docker compose ps`, which should list `analysis-env`.

2. In Positron, press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows) to open the Command Palette.
   Search for **Remote SSH: Show Remote Menu** and choose **Connect to Host**.

3. Enter `root@localhost:2222`. Positron opens a second window for the container.
   Choose **Linux** if you are asked about the platform,
   and **Continue** if you are asked to trust the host.
   The very first connection is slow because Positron installs its server in the container,
   so give it a few minutes.
   Once it is ready, you will see `SSH: localhost:2222` in the bottom left corner.

4. The new window starts with no folder open.
   Click **Open Folder**, replace the suggested path with `/workspace`, and press Enter.
   After the window reloads, the Explorer lists our project files.

5. A banner about Restricted Mode may appear at the top.
   Click **Manage** and then **Trust**; otherwise, Positron will not let you start a console.

6. Choose the right Python. Click the interpreter button in the top right corner,
   select **New Console Session…**, and pick the one located at `/opt/venv/bin/python`.
   This is the environment built into our image from `uv.lock`.
   Avoid `/workspace/.venv/bin/python` (it was created on your own computer and
   cannot run in the container) and `/usr/bin/python3` (it is missing our packages).
   If `/opt/venv/bin/python` does not appear, run **Python: Select Interpreter**
   from the Command Palette, choose **Enter interpreter path…**, and type the path yourself.
   You can double-check by running `import sys; print(sys.executable)` in the Console.
   You may still see a warning about `.venv` on the Welcome page;
   it is safe to ignore, and you should not click **Create Python Environment**.

7. You are ready to work. Anything you run from the Terminal, the Console,
   or the Render button now runs inside the container.

8. When you finish, close the container's Positron window and shut the container down
   from the terminal on your computer:

   ```bash
   docker compose down
   ```

### Troubleshooting the connection
- **Docker turned `~/.ssh/id_ed25519.pub` or `~/.gitconfig` into a folder.**
  This happens when the file did not exist the first time the container started.
  Stop the container with `docker compose down`, delete the folder,
  create the ssh key or set your Git name and email, and try again.
- **You are asked for a password.**
  The container cannot find your public key.
  Make sure it is called `id_ed25519.pub`, or update the key path in `docker-compose.yml`.
- **You see "Remote host identification has changed".**
  This is expected after the image is updated.
  Clear the old entry with `ssh-keygen -R "[localhost]:2222"` and reconnect.
- **Pushing from the container asks you to log in to GitHub.**
  Sign in once in the browser window that Positron opens; it will remember you.
- **Port 2222 is already taken.**
  Replace the first `2222` in `docker-compose.yml` with a free port, such as `2223`,
  and connect to that port instead.
- **You use Linux and ssh rejects your key.**
  Uncomment the `StrictModes no` line in the `Dockerfile` and push the change,
  so that GitHub Actions builds an updated image.

## Re-rendering the Report
If you only need to regenerate the report, you do not have to open Positron.
From the project folder, run:

```bash
docker compose run --rm analysis-env uv run quarto render analysis/penguins-analysis.qmd
```

## Changing the Python Packages

Because the packages live inside our Docker image,
adding or upgrading one also means publishing a new image:

1. Start a new branch from the latest `main`.
2. Inside the container, install the package and pin its exact version:

   ```bash
   uv add <package>==<version>
   ```

3. Commit the updated `pyproject.toml` and `uv.lock` in the same commit, then push the branch.
4. GitHub Actions will rebuild the image, upload it to Docker Hub,
   and commit the new image tag to `docker-compose.yml` on your branch.
   Wait for the workflow to finish before moving on.
5. Pull that commit with `git pull`, then download the new image with `docker compose pull`.
6. Open a pull request for review. Once it is merged, the workflow runs again on `main`.
   After it finishes, every team member should run `git pull` on `main` followed by `docker compose pull`.
  
## Updating the Online Report

Our report on GitHub Pages is served from `docs/index.html`,
which is a copy of the rendered report.
Whenever the report changes, render it again and refresh the copy:
```bash
cp analysis/penguins-analysis.html docs/index.html
```
Commit and push `docs/index.html` so that the report on GitHub Pages stays up to date.

## Pull Request Process

1. Branch off an up-to-date `main` and give the branch a short name that describes the change
   (for example, `fix-plot-labels`). Each branch should focus on a single task.
    Team members can create branches in this repository directly; contributors outside the team should first fork the repository and work in their fork.
2. Commit regularly with clear, meaningful commit messages.
3. Before opening a pull request, render the report to make sure nothing is broken.
4. Push your branch and open a pull request into `main`, explaining what you changed and why.
   If it fixes an issue, include `Closes #issue-number` in the description.
5. Every pull request needs an approval from at least one other team member before merging.
   Please never push directly to `main`.

## AI Policy

AI assistance (for example, from Codex, ChatGPT or Claude) is welcome, but submitting work you don't understand is not.

In short: disclose your AI use, understand everything you submit, and don't let an AI agent open issues or pull requests for you.

**Responsibility:**
You are responsible for anything you submit, whether you wrote it yourself or used AI to help. You must be able to explain your changes in your own words.

**Disclosure:**
In your pull request description, say whether you used AI and include which tools you used and what you used them for.

**No autonomous AI contributions:**
AI agents may not open issues or pull requests on their own.

A human must check any AI-generated work and open the issue or pull request themselves.

All reviews and merge decisions are made by humans.

This policy was adapted from the
[earthaccess AI policy](https://earthaccess.readthedocs.io/en/latest/contributor/ai-policy/), which is based on the [SciPy](https://scipy.github.io/devdocs/dev/conduct/ai_policy.html) and [SymPy](https://docs.sympy.org/dev/contributing/ai-generated-code-policy.html) AI policies.

## Attribution
The structure of this guide follows the
[DSCI 522 Breast Cancer Predictor contributing guide](https://github.com/UBC-MDS/DSCI_522_project-template-breast-cancer-predictor/blob/1.0.0/CONTRIBUTING.md)
and the [dplyr contributing guidelines](https://github.com/tidyverse/dplyr/blob/main/.github/CONTRIBUTING.md).