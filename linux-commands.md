# Linux commands

## List of commands in this file:

- find
- df


------

## Find command

Usage of the command: `find . -name '*.jpg*'` which means `find` from here`.` files or directories with . jpg in the name `'*.jpg*'` - remember to use single quore when using file globbing

### Examples

To look for a file and limit how deep find can go in a structure of a directory use `-maxdepth 2` - in this case 2 directories down the structure.  
Oposite is for `-mindepth 2`  - will start from 2 directories down and go deeper.

Find directories modified/created between 25-27 November 2024 and copy them to other directory  
bottom wersion is POSIX compliant
```sh
find . -type d -newermt '2024-11-25' ! -newermt '2024-11-27' -exec cp -rp '{}' /tmp/eff_copy/ \;
find . -type d -newermt '2024-11-25' -not -newermt '2024-11-27' -print
```

Find files ending on `.txt` and remove them

```sh
find . -type f -name '*.txt' -exec rm '{}' \;
```
