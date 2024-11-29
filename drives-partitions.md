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
1. First create new partition table on a new drive
```sh
sudo gdisk /dev/xvdb
```
in submenu use option `o` - create a new empty GUID partition table (GPT)  
On a next step create new partitions with `n` for example 5GB partition as end sector of a new partition use +5G.  
Last step is option `w` to write the partition table

2. Second step is to format partitions.
Use tool `mke2fs` or `mkfs`. Usage:
```sh
sudo mkfs.ext4 /dev/xvdb1
```
or
```sh
sudo mke2fs -t ext4 /dev/xvdb1
```

==**Important!**==

After changing partition size or adding/changing partitions use tool partprobe with option `s` to let the kernel know about partition change
```sh
sudo partprobe -s
```


--------------------


## Using LVM with xfs filesystem

First install lvm2 and xfsprogs.
$ sudo yum install lvm2 xfsprogs

Let's say we have 2 extra drives /dev/xvdb and /dev/xvdc, verify those drives:
$ sudo fdisk -l

After that if there is a partition with data use wipefs:

$ sudo wipefs -a /dev/xvdb and again for second drive
$ sudo wipefs -a /dev/xvdc

Now create volumes in this order: Physical Volume PV, Volume Group VG and create Logical Volumes LV

$ sudo pvcreate /dev/xvdb /dev/xvdc
After that check Phisical Volume with pvs
$ sudo pvs
Next step is to create a Volume Group VG which combines the physical volumes into a volume group. Use vgcreate:
$ sudo vgcreate vg_data /dev/xvdb /dev/xvdc
And check it with vgs and again pvs:
$ sudo vgs and again $ sudo pvs

Now last step is to create Logical Volumes using all available drive space:
$ sudo lvcreate -n lv_data -l 100%FREE vg_data
And verify Logical Volume with lvs:
$ sudo lvs

Now create xfs filesystem:
$ sudo mkfs.xfs /dev/vg_data/lv_data 

To check filesystem on LVM use xfs_info:
$ sudo xfs_info /dev/mapper/vg_data-lv_data

Create a mount point and mount Filesystem:
$ sudo mkdir -p /mnt/data
$ sudo mount -t xfs /dev/vg_data/lv_data /mnt/data


To extend Logical volume by adding another drive named /dev/xvdd:
Create another Phisical Volume PV and check after creation with $ sudo pvs
$ sudo pvcreate /dev/xvdd

Now extend Volume group for new PV:
$ sudo vgextend vg_data /dev/xvdd

Now check free space in LV:
$ sudo vgdisplay vg_data

And last step to extend the Logical Volume lv_data to use all the free space in Volume Group vg_data:
$ sudo lvextend -l +100%FREE /dev/vg_data/lv_data


Resize the Filesystemon extended LVM
Since it’s XFS filesystem, it can grow it online without unmounting.

$ sudo xfs_growfs /mnt/data

And last to check everything use df -h

Summary of Commands:
sudo pvcreate /dev/xvdd
sudo vgextend vg_data /dev/xvdd
sudo lvextend -l +100%FREE /dev/vg_data/lv_data
sudo xfs_growfs /mnt/data


## same for ext4 filesystem

Certainly! When using an ext4 filesystem instead of XFS, the steps to extend the LVM remain largely the same until you reach the filesystem resizing step. Here's how you would adjust the process:

1. Prepare the New Disk
Verify the New Disk:

lsblk
Initialize the Physical Volume:

sudo pvcreate /dev/xvdd
2. Extend the Volume Group
sudo vgextend vg_data /dev/xvdd
3. Extend the Logical Volume
Extend the Logical Volume to Use All Free Space:

sudo lvextend -l +100%FREE /dev/vg_data/lv_data
4. Resize the Filesystem
Since you're using an ext4 filesystem, you can typically resize it online without unmounting, provided your kernel supports online resizing (most modern kernels do).

Resize the ext4 Filesystem:

sudo resize2fs /dev/vg_data/lv_data
Note: If your system does not support online resizing for ext4, you will need to unmount the filesystem first:

sudo umount /mnt/data
sudo resize2fs /dev/vg_data/lv_data
sudo mount /dev/vg_data/lv_data /mnt/data
5. Verify the Changes
Check the Logical Volume Size:

sudo lvdisplay /dev/vg_data/lv_data
Check the Filesystem Size:

df -h /mnt/data
You should now see that the size of /mnt/data has increased accordingly.

Summary of Commands for ext4 Filesystem:
sudo pvcreate /dev/xvdd
sudo vgextend vg_data /dev/xvdd
sudo lvextend -l +100%FREE /dev/vg_data/lv_data
sudo resize2fs /dev/vg_data/lv_data

edit til here

## Swap partitions and swap files

### Swap partition

Setting up swap partition can be done with `fdisk` or `gdisk` code is 82 and 8200

### Swap file

First create a file that will be used as swap space:
```sh
sudo dd if=/dev/zero of=swapfile bs=1M count=1024
```
Change permission on a file to `0600` with `chmod 0600 /path/to/swapfile`

### Make swap partition and swap file usable

#### Using swap partition:

```sh
sudo mkswap /dev/sdb1
```
and now to use swap partition:

```sh
sudo swapon /dev/sdb1
```
#### Using swap files

procedure is the same but instead a device now use a file:

```sh
sudo mkswap /path/to/swapfile
```
and now to use swap partition:

```sh
sudo swapon /path/to/swapfile
```
