# Mounting with Systemd

## Mounting Disks with Systemd units.

Mount units have to be created as root in `/etc/systemd/system` and need to have `.mount` extension.
Correct unit file name for mountpoint /mnt/disk1 is `mnt-disk1.mount`. So a name of a mountpoint has to be between `mnt-` and `.mount`

Inside a mount unit file

```
[Unit]
Description=Mount xvdb1 on disk1

[Mount]
What= /dev/disk/by-uuid/66cf9498-4b81-4adf-9603-77e75251ad4e
Where=/mnt/disk1
Type=xfs
Options=defaults

[Install]
WantedBy=multi-user.target
WantedBy=graphical.target
```
`WantedBy=graphical.target` is not needed because `multi-user.target` starte before it. But for a peace of mind can be included.

After file is created do the 3 steps:
- reload daemon:
- enable mount
- start mount
```sh
sudo systemctl daemon-reload
sudo systemctl enable mnt-disk1.mount
sudo systemctl start mnt-disk1.mount
```

### To verify mounts:  

To verify if everything works use `mount` or `df`
```sh
mount | grep '/mnt/disk'
df -h
```
