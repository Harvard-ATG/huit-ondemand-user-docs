# Spack in shared course folder

HUIT Open OnDemand comes with Spack already installed, and we try to make sure
that all of the software that instructors request is available from that global
Spack installation. However, there may be cases where teaching staff want
flexibility during the semester to install Spack packages on their own, while
still sharing those installations with students. For this, it's possible to set
up a Spack installation in the course shared folder provisioned by default for
each course.

Each shared course folder comes with a script, `setup_spack.sh`, which sets up a
new Spack installation in the shared course folder and connects it to the global
installation as an upstream source. This new Spack installation can be managed
by course staff, without having to reinstall packages that are already installed
globally.

The way to activate the global installation is by sourcing a script from that
global installation, like so:

```bash
. /shared/spack/share/spack/setup-env.sh
```

For a spack installation in a shared course folder, anyone with access can
activate it by following the link in their home directory. For a class with
course ID 000000, that would look like this:

```bash
. ~/000000/spack/share/spack/setup-env.sh
```

You should test the command to make sure it works first, but you can add a line
like that one to your `~/.bashrc` file so that the Spack installation in your
shared course folder is activated whenever you log in. Just be sure that it
works, because problems with your `~/.bashrc` file can also cause problems with
other interactive apps.

Anyone on the teaching staff should have permission to modify the spack
installation, including by installing new packages and creating new
environments.

For more on managing a Spack installation and Spack environments, see our [Spack
package management docs](package-management.md).
