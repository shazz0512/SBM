<h1 align="center">RAID 0</h1>

### To implement this follow config below

* 1 BOOT PARTITION
* ADD 2 HDD OF ANY SIZE




### To Check if our harddisk are mounted or not 

    lsblk
    



### Install mdadm to create raid

    yum install mdadm -y

    
### Create Raid-0 with command below

    mdadm  --create --verbose /dev/md0 --level=0 --raid-devices=2 /dev/sdb /dev/sdc



### To check if it's created or not

    cat /proc/mdstat


### You can examine drives as well

    mdadm --examine /dev/sdb

### List Blocks

    lsblk

### Create new partition
    
    fdisk /dev/md0


### Make filesystem

    mkfs.ext4 /dev/md0p1

### Mounting the created partition 

    mkdir /mnt/raid0
    mount /dev/md0p1 /mnt/raid0

### Check for partition folder if it's mounted or not

    cd /mnt/raid0
    ll


### Check for partitions and used space by command below

    df- h


### Creating a file so that we can see the space usage

    dd if=/dev/zero of=500mb.file bs=1024 count=502400
 

### And now we can see changes

    df -h


### To unmount the raid partition

    umount /mnt/raid0
    
### check for partitions ,it'll be missing from list 

    df -h 



### Stop the raid 0 partition

    mdadm --stop /dev/md0


