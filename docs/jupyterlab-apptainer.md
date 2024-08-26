# JupyterLab (Apptainer)

This is an implementation of JupyterLab that runs in a container using software
called [Apptainer](https://apptainer.org/).

## Differences from Spack implementation

For general purpose data science use cases, the [Apptainer
implementation](jupyterlab-apptainer.md) and the Spack implementation of
JupyterLab are the same. The Apptainer implementation seems to load slightly
faster, and the Spack implementation provides access to Slurm commands directly
from the JupyterLab app.

However, for various course-specific use cases, one or the other implementation
will be in use as the primary means of accessing a custom environment. If you
aren't sure which one to use, ask your instructor; they should receive
information about which implementation to use when they are notified that their
software is ready for use.

## Running the app

When you start the app, you will see the standard options to set the duration of
your session and the number of CPUs that you will need, as described on the
[interactive apps page](jupyterlab-apptainer.md).

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

In addition, we can configure custom software configurations, and the Apptainer
JupyterLab implementation is one of the ways that we can do that. If you see an
image with your course's name on it, it's likely for you. Ask your instructor if
you aren't sure which container to use.
