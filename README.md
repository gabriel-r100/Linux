<h1>Linux</h1>




<h2>General Linux</h2>




<details><summary><h2>Viewing and changing permissions, viewing hidden files.</h2></summary>

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
The last three characters are for everyone else. (other)<br>
<br>
`r` provides read permissions<br>
`w` provide write permissions<br>
`x` provides executable permissions<br>


![linux-permissions drawio](https://github.com/gabriel-r100/Linux/assets/55646808/bbc84164-3317-4ae2-9d22-ea62984f1d62)
<br>
By default, created files have a file permission of `rw` for the owner and `r` for the owner's group and everyone else.<br>
<br>
Alternatively, because each permission is represented as a three-digit octal number (0-7), table included below, we could read the file permissions of `test.txt` as `644`<br>
![Three-Digit Octal Permissions](https://github.com/gabriel-r100/Linux-File-Permissions/assets/55646808/3a4a4719-b5b8-4b71-b898-779d30d0c43d)

<h3>Changing File/Directory Permissions and Owner</h3>

To update the file/directory permissions, we can use the `chmod`.<br>
To transfer ownership of a group we can use the `chgrp` command.<br>
Additionally, if you would like to update the owner of the file, you can use the `chown` command.<br>
![5-chmod-chown](https://github.com/gabriel-r100/Linux/assets/55646808/cbbf242a-76fa-4a05-bc0b-77bda94c7083)


<h3>Viewing Hidden Files</h3>

Hidden files start with a `.`, we can show them in our `ls` command using the `-a` option.<br>
![6-ls-a](https://github.com/gabriel-r100/Linux/assets/55646808/9a25de52-a5c2-4eee-b10c-bda640111867)

We can combine options by entering them after the hyphen. `-la` will list contents including hidden files
![7-ls-la](https://github.com/gabriel-r100/Linux/assets/55646808/9bbe442a-8f24-4f94-9fcf-6f35dc2960a5)

</details>

`pwd`, `cd`, `ls -la`, `chmod`, `chown`




<details><summary><h2>Default and Special Permissions</h2></summary>

<h3>Default Permissions</h3>

By default, Linux sets the permissions for new files using the three-digit octal permissions of `666`, meaning everyone has read and write access.<br>
When I check the permissions on my files currently, they are set to `644` I can check what `umask` is configured to see what permissions are default on my system.<br>
The `umask` is located at `/home/<user>/.profile`, in my case `/home/gabriel/.profile`<br>

![2-profile](https://github.com/gabriel-r100/Linux/assets/55646808/93123daf-4e74-4573-9eed-dec2d61d94b0)

The `umask` is subtracted from the Linux default permissions resulting in permissions of `644`

![1-default_permissions](https://github.com/gabriel-r100/Linux/assets/55646808/16dd148f-46ac-46ee-a55f-d9ed4e8a8cf9)

<h3>Special Permissions</h3>

`SUID` elevates permissions to the owner. It does this by setting a bit to allow any user to execute the file with the owner's permission but does not extend those permissions beyond that file.<br>
To set a `SUID` bit, we enter a `4` before our permissions. `chmod 4644 <file>`, we will see a capital `S` bit placed on the write place.<br>

![3-SUID-644](https://github.com/gabriel-r100/Linux/assets/55646808/6e6ce7d2-3a55-4327-9156-d6b54ecfacd0)

`SGID` elevates the permissions to the **owner's group**. It does this similar to `SUID` but denoted with a `2`.<br>
To set the `SGID` bit, we enter a `2` before our permissions. `chmod 2644 <file>`, we can see a capital `S` on the execution place of the group.<br>

![4-SGID-644](https://github.com/gabriel-r100/Linux/assets/55646808/f21fe489-a396-4851-990e-7e537aae7d57)

We can also apply the `SGID` bit to a directory but new files created in the directory will belong to the owner's group, helpful when multiple people will contribute to a directory.<br>

A sticky bit a legacy permission bit used to allow a user to delete or rename files within a directory.<br>
Modern distributions now ignore the sticky bit.

</details>

`umask`, `SUID`, `SGID`, sticky bit




<details><summary><h2>Text Output and Manipulation</h2></summary>

<h3>Outputting File Contents</h3>

We have a few options when choosing to output the contents of a file to our terminal.<br>
<br>
`cat` will output the entirety of the contents at once<br>
`head` will output the first 10 lines of a file (10 is default)<br>
`tail` will output the last 10 lines of a file (10 is default)<br>
`nl` will output the entirety of the contents but with line numbers<br>

![linux-text-output drawio](https://github.com/gabriel-r100/Linux/assets/55646808/af853ae6-e47e-4291-b1f1-b4a5b5497d5d)

With both `head` and `tail` we can modify the number of lines by adding the number with the following syntax: `head -20 <filename>`, `tail -20 <filename>` <br>

![3-head-20](https://github.com/gabriel-r100/Linux/assets/55646808/8448bccd-f092-4c7c-8a4b-43465bfb3490)
![5-tail-20](https://github.com/gabriel-r100/Linux/assets/55646808/81eff1f9-fa1f-421e-a489-d7dde625cb28)

Additionally, we also have the `more` and `less` command, these also output the contents of text but allow you to scroll page by page. (only shows you the amount your terminal can display at once.
![10-more-config](https://github.com/gabriel-r100/Linux/assets/55646808/95f555f1-bd56-44c5-8eb0-a69444aa32fa)


`less` has a few more functionalities such as being able to search while outputting the contents (matches what you look for instead of only showing you lines that match with `grep`). You will need to enter `/` to enter your search term.<br>
![11-less-config](https://github.com/gabriel-r100/Linux/assets/55646808/9049104f-1916-4b29-834f-1aa3c488b6d4)
![11-less-config-search](https://github.com/gabriel-r100/Linux/assets/55646808/651367a9-0e43-4dda-a015-3e70446000c1)


<h3>Manipulating Text</h3>

We can narrow down output to particularly what we are looking for with the `grep` command in combination with one of our text output commands.<br>
Syntax is: `cat <filename> | grep <key>` replace <key> with what you would like to look for.<br>

![7-grep](https://github.com/gabriel-r100/Linux/assets/55646808/631fefee-c9af-48da-a760-d110c758d990)

We can also find and replace within files with the `sed` command.<br>

![8-sed](https://github.com/gabriel-r100/Linux/assets/55646808/bb9c5ab9-ebf3-4c18-8461-923f72f54f00)

`s` command performs substitution<br>
`bottom` being replaced with `end`<br>
`g` option tells Linux that you would like this globally<br>
  - If you leave the global flag out, it will only replace the first occurrence
  - Can target a specific occurrence by adding a number instead of `g`
    - `sed s/bottom/end/2 test.txt > test.txt` will only replace the second occurrence

</details>

`cat`, `head`, `tail`, `nl`, `grep`, `sed`, `less`, `more`




<details><summary><h2>Network Configurations and Inspection</h2></summary>
To view our network interfaces/adapters and their configurations, we can use the `ifconfig` command or on newer Linux distributions, the more modern and featured `ip address` command.<br>
As you can see below, my Debian 12 distribution does not have `ifconfig` installed by default.<br>

![1-ifconfig](https://github.com/gabriel-r100/Linux/assets/55646808/823e4187-519b-4d8f-b296-59face627404)
![3-ip-address](https://github.com/gabriel-r100/Linux/assets/55646808/ad184232-a731-4d3b-8dac-a5faf41b6ec9)
<br>
Additionally, we can view our wireless interfaces with the command `iwconfig`.

![2-iwconfig](https://github.com/gabriel-r100/Linux/assets/55646808/c1b5c78a-e0c7-46a4-b7bd-00aee9c45f38)

Using `ifconfig` we can update the assigned IP address on our interface with the syntax `(sudo) ifconfig <interface> <ipaddress>`.

![4-changing-ip-address](https://github.com/gabriel-r100/Linux/assets/55646808/2ffa06b7-38f8-4692-a9de-53f932a54ea8)

The MAC address can also be updated by:<br>
<br>
First shutting down the interface with `(sudo) ifconfig <interface> down`.<br>
Then updating the MAC address with `(sudo) ifconfig <interface> hw ether <macaddress>`<br>
Lastly, we need to re-enable the interface with `(sudo) ifconfig <interface> up`<br>

![5-changing-mac-address](https://github.com/gabriel-r100/Linux/assets/55646808/f230dcfc-f04a-49e0-a816-3d52f772e0e2)

If we ever need to renew our lease, similar to Windows' `ipconfig /renew`, we can use the `dhclient <interface>` command.

<h3>DNS</h3>
The command `dig` can help us find the IP address of websites, similar to Window's `nslookup`.

![7-dig-google](https://github.com/gabriel-r100/Linux/assets/55646808/082912a2-c339-4ba2-9d0b-cb2d1b2ec093)

We can also modify the DNS server by modifying the DNS configurations stored at `/etc/resolv.conf`<br>
In my Kali Linux VM's case, my DNS server is pointing to 192.168.1.1 (home router).<br>

![8-dns-configuration](https://github.com/gabriel-r100/Linux/assets/55646808/c3795916-e6c0-424a-ae2b-86bd5948088f)

We can also add our own DNS entries by modifying the file at `/etc/hosts`<br>
We can add entries with the syntax `<ipaddress> [TAB] <FQDN>`

![9-dns-entries](https://github.com/gabriel-r100/Linux/assets/55646808/e910f963-c29c-4d14-8543-a00ec5c305ca)

</details>

`ifconfig`, `iwconfig`, `ip address`, `dhclient`, `dig`




<details><summary><h2>Adding, Updating, and Removing Software</h2></summary>

Linux doesn't always have a GUI like windows, we will still need to be able to download, install, update, and remove software from our system.<br>
`apt-get` can be used in combination with several keywords to perform these functions. (`apt` is also available but has a bit less functionality)<br>
<br>
We can search our repository for programs with the command `apt-cache search <keyword>`

![1-apt-cache-search](https://github.com/gabriel-r100/Linux/assets/55646808/541d6532-d06a-4d07-b560-ff7ae993ed67)

We can install programs in our using the `apt-get install <program_name>`<br>
<br>
We can remove programs using `apt-get remove <program_name>`<br>
Alternatively, the `apt-get purge <program_name>` will remove the software **and** it's configuration file.<br>
We can add on `apt-get autoremove <program_name>` to remove any dependencies installed with the program.<br>
<br>
We can also update our installed programs using the `apt-get update` command.<br>
This will update all out of date software in our repository.<br>

If our repository doesn't have the program we are looking for, we can add to our sources list located at `etc/apt/sources.list`
Alternatively, we can clone a program from github using the command `git clone <github_url>`, it will download it to our system.

</details>

`apt-get install`, `apt-get remove`, `apt-cache search`, `apt-get purge`, `apt autoremove`, `apt-get update`, `/etc/apt/sources.list`, `git clone`




<details><summary><h2>Process Management</h2></summary>

Linux has hundreds, sometimes thousands, of processes running at the same time.<br>
We may need to view what processes are running and stop certain ones as well.<br>

We can use the `ps` command to view what processes are active. `pid` is the process ID which is used to work with processes.<br>

![1-ps](https://github.com/gabriel-r100/Linux/assets/55646808/79a32847-f3d6-4c6f-973a-22c44b98bf0d)

We can view all processes running for all users with the `ps aux` command, this will output a lot more processes. If you are looking for a specific process, we can use the `grep` command to filter output.<br>

![2-ps-aux](https://github.com/gabriel-r100/Linux/assets/55646808/4054daf7-02c3-47dc-b50d-f5c57eaf8716)

`ps` will take snapshots of process, we can view processes and the compute they are using with the `top` command which refreshes every 3 seconds.<br>

![3-top](https://github.com/gabriel-r100/Linux/assets/55646808/2726cd84-759d-4833-a02e-6ffa82b1c580)

We can also use the `nice` command to prioritize processes.<br>
The higher the value, the "nicer" you are being meaning the process will be less prioritized.<br>

![4-nice-spectrum](https://github.com/gabriel-r100/Linux/assets/55646808/bda22def-da63-405b-a84b-46416f6d960e)

If a `nice` level has been defined, we can use the `renice` command to update the value. It will also require the process ID (PID).<br>
**Any user can lower priority, only root user can increase past 0**<br>
<br>
We can use the `kill` command to end processes whether they are consuming too many resources or causes issues.<br>
There are 64 kill signals, below are commonly used ones.<br>

    # This will restart a process
    kill -1 <PID>
    # This will end the process
    kill -9 <PID>

![5-kill-table](https://github.com/gabriel-r100/Linux/assets/55646808/e5f07ad0-c72c-4ea0-8929-2802f81b81f7)

We can also kill from the `top` utility by pressing `k` and entering the PID of the process we want to terminate.<br>

![6-kill-via-top](https://github.com/gabriel-r100/Linux/assets/55646808/7f93d708-ffa2-4c73-ae81-fd918c75e216)

We can run process in the background by adding an ampersand when calling for the process: `vim test.txt &`<br>
We can bring it to the foreground withe the `fg` command plus it's PID: `fd <PID>`<br>
<br>

We can also schedule processes with the `at` and `crond` command.

</details>

`ps`, `pid`, `ps aux`, `top`, `nice`, `renice`, `kill`, `&`, `fg`, `at`, `crond`




<details><summary><h2>Shell/Environment Variables and Adding New Tools</h2></summary>

There are two types of variables:
  - Shell variables exist only within the shell they are created
  - Environment variables (aka process-wide variables) change how the system looks, acts, and feels.

Shell variables can be declared and set on the terminal

    VARIABLE="My variable"

We can use the `unset` command to free the variable created, this variable will also disappear once the shell is closed.

    unset VARIABLE

We can view our environment variables using the `env` command. Environment variables will be in all capital letters

![1-env](https://github.com/gabriel-r100/Linux/assets/55646808/f310b421-bbca-4a07-b635-20b947274468)

We can view all environment variables using the `set` command. (This will include shell variables, local variables, and shell functions.)<br>
The output will be very long, so it is recommended to pair with `more` or `less` to see one page at a time. Use `grep` if you know the variable you are looking for.<br>

![2-set](https://github.com/gabriel-r100/Linux/assets/55646808/da6e93c0-4d4d-47c5-8069-0aa3500ca96c)

The command `set | grep HISTSIZE` will find the variable that determines how many commands will go into our history. (Accessed with up arrows)<br>

![3-HISTSIZE](https://github.com/gabriel-r100/Linux/assets/55646808/4a65c35b-3131-4f55-9bee-d30614584a45)

We can change this to 0 to have our shell remember no previous commands

    HISTSIZE=0

When changing variables, it's a good idea to save the previous value.

    echo $HISTSIZE > ~valueofHISTSIZE.txt

When we make these changes, they will revert to defaults once the shell is terminated.<br>
To make the changes permenant, we need to use the `export` command

![7-exporting-HISTSIZE](https://github.com/gabriel-r100/Linux/assets/55646808/2b9e024b-8832-4110-8403-69f3a0bf9658)

We can also change the prompt that our shell provides as the variable that stores the value is `PS1`.<br>
On my Debian system, the default terminal prompt is `gabriel@Debian12:~`<br>
`gabriel` is the user, which can be added with the `\u`.<br>
`Debian12` is the host name, which can be added with `\h`.<br>
`:~` is the current directory, which can be added with `\w`.<br>

We can make our Linux terminal prompt look like Windows by entering `PS1='C:\w'

![9-windows-prompt-on-linux](https://github.com/gabriel-r100/Linux/assets/55646808/0c31237a-3946-4b17-b822-baa5698cd0a1)

<h3>New Tools</h3>

Once we install new tools we want to be able to use commands associated with them.<br>
By default, Linux will check a few directories for valid commands to execute.<br>
The directories it will check can be found in the `PATH` variable.<br>

![10-PATH](https://github.com/gabriel-r100/Linux/assets/55646808/415ee0e2-6b4f-481f-b9a4-1c6c6fe233e0)

When we download new tools that enable new commands, we need to **append** the directory to the `PATH` variable.<br>
**If we replace the value with the new directory, only the new directory commands will work. Always append, not replace**<br>

    # This will make PATH equal to the current value of PATH
    PATH=$PATH
    # This will append a new directory to the existing value of PATH
    PATH=$PATH:/root/newtool


</details>

`env`, `set`, `HISTSIZE`, `export`, shell prompt, adding commands (`bin/sbin`)




<details><summary><h2>Compressing and Archiving Files</h2></summary>

Compression is used to make data smaller.<br>
There are two types of compression:<br>

- Lossy compression provides bigger difference (more compression) at the cost of integrity.
  - Examples would be .mp3, .mp4, .jpg
- Lossless compression upholds integrity but compresses less.

<details><summary>Tarring Files Together Prior to Compression</summary>

We can also combine files into an archive (tarring) to make transporting easier.<br>
Once combined, it is referred to as a archive, tar file, or tarball.<br>

    tar -cvf <tar_file_name>.tar <file1> <file2> <file3>
  - `-c` signals tar command to create
  - `-v` signals for verbose, it will lists the files that are tarred
  - `-f` signals what the file name will be
<br>

    tar -cvf HackersArise.tar hackerarise1 hackerarise2 hackerarise3

We can also see what files are within a tar file<br>

    tar -tvf <tar_file_name>.tar
  - `-t` signals to list the contents
  - `-v` signals for verbose output
  - `-f` signals that we will name the file we are interested in
<br>

    tar -tvf HackersArise.tar

Lastly, we can extract the files within the tar file<br>

    tar -xvf <tar_file_name>.tar
  - `-x` signals to extract
  - `-v` signals for verbose output
  - `-f` signals that we will name the file we are interested in
<br>

    tar -xvf HackersArise.tar
    
</details>
<br>

<details><summary>Compressing and Decompressing Tarred Files</summary>

Once we have combined our files into a single tar file, we can use three different methods of compression to shrink the file size.

We can use the `gzip` compression method which will create `.tar.gz` or `.tgz` files.<br>

    gzip HackersArise.*

This will use the `gzip` command on any file that begins with `HackersArise.` which will include our tar file.<br>
We can similarly decompress the file using the `gunzip` command.<br>

    gunzip HackersArise.*

<br>
We can use the `bzip2` compression method to create `.tar.bz2` files.<br>
`bzip2` is slower but offers the most compression of the three options.<br>

    bzip2 HackersArise.*

We can decompress with the `bunzip2` command.<br>

  bunzip2 HackersArise.*
<br>
We can use the `compress` compression method to create `.tar.z` files.<br>
`compress` is the fastest but offers the least amount of compression.<br>

    compress HackersArise.*

We can decompress with the `uncompress` command. We can also use the `gunzip` command on files that were compressed using `compress`.

    uncompress HackersArise.*
    gunzip HackersArise.*
  
</details>



</details>

`tar`, `gzip`, `gunzip`, `bzip2`, `bunzip2`, `compress`, `uncompress`, `dd`




<details><summary><h2>Creating Copies of Storage Devices</h2></summary>

We can create a bit-by-bit copy of a storage device with the use of the `dd` command.<br>
This command is very slow but is useful for creating a copy for forensic investigators.<br>

    dd if=<input_file> of=<name_of_copy>
    dd if=/dev/sdb of=/root/flashcopy

`if` will designate what will be copied<br>
`of` designates what the name of the file will be, additionally you can specify where we will place the file.<br>
`noerror`is a helpful option to add if you would like the copy to continue regardless of errors.<br>
`bs` allows you to determine the block size while copying, it can speed up the process of copying but errors are more impactful. (default block size is 512 bytes)<br>

    dd if=/dev/sdb of=/root/flashcopy bs=4096 conv=noerror

</details>

`dd`




<h2>Kali Linux Tools</h2>

<details><summary><h3>Possible Privilege Escalation</h3></summary>

A bad actor can find our sudo file using a search command of `find / -user root -perm -4000`<br>
This will return files that are owned by the root user with SUID permissions set.<br>
This means that if a user can control an application that needs root permissions, they can use those permissions to have root access over a system.<br>

![9999-finding-root-files-with-SUID](https://github.com/gabriel-r100/Linux/assets/55646808/7a37e9f7-85dc-4390-9fe0-61a5bc01d37f)


</details>
