# Shared Software with Spack

Our configuration of OnDemand uses a centrally configured repository of command-line software managed by and available through [Spack](https://spack.readthedocs.io/en/latest/index.html). We provide some pre-installed packages, but if you find that you need some software that is available through Spack, it can be installed to that shared location on request.

## Make the `spack` command available

In order to avoid interfering with any other configurations that you may want to set up, Spack is not configured in your terminal by default. Rather, it must be activated with the following command (note the dot at the start, and be sure to include that with the rest):

```bash
. /shared/spack/share/spack/setup-env.sh
```

This will make the `spack` command available in your terminal session. If you want to use the shared `spack` command in every session, you can add this line to your `~/.bashrc` file.

The Code Server app runs using a Spack package, so the shared `spack` command is available by default in the terminal inside the VS Code interface.

## Spack Environments

Once the `spack` command is available, you can load software. The preferred way to do that in our setup is with a Spack environment. Spack environments are a way of bundling up different software together into a single, easy to load bundle. Spack environments also provide consistency; a Spack environment will consistently load the same set of software, even if new variants of the software are added to the Spack installation. If you've requested software that is installed via Spack, it's likely that an environment was prepared for you by HUIT Academic Technology staff.

To load an environment, you can use the `spack env activate` command, followed by the name of the environment. Spack also provides the `spacktivate` command, which works the same way. So if you have an environment called "testEnv", you can load it with either `spack env activate testEnv` or `spacktivate testEnv`, whichever is easier for you to remember.

## Load packages with `spack`

If you want to load individual packages in an interactive session, you can use the `spack load` command. This lets you specify packages to load by name, version, and even compiler, if there are different variants on the system.

You can list all of the packages available with `spack find`:

```bash
$ spack find
-- linux-amzn2-skylake_avx512 / gcc@7.3.1 -----------------------
berkeley-db@18.1.40                 curl@8.4.0      htslib@1.17         libdivsufsort@2.0.1  libtool@2.4.7     nghttp2@1.57.0       r@4.3.0               unzip@6.0
boost@1.83.0                        curl@8.4.0      hwloc@2.9.1         libffi@3.4.4         libunistring@1.1  openjdk@11.0.20.1_1  readline@8.2          util-linux-uuid@2.38.1
bowtie@1.3.1                        diffutils@3.9   icu4c@67.1          libgff@2.0.0         libxcrypt@4.4.35  openssl@3.1.3        salmon@1.10.2         util-macros@1.19.3
bzip2@1.0.8                         expat@2.5.0     intel-pin@3.27      libiconv@1.17        libxml2@2.10.3    pcre2@10.42          sqlite@3.43.2         which@2.21
ca-certificates-mozilla@2023-05-30  gdbm@1.23       intel-tbb@2021.9.0  libidn2@2.3.4        likwid@5.2.2      perl@5.38.0          staden-io-lib@1.14.8  xz@5.4.1
cereal@1.3.2                        gettext@0.22.3  jemalloc@5.3.0      libmd@1.0.4          lua@5.4.4         pigz@2.7             star@2.7.10b          zlib-ng@2.1.4
cmake@3.27.7                        gmake@4.4.1     libbsd@0.11.7       libpciaccess@0.17    m4@1.4.19         pkgconf@1.9.5        tar@1.34              zstd@1.5.5
code-server@4.12.0                  gzip@1.12       libdeflate@1.18     libsigsegv@2.14      ncurses@6.4       python@3.11.6        texinfo@7.0.3
==> 63 installed packages
```

You can load packages with `spack load` followed by the name of the package. Once you have the package loaded, you'll be able to use the commands that it enables. As an example:

```bash
$ which likwid-perfctr
/usr/bin/which: no likwid-perfctr in (/opt/amazon/openmpi/bin:...)
$ spack load likwid
$ which likwid-perfctr
/shared/spack/opt/spack/linux-amzn2-skylake_avx512/gcc-7.3.1/likwid-5.2.2-aayxcqg6nj5zykdozo5z4yubzjevxhhm/bin/likwid-perfctr
```

The `spack load` command can tolerate some ambiguity if there's only one variant of a software package available. However, if there are multiple variants of the same package, like different versions or software compiled with different compilers, then the command will prompt you to choose which version you mean. That's not an issue in an interactive session, but you should use caution with `spack load` commands in scripts or `.bashrc` files, as changes to the Spack installation can cause those commands to suddenly fail if a new variant of loaded software is installed. The consistency of Spack environments in this circumstance is why they are preferred.

## Use in scripts

If you are preparing a batch job, be sure to include a line to make the `spack` command available, and to load the packages that your job needs.
