# File /etc/fstab

Structure of a `/etc/fstab` file on a linux system:

`FILESYSTEM MOUNTPOINT TYPE OPTIONS DUMP PASS`

## Explanation of the 4th field - OPTIONS

### List of mount options:

- defaults
- rw
- ro
- sync
- async
- auto
- noauto
- dev
- nodev
- exec
- noexec
- suid
- nosuid
- user
- nouser
- owner
- atime
- noatime
- relatime
- diratime
- nodiratime
- remount
- bind
- acl
- noacl
- errors=remount-ro
- errors=continue
- errors=panic
- barrier=0
- barrier=1
- nobarrier
- data=ordered
- data=writeback
- data=journal
- commit=
- discard
- nofail
- x-systemd.automount
- x-systemd.device-timeout=
- x-systemd.idle-timeout=
- x-systemd.mount-timeout=
- x-systemd.requires=
- x-systemd.after=
- mode=
- uid=
- gid=
- umask=
- iocharset=
- fmask=
- dmask=

### Explanation of Each Option:

- defaults
Description: Uses the default mount options: rw, suid, dev, exec, auto, nouser, and async.
Usage: Commonly used when no specific options are needed.
2. rw
Description: Mounts the filesystem in read-write mode, allowing both read and write operations.
Usage: Default behavior; specify if you want to ensure the filesystem is writable.
3. ro
Description: Mounts the filesystem in read-only mode, disallowing write operations.
Usage: Useful for mounting filesystems that should not be modified, such as CD-ROMs or backup images.
4. sync
Description: All input/output operations are done synchronously, meaning write operations wait until the data is physically written to the disk.
Usage: Can improve data integrity but may reduce performance.
5. async
Description: All input/output operations are done asynchronously, allowing write operations to be cached.
Usage: Improves performance but may risk data loss in the event of a crash.
6. auto
Description: The filesystem will be automatically mounted at boot time or when the mount -a command is issued.
Usage: Default behavior; use when you want the filesystem to mount automatically.
7. noauto
Description: The filesystem will not be automatically mounted at boot or with mount -a.
Usage: Use for filesystems that should be mounted manually.
8. dev
Description: Interprets character or block special devices on the filesystem.
Usage: Allows device files (e.g., /dev/sda) to function properly.
9. nodev
Description: Does not interpret character or block special devices.
Usage: Enhances security by preventing device files on the filesystem from being used.
10. exec
Description: Permits the execution of binaries on the mounted filesystem.
Usage: Default behavior; necessary for filesystems containing executable programs.
11. noexec
Description: Does not allow the execution of binaries on the filesystem.
Usage: Enhances security by preventing execution of potentially malicious binaries.
12. suid
Description: Honors set-user-ID and set-group-ID bits, allowing executables to run with the permissions of the file owner.
Usage: Default behavior; necessary for certain system utilities.
13. nosuid
Description: Does not honor set-user-ID and set-group-ID bits.
Usage: Enhances security by preventing privilege escalation.
14. user
Description: Allows an ordinary user to mount and unmount the filesystem.
Usage: The user who mounts the filesystem becomes its owner.
15. nouser
Description: Only the root user can mount the filesystem.
Usage: Default behavior; restricts mounting to administrative users.
16. owner
Description: Allows the device owner to mount the filesystem.
Usage: Useful for removable media where the device file is owned by the user.
17. atime
Description: Updates inode access times on each access.
Usage: Necessary for certain applications that rely on accurate access times.
18. noatime
Description: Does not update inode access times, reducing disk writes.
Usage: Improves performance, especially on SSDs; may be incompatible with some applications.
19. relatime
Description: Updates inode access times relative to modification time.
Usage: Balances performance and compatibility by reducing disk writes while keeping reasonably accurate access times.
20. diratime
Description: Updates directory inode access times.
Usage: Default behavior; necessary for applications that rely on directory access times.
21. nodiratime
Description: Does not update directory inode access times.
Usage: Improves performance by reducing writes for directory accesses.
22. remount
Description: Remounts an already-mounted filesystem, typically to change its mount options without unmounting.
Usage: Used in conjunction with mount -o remount.
23. bind
Description: Binds a mount point to another location, making the same content accessible from multiple paths.
Usage: Useful for making directories available in multiple locations.
24. acl
Description: Enables POSIX Access Control Lists, allowing more granular permissions.
Usage: Necessary when fine-grained permissions are required beyond the standard Unix permissions.
25. noacl
Description: Disables POSIX Access Control Lists.
Usage: Default behavior; specify to ensure ACLs are not used.
26. errors=remount-ro
Description: Remounts the filesystem as read-only upon detecting errors.
Usage: Enhances data integrity by preventing further writes to a corrupted filesystem.
27. errors=continue
Description: Continues operations despite errors.
Usage: May risk data integrity; generally not recommended.
28. errors=panic
Description: Causes a kernel panic when errors are encountered.
Usage: Useful in environments where data integrity is critical.
29. barrier=0
Description: Disables write barriers, which can improve performance but may risk data integrity during power failures.
Usage: Use cautiously; suitable for systems with battery-backed storage.
30. barrier=1
Description: Enables write barriers, ensuring that write operations are properly ordered.
Usage: Default behavior; enhances data integrity.
31. nobarrier
Description: Equivalent to barrier=0.
Usage: Alternative syntax for disabling write barriers.
32. data=ordered
Description: Journaling mode where data is written to disk before the metadata is committed.
Usage: Default mode for ext4; balances performance and data integrity.
33. data=writeback
Description: Journaling mode where metadata is journaled, but data is not, leading to potential data corruption on crashes.
Usage: Improves performance at the risk of data integrity.
34. data=journal
Description: Journaling mode where both data and metadata are journaled, providing the highest level of data integrity.
Usage: Reduces performance; suitable for critical data.
35. commit=
Description: Specifies the maximum interval (in seconds) between when data is written to the journal and when it is committed to the filesystem.
Usage: Adjusts the frequency of disk writes; default is typically 5 seconds (e.g., commit=30).
36. discard
Description: Enables TRIM support for SSDs, allowing the filesystem to inform the storage device about blocks no longer in use.
Usage: Enhances SSD longevity and performance.
37. nofail
Description: The system will continue the boot process even if the filesystem fails to mount.
Usage: Useful for non-critical filesystems or removable media.
38. x-systemd.automount
Description: Instructs systemd to automatically mount the filesystem when it is first accessed.
Usage: Improves boot time by deferring mounting until necessary.
39. x-systemd.device-timeout=
Description: Specifies the time systemd should wait for the device to become available.
Usage: Useful for network filesystems or devices that may be slow to initialize (e.g., x-systemd.device-timeout=60).
40. x-systemd.idle-timeout=
Description: Unmounts the filesystem after a specified period of inactivity.
Usage: Helps free up resources by unmounting unused filesystems (e.g., x-systemd.idle-timeout=30s).
41. x-systemd.mount-timeout=
Description: Specifies how long systemd waits for the mount operation to complete.
Usage: Adjusts mount timeout to prevent long waits during boot (e.g., x-systemd.mount-timeout=30s).
42. x-systemd.requires=
Description: Specifies that the mount unit depends on another systemd unit.
Usage: Ensures that dependent units are started before mounting (e.g., x-systemd.requires=network-online.target).
43. x-systemd.after=
Description: Specifies that the mount unit should be started after another systemd unit.
Usage: Controls the ordering of unit startup (e.g., x-systemd.after=network-online.target).
44. mode=
Description: Sets the permissions (in octal) for all files and directories on the filesystem (e.g., mode=0777).
Usage: Useful for filesystems that do not support Unix permissions, like vfat.
45. uid=
Description: Sets the owner user ID for all files and directories.
Usage: Ensures that all files appear to be owned by a specific user (e.g., uid=1000).
46. gid=
Description: Sets the owner group ID for all files and directories.
Usage: Ensures that all files appear to be owned by a specific group (e.g., gid=1000).
47. umask=
Description: Sets the file mode creation mask, determining the default permissions for new files and directories.
Usage: Controls the access permissions on filesystems without native Unix permissions (e.g., umask=022).
48. iocharset=
Description: Specifies the character set used to encode file names.
Usage: Necessary when dealing with non-ASCII file names on filesystems like vfat or ntfs (e.g., iocharset=utf8).
49. fmask=
Description: Sets the file permission mask for files.
Usage: Similar to umask, but applies only to files (e.g., fmask=133).
50. dmask=
Description: Sets the directory permission mask for directories.
Usage: Similar to umask, but applies only to directories (e.g., dmask=022).
