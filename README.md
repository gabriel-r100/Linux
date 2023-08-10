# Linux-File-Permissions

## Project description
The task is to update permissions on files and directories within the projects directory.

## Check file and directory details
`ls -la` displays permissions for files in directory, including hidden files

## Describe the permissions string
Looking at permissions for “drafts”, we can see with the first character, that the selected object is a directory denoted by the `d`.

2nd-4th characters show that the user has full read, write, and execute permissions.

5th-7th characters denote that the group, our user is a part of,  have execute permissions. 

Lastly, 8th-10th characters display other users, not a part of our user’s group, have no permissions.

## Change file permissions
Because our company does not allow other users to have write permissions, we will be removing them. Currently, project_k.txt is the only file that is set up incorrectly. We remove the write permission from others with the `chmod o-w project_k.txt` command. Now, all files and directories follow company policy.

## Change file permissions on a hidden file
Hidden files are denoted by the beginning of the filename including a `.`
Ideally we want only read permissions on these files so we run chmod to set proper permissions.


## Change directory permissions
We would like researcher2 to be the only one allowed to access the drafts directory. We can achieve this by removing executable permissions for groups and others.


## Summary
This is my short document explaining commands to modify permissions to both files and directories.
