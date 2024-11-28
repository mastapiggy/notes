# Drives, partitions and filesystem

## Listing block devices on a system

To see drives and partitions and mountpoints:
```bash
sudo lsblk
```
To see Filesystem avaliable, used, filesystem type and UUID use -f option: `sudo lsblk -f`

To see Label names, boot partition, UUID, FS Type and Partition UUID use:

```sh
sudo blkid
```

## Steps to set up new drive on a system with mounting but without editing fstab (not persistent)

Can use `fdisk` for drives with MBR partition Table or `gdisk` with GTP partition table

### Using `gdisk`
First create new partition table on a new drive
```sh
sudo gdisk /dev/xvdb
```
in submenu use option `o` - create a new empty GUID partition table (GPT)
On a next step create new partitions with `n` for example 5GB partition as end sector of a new partition use +5G.  
Last step is option `w` to write the partition table
