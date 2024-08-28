# Jupyter Lab

This is an implementation of JupyterLab that runs in a container using software
called [Apptainer](https://apptainer.org/). Since the app runs in a container,
Slurm commands are not available from within the Jupyter Lab interface, although
they will still be available through the default [Open OnDemand terminal
app](terminal.md).

## Running the app

When you start the app, you will see the standard options to set the duration of
your session and the number of CPUs that you will need, as described on the
[interactive apps page](interactive-apps.md).

In addition, you will see a dropdown menu allowing you to select a container.
There are two different default options (`scipy-notebook` and
`datascience-notebook`), as well as other course-specific images that may have
been prepared for particular use cases.

We use two of the [Jupyter Docker
stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html)
created by Project Jupyter. Specifically, we have the
[scipy-notebook](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook)
and
[datascience-notebook](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html#jupyter-scipy-notebook)
containers configured for use.

The `scipy-notebook` container is a general purpose, Python-only Jupyter Lab app
with commonly used Python libraries such as `numpy`, `pandas`, `matplotlib`, and
of course `scipy`. For a full overview of what's included, see the documentation
for the docker container linked above.

The `datascience-notebook` container has everything in the `scipy-notebook`
image with the addition of additional kernels for the R and Julia programming
languages. For a full overview of what's included, see the documentation for the
docker container linked above.

In addition, we can configure custom software configurations, and this app is
one of the ways that we can do that. If you see an image with your course's name
on it, it's likely for you. Ask your instructor if you aren't sure which
container to use.
