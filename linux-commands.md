# Linux commands

## List of commands in this file:

- find
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

