# RStudio

We can provide an R environment with RStudio for courses that require it. If
this has been set up for your course, you will see an app with a name like
"RStudio - Course Code" in your list of interactive apps in your Open OnDemand
dashboard.

When launching an RStudio session, you can set a number of CPU cores available
to the session, as well as the duration of the session. Using a smaller number
of CPUs can help your session start faster, since it will be easier to fit it
into running nodes. Session durations cannot be extended, so if you're going to
be working for a while, it may be better to set a long session duration, and
cancel the session from your "My Interactive Sessions" page if you finish early.

**Using R in batch compute:** If you have occasional needs to run R code in
batch compute sessions, using slurm commands like `sbatch`, you can use the
underlying apptainer container for the RStudio app to provide a directly
analogous environment. If you're going to be using R batch compute regularly, or
if you have questions about using R in batch compute, reach out to 
[atg@fas.harvard.edu](mailto:atg@fas.harvard.edu)

## Managing Packages

You should be able to install packages for yourself as normal with an
`install.packages()` command in your R terminal. The default behavior for R is
to install these packages in a folder in your home directory, which R may need
to create for you.

However, instructors may wish to install packages for students in a course, so
each student doesn't need to install required packages themself. To facilitate
this, we set up an R package install location in the course shared folder for
courses using RStudio. The default installation location for new packages is
still in a user's home directory, so instructors who want to install packages
for their students should do the following:

1. Find the shared package install location with `.libPaths()`. Your output will
   be different, but look for a location containing "`courseSharedFolders`". Note
   the number to the left of that location.
```R
> .libPaths()
[1] "/shared/home/uuu000/R/x86_64-pc-linux-gnu-library/4.5"                           
[2] "/usr/local/lib/R/site-library"                                                   
[3] "/usr/local/lib/R/library"                                                        
[4] "/shared/courseSharedFolders/000000outer/000000/R/x86_64-pc-linux-gnu-library/4.5"
```
2. Install package(s) to the shared location. You can use the `.libPaths()`
   function and the index number you noted to install to the shared location
   without going to the trouble of copying and pasting it. In the example above,
   one could install `ggplot2` to the shared location like so:
```R
install.packages('ggplot2', lib=.libPaths()[4])
```

If you encounter problems with this process, please reach out to us at
[atg@fas.harvard.edu](mailto:atg@fas.harvard.edu).
