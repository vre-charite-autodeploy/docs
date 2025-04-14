# Deploy MkDocs GitHub Pages

This repository contains a GitHub Actions workflow that extracts README files from all repositories and provides them as documentation using [mkdocs](https://www.mkdocs.org/) on [GitHub Pages](https://pages.github.com/).

## How it works

When new commits are pushed, the `deploy` pipeline in the `deploy.yaml` file is executed. The following list briefly describes what happens:

1. **Check out repository**: The workflow starts by checking out the current repository.
2. **Set up Python**: Python version 3.x is set up.
3. **Install dependencies**: The required Python packages (`mkdocs`, `mkdocs-material`, `PyYAML`, `requests`) are installed.
4. **Fetch documentation**: A Python script (`fetch_docs.py`) is executed to fetch the README files and additional documentation files from the repositories of the specified organization.
5. **Create MkDocs site**: The documentation site is created using MkDocs.
6. **Deploy to GitHub Pages**: The created documentation site is deployed to the `gh-pages` branch of the repository.

## Files

- `fetch_docs.py`: A Python script that fetches the README files and additional documentation files from the repositories of an organization and saves them in the docs directory.
- `doc_map.yaml`: An optional YAML file that defines additional documentation files for each repository. vre-documentation.md can serve as an example here.
- `mkdocs.yml`: The configuration file for MkDocs, which defines the structure and theme of the documentation site.


## Compile source

This repo is primarily intended to be executed within a pipeline. It is not actually intended to be run manually. If desired, the following steps can be taken to obtain the compiled HTML files.

1. **Create and activate virtual environment (optional but recommended):**:

```bash
python -m venv venv
source venv/bin/activate
```

2. **Install dependencies:**:

```bash
pip install mkdocs mkdocs-material PyYAML requests
```

3. **Fetch documentation:**:

Run the `fetch_docs.py` script to fetch the README files and additional documentation files from the repositories of the specified organization:

```bash
python fetch_docs.py vre-charite-autodeploy
```

 4. **Create MkDocs site**:

 Create MkDocs site HTML pages:

```bash
mkdocs build
```

The created HTML pages can now be found in the `build/` directory.