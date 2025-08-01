# Linux commands

## List of commands in this file:

- find
- sed
- df
- xargs

------

## Find command

Usage of the command: `find . -name '*.jpg*'` which means `find` from here`.` files or directories with . jpg in the name `'*.jpg*'` - remember to use single quore when using file globbing

### Examples

To look for a file and limit how deep find can go in a structure of a directory use `-maxdepth 2` - in this case 2 directories down the structure.  
Oposite is for `-mindepth 2`  - will start from 2 directories down and go deeper.

Find directories modified/created between 25-27 November 2024 and copy them to other directory  

```sh
find . -type d -newermt '2024-11-25' -not -newermt '2024-11-27' -exec cp -rp '{}' /tmp/eff_copy/ \;

find . -type d -newermt '2024-11-25' -not -newermt '2024-11-27' -print
```

Find files ending on `.txt` and remove them

```sh
find . -type f -name '*.txt' -exec rm '{}' \;
```
or use `xargs` instead of `exec`
```sh
find . -type f -name '*.txt' -print0 | xargs -0 /bin/rm -f
```
Find files and execute `file` command on every file found:
```sh
find . -type f -exec file '{}' \;
```
Find only files in a directory and move them to Dir1: "\"  at the end of exec command is to escape ";" which is needed to close exec command.
```sh
find . -type f -exec mv {} Dir1/ \;
```


## SUDO config - 

LPIC 1 102 page **523!**

The /etc/sudoers File
sudo's main configuration file is /etc/sudoers(there is also the /etc/sudoers.d directory). That is
the place where users' sudo privileges are determined. In other words, here you will specify who can
run what commands as what users on what machines — as well as other settings. The syntax used is
as follows:
carol@debian:~$ sudo less /etc/sudoers
(...)
# User privilege specification
root    ALL=(ALL:ALL) ALL
# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL
(...)

Finish correction

## Sed

To subsidize one character to another use:  
s - subsidize, g - at the end means global. Otherwise it will only work for 1st instance of the pattern.

```sh
sed 's/old/new/g' file.txt
```

To remove a pattern:  
d - is for delete
```sh
sed '/---/d' file.txt
```

## Xargs command

Build and execute command lines from standard input

A file `hostnames.txt` contains on each line domain name:  
```
example.com
example.net
example.org
google.com
google.pl
```
We want to check every single line of this file with `host` command with arguments `-t A` for a type of A record over the google dns server:
Option `-I` specifies a placeholder `{}`to control where to put a line of input in a command  
```sh
cat hostnames.txt | xargs -I{} host -t A {} 8.8.8.8
```
To speed up and run 4 `host` commands at once use `-P`, example:  
```sh
cat hostnames.txt | xargs -I{} -P4 host -t A {} 8.8.8.8
```  
If we want to have only last line of output from `host` command we need to tell xargs to run shell for every line from the file as an input and that needs to be piped to `tail` command
```sh
cat hostnames.txt | xargs -I{} -P4 sh -c "host -t A {} 8.8.8.8 | tail -n1"
```
























