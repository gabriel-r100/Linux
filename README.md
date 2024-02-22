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




<h2>Kali Linux Tools</h2>

