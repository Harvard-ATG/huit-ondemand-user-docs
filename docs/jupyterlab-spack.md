# JupyterLab (spack)

This is an implementation of JupyterLab that runs directly on compute nodes using a package manager
called [Spack](https://spack.io/).

## Differences from Spack implementation

For general purpose data science use cases, the Apptainer implementation and the
[Spack implementation](jupyterlab-spack.md) of JupyterLab are the same. The
Apptainer implementation seems to load slightly faster, and the Spack
implementation provides access to Slurm commands directly from the JupyterLab
app.

However, for various course-specific use cases, one or the other implementation
will be in use as the primary means of accessing a custom environment. If you
aren't sure which one to use, ask your instructor; they should receive
information about which implementation to use when they are notified that their
software is ready for use.

## Additional Settings

The JupyterLab app that runs via spack has some options in addition to the basic
CPU and time allocations. These allow you to launch a session with an
alternative configuration that you define. 

If you just want to use the default packages included in the app, including
`numpy`, `pandas`, `matplotlib`, and `scipy`, then you don't need to worry about
these settings. If you want to define your own environment with spack, or you
have been instructed that an alternative environment has been prepared for your
class, read on.

## Alternative Spack Installation

The package manager that we use in HUIT Open OnDemand,
[Spack](https://spack.io/), has a self-contained installation in the file
system. That means that within your own home directory, or within a course
shared folder, you can set up a different Spack installation with packages and
environments that you define, and which can draw on the software already
installed globally. The JupyterLab (spack) setup allows you to specify an
alternative Spack path to use, so that the same app configuration can be used
with these other installations.

When setting this option, you must already have an alternative Spack
installation set up, and the installation must include a named environment that
includes the `py-jupyterlab` package. You can refer to this installation by its
absolute path, beginning with `/shared`

## Alternative Spack Environment

The JupyterLab (spack) application also allows you to specify an alternate Spack
environment. [Spack
environments](https://spack-tutorial.readthedocs.io/en/latest/tutorial_environments.html)
define a consistent set of packages in a more durable way than a series of
`spack load` commands. You may be instructed to change this environment if one
has been set up for your course as part of the global Spack installation. If
you've set up your own Spack installation, you must also define an environment
within that installation that includes the `py-jupyterlab` package, as well as
any other packages containing Python modules that you want to have available.
