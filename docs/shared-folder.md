# Shared Folder

In HUIT OnDemand, course staff have access to a shared folder for use in their
course. Users in a course will have a link created to the shared folder for any
course that they are enrolled in upon login to HUIT Open OnDemand. The shared
folder is named for the Canvas course ID for the course they are enrolled in,
usually a six digit number. This link is to the shared folder's absolute path,
which is

```
/shared/courseSharedFolders/${CANVAS_COURSE_ID}outer/${CANVAS_COURSE_ID}
```

This uses `${CANVAS_COURSE_ID}` as a placeholder for the actual course ID.

The shared folder should contain three utility scripts:

- `fix-permissions.sh`
- `link_folder.sh`
- `setup_spack.sh`

The `fix-permissions.sh` script sets appropriate permissions on the contents of
the folder, which is useful if students or teaching staff run into permisssions
errors in the course.

The `link_folder.sh` script will re-create the link to the shared folder for a
user in the case where it is removed. If someone unintentionally removes the
link to the shared folder, they can run this script from the absolute path to
the shared folder to recreate it:

```bash
/shared/courseSharedFolders/${CANVAS_COURSE_ID}outer/${CANVAS_COURSE_ID}/link_folder.sh
```

The `setup_spack.sh` folder is there for course staff to set up a Spack
installation for their course, and then link it to the global installation as an
upstream. For more details about this kind of setup, see the [course level Spack
documentation](spack-course-shared.md).

## Support

If you have issues with your shared folder, please reach out to
[ithelp@harvard.edu](mailto:ithelp@harvard.edu?subject=HUIT Open OnDemand shared
folder issue). Please be sure to include the name of this platform, "HUIT Open
OnDemand", to help your request get routed appropriately.
