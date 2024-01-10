# Using Spack From Your Home Directory

If you want to use different modules than the shared modules, or if you want to test out a module before requesting that it be installed in the shared context, you can also install a different `spack` to your home directory.

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

## Adding modules

With a spack installation in your home directory, you can manage your own module installations. You can look for modules with `spack list <modulename>`, see your installed modules with `spack find`, and add new modules with `spack install <modulename>`

When using `spack` installed to your home directory, make sure that any scripts that reference local modules activate your spack environment, not the shared environment.
