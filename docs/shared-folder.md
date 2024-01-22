# Shared Folder

In HUIT OnDemand, course staff have access to a shared folder for use in their course. Using this shared folder requires use of the terminal, whether through the OnDemand dashboard or through the terminal in the VS Code interface.

The shared folder will be located at `/shared/courseSharedFolders/$CANVAS_COURSE_ID`, where `$CANVAS_COURSE_ID` can be found in your course's Canvas url: `https://canvas.harvard.edu/courses/CANVAS_COURSE_ID`.

The shared folder should contain two utility scripts; one script configures a link to the folder in the home directory of whoever runs the script, and the other ensures that all content in the folder that the current user can edit has appropriate permisssions.

## Creating a link to the shared folder

You can create a link to the shared folder in your home folder with the included script, like so:

```bash
/shared/courseSharedFolders/$CANVAS_COURSE_ID/map-this.sh
```

That script creates a symbolic link in your home directory to the shared folder called `share`, making it accessible in interactive apps like the VS Code app, and making it easier to access than referencing its absolute location.

If you prefer, you can make your own link by modifying this line:

```bash
ln -s /shared/courseSharedFolders/$COURSE_ID ~/share
```

## Fixing permissions

The script at `/shared/courseSharedFolders/$COURSE_ID/fix-permissions.sh` will do two things to any file or folder that you have write access to in the shared folder:

1. Change the group ownership of the file or folder to the staff group for your course
2. Add group write permissions to the file or folder

If there are files that you did not create in the shared folder, you won't be able to modify their permissions, but running the script will still modify the permissions of files that you created. It will report errors modifying the files you do not own, but that doesn't mean it failed, just that there are files that you couldn't change.

## Support

If you have issues with your shared folder, please reach out to [ithelp@harvard.edu](mailto:ithelp@harvard.edu?subject=HUIT OnDemand shared folder issue). Please be sure to include the name of this platform, "HUIT Open OnDemand", to help your request get routed appropriately.
