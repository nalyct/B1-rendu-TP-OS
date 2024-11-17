# TP4 : Safé d partission

**TP autour du partitionnement !**
## Sommaire

- [TP4 : Safé d partission](#tp4--safé-d-partission)
  - [Sommaire](#sommaire)
  - [3. Vérification](#3-vérification)
  - [4. Taille et inodes](#4-taille-et-inodes)
- [II. Partitioning](#ii-partitioning)
  - [1. d disk partou](#1-d-disk-partou)
  - [2. Grow !](#2-grow-)
  - [3. Montage automatique](#3-montage-automatique)
  - [4. Bonus : options de montage](#4-bonus--options-de-montage)

## 3. Vérification

🌞 **Lister les périphériques de stockage branchés à la machine**
```
abc@abc:~$ sudo lsblk
[sudo] password for abc:
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda           8:0    0   20G  0 disk
└─sda1        8:1    0   20G  0 part
  ├─ok-root 254:0    0  9.3G  0 lvm  /
  ├─ok-swap 254:1    0  1.9G  0 lvm  [SWAP]
  ├─ok-home 254:2    0  1.9G  0 lvm  /home
  └─ok-var  254:3    0  2.8G  0 lvm  /var
sr0          11:0    1 1024M  0 rom
```


🌞 **Lister les partitions en cours d'utilisation**
```
abc@abc:~$ df -h
Filesystem           Size  Used Avail Use% Mounted on
udev                 448M     0  448M   0% /dev
tmpfs                 97M  968K   96M   1% /run
/dev/mapper/ok-root  9.1G  4.0G  4.7G  46% /
tmpfs                481M     0  481M   0% /dev/shm
tmpfs                5.0M     0  5.0M   0% /run/lock
/dev/mapper/ok-home  1.8G  1.6M  1.7G   1% /home
/dev/mapper/ok-var   2.7G  352M  2.2G  14% /var
tmpfs                 97M   52K   97M   1% /run/user/1000
```


## 4. Taille et inodes

🌞 **Lister la quantité d'*inodes* disponibles sur chaque partition**
```
abc@abc:~$ df -i
Filesystem          Inodes  IUsed  IFree IUse% Mounted on
udev                114610    419 114191    1% /dev
tmpfs               122980    685 122295    1% /run
/dev/mapper/ok-root 610800 117542 493258   20% /
tmpfs               122980      1 122979    1% /dev/shm
tmpfs               122980      3 122977    1% /run/lock
/dev/mapper/ok-home 121920     83 121837    1% /home
/dev/mapper/ok-var  183264   6394 176870    4% /var
tmpfs                24596     68  24528    1% /run/user/1000
```

🌞 **Déterminer la taille (avec `du`) et l'*inode* (avec `ls`) de chacun des fichiers suivants :**
```
abc@abc:~$ du -h /boot/vmlinuz-6.1.0-27-amd64  && ls -i /boot/vmlinuz-6.1.0-27-amd64
7.9M    /boot/vmlinuz-6.1.0-27-amd64
130319 /boot/vmlinuz-6.1.0-27-amd64
```

# II. Partitioning

## 1. d disk partou


🌞 **Repérer le nom des nouveaux disques**
```
abc@abc:~$ lsblk
NAME        MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda           8:0    0   20G  0 disk
└─sda1        8:1    0   20G  0 part
  ├─ok-root 254:0    0  9.3G  0 lvm  /
  ├─ok-swap 254:1    0  1.9G  0 lvm  [SWAP]
  ├─ok-home 254:2    0  1.9G  0 lvm  /home
  └─ok-var  254:3    0  2.8G  0 lvm  /var
sdb           8:16   0   10G  0 disk
sdc           8:32   0   10G  0 disk
sr0          11:0    1 1024M  0 rom
```

🌞 **Ajouter ces deux disques comme des PV LVM**
```
abc@abc:~$ sudo pvcreate /dev/sdb
[sudo] password for abc:
  Physical volume "/dev/sdb" successfully created.
abc@abc:~$ sudo pvcreate /dev/sdc
  Physical volume "/dev/sdc" successfully created.
  ```
🌞 **Créer un VG nommé `cat`**
```
abc@abc:~$ sudo vgcreate cat /dev/sdb /dev/sdc
  Volume group "cat" successfully created
```


🌞 **Créer un LV nommé `meoooow`**
```
abc@abc:~$ sudo lvcreate -L 3G -n meoooow cat
  Logical volume "meoooow" created.
  ```
  ```
  abc@abc:~$ lsblk
NAME          MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
sda             8:0    0   20G  0 disk
└─sda1          8:1    0   20G  0 part
  ├─ok-root   254:0    0  9.3G  0 lvm  /
  ├─ok-swap   254:1    0  1.9G  0 lvm  [SWAP]
  ├─ok-home   254:2    0  1.9G  0 lvm  /home
  └─ok-var    254:3    0  2.8G  0 lvm  /var
sdb             8:16   0   10G  0 disk
└─cat-meoooow 254:4    0    3G  0 lvm
sdc             8:32   0   10G  0 disk
sr0            11:0    1 1024M  0 rom
```


🌞 **Formater la partition (le LV) en autre chose que ext4**
```
abc@abc:~$ sudo apt install btrfs-progs
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  liblzo2-2
Suggested packages:
  duperemove
The following NEW packages will be installed:
  btrfs-progs liblzo2-2
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 811 kB of archives.
After this operation, 4,769 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://deb.debian.org/debian bookworm/main amd64 liblzo2-2 amd64 2.10-2 [56.9 kB]
Get:2 http://deb.debian.org/debian bookworm/main amd64 btrfs-progs amd64 6.2-1+deb12u1 [754 kB]
Fetched 811 kB in 1s (1,161 kB/s)
Selecting previously unselected package liblzo2-2:amd64.
(Reading database ... 113761 files and directories currently installed.)
Preparing to unpack .../liblzo2-2_2.10-2_amd64.deb ...
Unpacking liblzo2-2:amd64 (2.10-2) ...
Selecting previously unselected package btrfs-progs.
Preparing to unpack .../btrfs-progs_6.2-1+deb12u1_amd64.deb ...
Unpacking btrfs-progs (6.2-1+deb12u1) ...
Setting up liblzo2-2:amd64 (2.10-2) ...
Setting up btrfs-progs (6.2-1+deb12u1) ...
Processing triggers for man-db (2.11.2-2) ...
Processing triggers for initramfs-tools (0.142+deb12u1) ...
update-initramfs: Generating /boot/initrd.img-6.1.0-27-amd64
Processing triggers for libc-bin (2.36-9+deb12u9) ...
abc@abc:~$ sudo mkfs.btrfs /dev/mapper/cat-meoooow
btrfs-progs v6.2
See http://btrfs.wiki.kernel.org for more information.

NOTE: several default settings have changed in version 5.15, please make sure
      this does not affect your deployments:
      - DUP for metadata (-m dup)
      - enabled no-holes (-O no-holes)
      - enabled free-space-tree (-R free-space-tree)

Label:              (null)
UUID:               c3b0326d-8c2e-448c-9c40-2b684b1bb856
Node size:          16384
Sector size:        4096
Filesystem size:    3.00GiB
Block group profiles:
  Data:             single            8.00MiB
  Metadata:         DUP             256.00MiB
  System:           DUP               8.00MiB
SSD detected:       no
Zoned device:       no
Incompat features:  extref, skinny-metadata, no-holes
Runtime features:   free-space-tree
Checksum:           crc32c
Number of devices:  1
Devices:
   ID        SIZE  PATH
    1     3.00GiB  /dev/mapper/cat-meoooow
```

🌞 **Créer le *point de montage* `/mnt/meow`**
```
abc@abc:~$ sudo mkdir /mnt/meow
abc@abc:~$ ls -ld /mnt/meow
drwxr-xr-x 2 root root 4096 Nov 17 14:01 /mnt/meow

```


🌞 **Monter la partition `meoooow` sur le point de montage que vous avez créé**
```
abc@abc:~$ sudo mount /dev/mapper/cat-meoooow /mnt/meow
```

🌞 **Vérifier avec la commande adaptée que la partition est utilisable et qu'elle fait 3G**
```
abc@abc:~$ df -h /mnt/meow
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/cat-meoooow  3.0G  5.8M  2.5G   1% /mnt/meow
abc@abc:~$
```
## 2. Grow !

🌞 **Il reste 2G sur le disque dur principal**
```
abc@abc:~$ sudo lvextend -L +2G /dev/ok/home
  Size of logical volume ok/home changed from <1.86 GiB (476 extents) to <3.86 GiB (988 extents).
  Logical volume ok/home successfully resized.
  abc@abc:~$ sudo resize2fs /dev/ok/home
resize2fs 1.47.0 (5-Feb-2023)
Filesystem at /dev/ok/home is mounted on /home; on-line resizing required
old_desc_blocks = 1, new_desc_blocks = 1
The filesystem on /dev/ok/home is now 1011712 (4k) blocks long.
  ```


🌞 **Prouvez en affichant la liste des partitions que la partition fait désormais 2G de plus**
```
abc@abc:~$ df -h /home
Filesystem           Size  Used Avail Use% Mounted on
/dev/mapper/ok-home  3.8G  1.6M  3.6G   1% /home
```


🌞 **Agrandir la partition `meoooow` pour qu'elle occupe tout l'espace libre de son VG**
```
abc@abc:~$ sudo vgs
  VG  #PV #LV #SN Attr   VSize   VFree
  cat   2   1   0 wz--n-  19.99g 16.99g
  ok    1   4   0 wz--n- <20.00g  2.17g
abc@abc:~$ sudo lvextend -l +100%FREE /dev/cat/meoooow
  Size of logical volume cat/meoooow changed from 3.00 GiB (768 extents) to 19.99 GiB (5118 extents).
  Logical volume cat/meoooow successfully resized.
  abc@abc:~$ sudo btrfs filesystem resize max /mnt/meow
Resize device id 1 (/dev/mapper/cat-meoooow) from 3.00GiB to max
abc@abc:~$ df -h
Filesystem               Size  Used Avail Use% Mounted on
udev                     448M     0  448M   0% /dev
tmpfs                     97M 1020K   96M   2% /run
/dev/mapper/ok-root      9.1G  4.0G  4.7G  46% /
tmpfs                    481M     0  481M   0% /dev/shm
tmpfs                    5.0M     0  5.0M   0% /run/lock
/dev/mapper/ok-home      3.8G  1.6M  3.6G   1% /home
/dev/mapper/ok-var       2.7G  368M  2.2G  15% /var
tmpfs                     97M   52K   97M   1% /run/user/1000
tmpfs                     97M   48K   97M   1% /run/user/108
/dev/mapper/cat-meoooow   20G  5.8M   20G   1% /mnt/meow
  ```
🌞 **Déterminer la taille de la nouvelle partition**
```
abc@abc:~$ lsblk -f
NAME          FSTYPE      FSVER    LABEL UUID                                   FSAVAIL FSUSE% MOUNTPOINTS
sda
└─sda1        LVM2_member LVM2 001       5p4Mxx-aRB1-14n5-znPx-hNrv-E4SX-YsEbdl
  ├─ok-root   ext4        1.0            73fdb08c-912b-4ec9-aed9-1ff1cace002f      4.7G    43% /
  ├─ok-swap   swap        1              38fac470-c2c8-4e82-9332-c05b94660cff                  [SWAP]
  ├─ok-home   ext4        1.0            11c123f7-681d-4d95-a708-ade43dfef8a8      3.6G     0% /home
  └─ok-var    ext4        1.0            e1f58f05-6f87-4f3b-8620-ad4309ad8e0f      2.2G    13% /var
sdb           LVM2_member LVM2 001       Biyi8r-aDI2-VlfR-S0Km-juPE-SjCt-dTVG4g
└─cat-meoooow btrfs                      c3b0326d-8c2e-448c-9c40-2b684b1bb856     19.5G     0% /mnt/meow
sdc           LVM2_member LVM2 001       erTzzU-04pK-Ghq1-q1o7-yZRH-1yKF-5ygWCR
└─cat-meoooow btrfs                      c3b0326d-8c2e-448c-9c40-2b684b1bb856     19.5G     0% /mnt/meow
sr0
```

## 3. Montage automatique


🌞 **Modifier le fichier `/etc/fstab` pour que la partition soit montée `/mnt/meow` automatiquement**
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# systemd generates mount units based on this file, see systemd.mount(5).
# Please run 'systemctl daemon-reload' after making changes here.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ok-root /               ext4    errors=remount-ro 0       1
/dev/mapper/ok-home /home           ext4    defaults        0       2
/dev/mapper/ok-var /var            ext4    defaults        0       2
/dev/mapper/ok-swap none            swap    sw              0       0
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/cat/meoooow   /mnt/meow   btrfs   defaults   0 0
```
```
abc@abc:~$ sudo mount -av
/                        : ignored
/home                    : already mounted
/var                     : already mounted
none                     : ignored
/media/cdrom0            : ignored
/mnt/meow                : already mounted
```



## 4. Bonus : options de montage



⭐ **Déterminer quelles options de montage permettrait d'améliorer le niveau de sécurité des données contenues sur une partition.**
