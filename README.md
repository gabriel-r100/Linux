# Linux-File-Permissions

## Project description
The task is to update permissions on files and directories within the projects directory.

## Check file and directory details
`ls -la` displays permissions for files in directory, including hidden files
![Checking-file-and-directory-details](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/908cc7e6-749b-4acd-aaae-57b681519f41)

## Describe the permissions string
Looking at permissions for “drafts”, we can see with the first character, that the selected object is a directory denoted by the `d`.
![d-file-permissions-explained](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/645ddb18-b123-4f85-9cb8-8f109ba57770)

2nd-4th characters show that the user has full read, write, and execute permissions.
![2-4-file-permissions-explained](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/0562fffc-f820-42ef-915a-410dbbab1477)

5th-7th characters denote that the group, our user is a part of,  have execute permissions. 
![5-7-file-permissions-explained](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/e08fb648-e147-40e8-88fd-6eb1e84af8fd)

Lastly, 8th-10th characters display other users, not a part of our user’s group, have no permissions.
![8-10-file-permissions-explained](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/7952f75e-4572-4a08-b706-cb1b9663e0f9)

## Change file permissions
Because our company does not allow other users to have write permissions, we will be removing them. Currently, project_k.txt is the only file that is set up incorrectly. We remove the write permission from others with the `chmod o-w project_k.txt` command. Now, all files and directories follow company policy.
![removing-other-user-write-permissions](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/d28a4aba-09a9-4cc6-8cdd-9037d5072a51)

## Change file permissions on a hidden file
Hidden files are denoted by the beginning of the filename including a `.`
Ideally we want only read permissions on these files so we run chmod to set proper permissions.
![changing-file-permissions-hidden-file](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/12174b29-190e-4ed0-b93d-9909e047fa7a)

## Change directory permissions
We would like researcher2 to be the only one allowed to access the drafts directory. We can achieve this by removing executable permissions for groups and others.
![change-directory-permissions](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/862acf2b-1b28-4c5d-a47f-25e4d2247453)

Alternatively, because each permission is represented as a three-digit octal number (0-7), table below, permissions can also be updated with a command `chmod 700 /drafts`.<br>
![Three-Digit Octal Permissions](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/3a4a4719-b5b8-4b71-b898-779d30d0c43d)

## Summary
This is my short document explaining commands to modify permissions to both files and directories.
