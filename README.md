<h1>Linux</h1>




<h2>General Linux</h2>
<detailsopen><summary><b>Viewing and changing permissions, viewing hidden files.</b></summary>

<h3>Navigation and File Permissions</h3>

The terminal can print our the current directory you are in with the `pwd`. (**p**resent **w**orking **d**irectory)<br>
Using the `ls` command we can print out the directories and files within the current directory.<br>
We can also use the `ls` command to print out the contents of a directory that you have not moved into yet.<br>

![1-pwd-ls-ls-directory](https://github.com/gabriel-r100/Linux/assets/55646808/fb9bb639-7a6d-484b-b3f9-f2a94620eef4)

We can navigate through our directories using the `cd` command (**c**hange **d**irectory)<br>

![2-cd](https://github.com/gabriel-r100/Linux/assets/55646808/a99c63de-891c-4a15-b520-e98f09cc9c2e)

Two view our directory and file permissions, we can add the `-l` option to our `ls` command.

![3-ls-l](https://github.com/gabriel-r100/Linux/assets/55646808/21507c37-aa64-48b6-b7a9-37f50d7720f6)

<h3>Deciphering Permissions Output</h3>
The first character signals the file type, `d` for directory `-` for a file.<br><br>
The next three characters define the permissions for the owner of the file.<br>
The next three characters are for the owner's group permissions.<br>
The last three characters are for everyone else. (other)<br><br>

`r` provides read permissions<br>
`w` provide write permissions<br>
`x` provides executable permissions<br>


![linux-permissions drawio](https://github.com/gabriel-r100/Linux/assets/55646808/bbc84164-3317-4ae2-9d22-ea62984f1d62)
<br>
By default, created files have a file permission of `rw` for the owner and `r` for the owner's group and everyone else.<br>
<br>
Alternatively, because each permission is represented as a three-digit octal number (0-7), table included below, we could read the file permissions of `test.txt` as `644`
![Three-Digit Octal Permissions](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/3a4a4719-b5b8-4b71-b898-779d30d0c43d)

<h3>Change file permissions</h3>

Because our company does not allow other users to have write permissions, we will be removing them. Currently, project_k.txt is the only file that is set up incorrectly. We remove the write permission from others with the `chmod o-w project_k.txt` command. Now, all files and directories follow company policy.
![removing-other-user-write-permissions](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/d28a4aba-09a9-4cc6-8cdd-9037d5072a51)

<h3>Change file permissions on a hidden file</h3>

Hidden files are denoted by the beginning of the filename including a `.`
Ideally we want only read permissions on these files so we run chmod to set proper permissions.
![changing-file-permissions-hidden-file](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/12174b29-190e-4ed0-b93d-9909e047fa7a)

<h3>Change directory permissions</h3>

We would like researcher2 to be the only one allowed to access the drafts directory. We can achieve this by removing executable permissions for groups and others.
![change-directory-permissions](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/862acf2b-1b28-4c5d-a47f-25e4d2247453)


</details>




<h2>Kali Linux Tools</h2>

