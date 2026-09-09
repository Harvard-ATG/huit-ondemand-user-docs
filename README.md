# HUIT OnDemand user documentation

This repository contains the source files for the HUIT OnDemand user documentation, powered by [mkdocs](https://www.mkdocs.org/) and the [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) theme.

## Development environment

This repo uses `mkdocs`, managed with [uv](https://docs.astral.sh/uv/). Dependencies and their pinned versions are in `pyproject.toml` and `uv.lock`.

To set up your environment:
```
uv sync
```

To preview the site locally:
```
uv run mkdocs serve
```

## Deployment

To update the GitHub Pages site attached to this repository, use the following command:
```
uv run mkdocs gh-deploy
```
