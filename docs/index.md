# HUIT Open OnDemand

HUIT Open OnDemand is a new platform to provide access to high performance
compute (HPC) resources for courses. It runs in AWS using ParallelCluster,
unlike other HPC resources used for research that are housed in physical data
centers. If you have access to the platform, you can log in via
[ood.huit.harvard.edu/](https://ood.huit.harvard.edu/)

HUIT Open OnDemand is only available for use in courses. If you want to use it
in your course, you need to submit a request at
[atg.fas.harvard.edu/academic-computing](https://atg.fas.harvard.edu/academic-computing).
We need a new request for each semester that you intend to use the platform for,
so that we can ensure that the platform is still needed, and that we're
providing the software and compute resources required for your course.

## Interactive Software

In OnDemand, users have access to a file management app to access files in their
OnDemand home directory through a browser. They also have access to a terminal
app that provides browser access to a terminal in the cluster. In addition,
we've set up additional interactive apps for different use cases, outlined on
our [interactive apps page](interactive-apps.md)

## Shared Command Line Software

This platform uses [Spack](https://spack.readthedocs.io/en/latest/index.html) to
manage software packages that run on compute nodes. For more information on the
shared spack packages, see the [Shared Spack Software](spack-shared-software.md)
documentation page.

If you prefer to install software to your home directory, or if you want to test
out new software configurations, you can install spack directly to your home
directory. For more information on that, visit the [Local Spack
Installation](spack-local.md) documentation page.
