# Using Spack for Package Management

Spack is software that is pre-configured in HUIT Open OnDemand to enable the
easy installation and management of high performance compute applications. There
is a wide variety of software available, and for [packages with existing spack
configurations](https://packages.spack.io/), the installation is usually just
a one line command from the terminal.

Managing a Spack installation will require heavy use of the terminal; there is
no graphical interface available. If you need help with your course's
environment, please reach out to
[atg@fas.harvard.edu](mailto:atg@fas.harvard.edu).

However, since installations can take a while, and since you likely want a
consistent environment, there are some best practices for managing a spack
installation. You can manage any spack installation that you have access to,
whether it's a [Spack installation in a course shared
folder](spack-course-shared.md) for a course that you're on the teaching staff
for, or a [personal home directory spack installation](spack-local.md).

## Spack Environments

While you can just install packages directly to the Spack installations, Spack
environments provide more stability, especially when being loaded automatically.
For example, if you install one version of a package, load it with a `spack
load` command in your `.bashrc` file, and later install another version of the
same package, then the `spack load` command in your `.bashrc` can suddenly stop
working. Environments have an internal lock file that articulates the exact
packages that are loaded, so they're safe to load from a `.bashrc` file or in an
automated script. When Spack is required for an interactive application, we use
Spack environments for this reason.

The Spack documentation provides a [tutorial on
environments](https://spack-tutorial.readthedocs.io/en/latest/tutorial_environments.html),
which is useful for a more comprehensive understanding of how these environments
function. In this documentation, we'll take a more focused approach, dealing
with common setup and installation tasks for preparing an environment for a
course.

You can only set up environments in environments that you can modify. In HUIT
Open OnDemand, that means that you can only set up environments in your own
personal Spack installation in your home folder, or in a shared course folder.
In both cases, you should have the global spack installation set as an upstream,
whether by the course shared folder's pre-made spack installation script, or by
following our directions on setting up your own Spack installation.

For the rest of this document, we'll assume that you've already sourced the
`setup-env.sh` script from the installation where you want the environment to
be.

### Creating & Activating

For an environment to be used, it must first be created. This is pretty
straightforward, with the command

```bash
spack env create environmentName
```

Replace "environmentName" with whatever you want the environment to be called.
Then the environment can be activated with

```bash
spack env activate environmentName
```

### Adding Packages

To get started, you can add one or more packages. You do this with a command like

```bash
spack add packageSpec
```

You can install a package simply by name, but if you have specific version or
compiler requirements, you can specify those with [Spack's spec
syntax](https://spack.readthedocs.io/en/latest/basic_usage.html#sec-specs).

Adding a package won't install it, but it will associate that package with the
environment itself.

### Installing Packages

The syntax to start an installation is simple, but where to run the installation
is less simple. It's best to run these installations in a Slurm job, since some
installations will take a long time to run. Therefore, we recommend adapting
this bash script for your Spack installation, and using it via `sbatch`. This is
the script that we use to manage the global installation. You can adapt it for
your use by copying the script to a file in your own home directory (we call it
`spackEnvironment.sh`, so you might as well use the same name). Once you have
your own copy of the script in HUIT OOD, you can edit the line marked with `#
CHANGEME` to point the script to your own Spack installation, rather than the
global one.

```bash
#!/bin/bash
if [ -x "${1}" ]
  then
    echo "Environment name is required, e.g. `spackEnvironment.sh environmentName`"
    exit 1
fi

# Change the line below to activate your own Spack environment
. /shared/spack/share/spack/setup-env.sh # CHANGEME
ENVIRONMENT=$1
echo "Activating environment $ENVIRONMENT..."
spack env activate $ENVIRONMENT
echo "Installing packages for $ENVIRONMENT..."
spack install
echo "Done!"
```

From wherever you place that script, assuming you name it `spackEnvironment.sh`,
you can run it as a Slurm job with

```bash
sbatch -c 4 spackEnvironment.sh environmentName
```

Once you've submitted the job, you can check on the job's progress with slurm
commands. For instance, you can see the state of your running jobs with the
command `squeue -u $(whoami)`. A "state" of "CF" indicates your job is allocated
to a job that is currently starting (or configuring), and a state of "R"
indicates that your job is running. This command will also show you the job ID
of your job, which you can use to view the output of your job. The output file
will appear in the directory you started the job from as `slurm-$JOBID.out`,
where `$JOBID` is your job ID.

If you prefer to do this interactively, you can start an interactive Slurm
session with an `salloc` command, then using `srun spack install`. However, this
could require babysitting your terminal to see if there are any errors with the
installation. By running the installation as a batch job, output from the
install process is recorded to an output log file, so you can review what the
script did at your leisure.

### Saving an Environment Definition

If you have spent some time creating a Spack environment during the course of a term, you may want to re-use the same environment in future terms. Or, if you leave the university, you may want to save an environment definition to take with you to another institution to use on their infrastructure. Spack supports this with `spack.yaml` files.

When you create an environment, a file is created at
`$SPACK_ROOT/var/spack/environments/$ENVIRONMENT_NAME/spack.yaml`, where
`$SPACK_ROOT` is the location of your spack installation, and
`$ENVIRONMENT_NAME` is the name of the environment that you've set up. You can
copy this file to another location where you can download it. Say you save it as
MyEnvironment.yaml. Then, in the future, you can re-create the same environment
with 

```bash
spack env create environmentName MyEnvironment.yaml
```
