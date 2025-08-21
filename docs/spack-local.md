# Using Spack From Your Home Directory

If you want to use different packages than the shared packages, or if you want to test out a package before requesting that it be installed in the shared context, you can also install a different `spack` to your home directory.

## Installing

Installing Spack just requires cloning its git repository:

```bash
git clone --depth=2 --branch=releases/v0.21 https://github.com/spack/spack.git ~/spack
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

## Package repository

As of [Spack v1.0.0](https://github.com/spack/spack/releases/tag/v1.0.0),
package definitions in Spack are separate from the Spack tool itself. This means
you can configure a location for package definitions separately from the Spack
tool definition. When you create a local spack install, its default behavior is
to create a package repository in your home directory under `~/.spack`.

Having your own package repository in your home directory allows you to manage
your own package definitions, allowing you to edit package specifications to
change how applications are configured, or to experiment with the latest
versions of software. However, if you don't need or want to do those things, you
may want to re-use the package directory used in the global Spack install to
save some time and space. If you want to do that, you can run this command:

```bash
spack repo set --destination /shared/spack-packages builtin
```

This will set your currently active Spack installation to use the package
repository configured for the global Spack installation.

## Adding packages

With a spack installation in your home directory, you can manage your own
package installations. You can look for packages with `spack list
<packagename>`, see your installed packages with `spack find`, and add new
packages with `spack install <packagename>`

When using `spack` installed to your home directory, make sure that any scripts
that reference local packages activate your spack environment, not the shared
environment.

For more on managing a Spack installation and Spack environments, see our [Spack
package management docs](package-management.md).

# Further Resources

- [Official Spack Documentation](https://spack.readthedocs.io/en/latest/)
- [Spack v1.0.0 release
  notes](https://github.com/spack/spack/releases/tag/v1.0.0) - Spack entered
  `v1.0` over the summer of 2025, so some of the most recently implemented
  features may not yet be reflected in the main documentation.
