# HUIT Open OnDemand

HUIT OnDemand is a new platform to provide access to high performance compute (HPC) resources for courses. It runs in AWS using parallel cluster, unlike other HPC resources used for research that are housed in physical data centers.

## Interactive Software

In OnDemand, users have access to a file management app to access files in their OnDemand home directory through a browser. They also have access to a terminal app that provides browser access to a terminal in the cluster. In addition, we've added a Visual Studio Code app to provide a browser-based IDE that provides another point of entry to the cluster.

## Shared Command Line Software

This platform uses [Spack](https://spack.readthedocs.io/en/latest/index.html) to manage software modules that run on compute nodes. For more information on the shared spack modules, see the [Shared Spack Software](spack-shared-software.md) documentation page.

If you prefer to install software to your home directory, or if you want to test out new software configurations, you can install spack directly to your home directory. For more information on that, visit the [Local Spack Installation](spack-local.md) documentation page.
