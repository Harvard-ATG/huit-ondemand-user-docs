# Using Spack From Your Home Directory

If you want to use different packages than the shared packages, or if you want to test out a package before requesting that it be installed in the shared context, you can also install a different `spack` to your home directory.

## Installing

Installing Spack just requires cloning its git repository:

```bash
git clone --depth=100 --branch=releases/v0.21 https://github.com/spack/spack.git ~/spack
```

You can change `~/spack` if you want to install to another location.

Once you have Spack cloned, you can find the activation script in `<install location>/share/spack/setup-env.sh` That means if you installed spack via the command above, you can activate it with

```bash
. ~/spack/share/spack/setup-env.sh
```

## Setting an upstream

You can build all of your own dependencies in your home folder, but it can be more expedient to use the pre-build software in the shared spack installation as a starting point. To enable this, you need to set the shared installation directory as an [upstream](https://spack.readthedocs.io/en/latest/chain.html). The easiest way to do this is to run this command with your local spack environment activated:

```bash
spack config add upstreams:spack-instance-1:install_tree:/shared/spack/opt/spack
```

## Adding packages

With a spack installation in your home directory, you can manage your own package installations. You can look for packages with `spack list <packagename>`, see your installed packages with `spack find`, and add new packages with `spack install <packagename>`

When using `spack` installed to your home directory, make sure that any scripts that reference local packages activate your spack environment, not the shared environment.

For more on managing a Spack installation and Spack environments, see our [Spack
package management docs](package-management.md).
