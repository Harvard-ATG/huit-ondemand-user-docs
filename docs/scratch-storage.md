# Scratch Storage

HUIT Open OnDemand gives every user a private scratch directory at
`/scratch/$USER`, where `$USER` is your username. Use scratch storage for
fast, temporary storage during a compute job. Typical uses include
intermediate files and large datasets that your job reads and writes.

!!! warning "Scratch storage is ephemeral"
    Scratch storage does not keep multiple copies of your data. A file in
    `/scratch/$USER` can disappear at any time, even outside of any job. Do
    not use scratch storage for long-term storage. Save any results that you
    want to keep in your home directory instead.

To find your username, run this command in a terminal on the cluster:

```
echo $USER
```

If this command returns nothing, run `id -nu` instead.

## How your scratch directory gets created

The system creates `/scratch/$USER` automatically the first time you run a
job, whether through an interactive app, `sbatch`, or `srun`. Your scratch
directory is private: only you can read or write it.

## Using the Terminal app before running a job

The [Terminal app](terminal.md) connects you to a login node, not a compute
node. If you open the Terminal app before you run any job, `/scratch/$USER`
does not exist yet.

To create your scratch directory now, run this command:

```
srun --pty true
```

This command runs a simple job on a compute node. The job creates
`/scratch/$USER`. Scratch storage exists on both login and compute nodes, so
your scratch directory then also appears in the Terminal app.

Even after `/scratch/$USER` appears in the Terminal app, do not run compute
intensive work there. [Login nodes are not for
computing](terminal.md#terminal-app). Submit a job instead.
