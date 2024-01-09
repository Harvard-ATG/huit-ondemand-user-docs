# HUIT OnDemand user documentation

This repository contains the source files for the HUIT OnDemand user documentation, powered by [mkdocs](https://www.mkdocs.org/) and the [mkdocs-material](https://squidfunk.github.io/mkdocs-material/) theme.

## Development environment

The dependencies are defined by [poetry](https://python-poetry.org/), and it's easiest to spin up a new environment using that. If you prefer another virtual environment tool, reference the `pyproject.toml` file for required modules.

With the dependencies set up and your environment activated, running `mkdocs serve` will provide you with a live test version of the site for reference.

## Deployment

To update the GitHub Pages site attached to this repository, use the following command:
```
mkdocs gh-deploy
```
