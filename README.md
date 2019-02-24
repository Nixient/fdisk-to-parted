# Fdisk to Parted Conversion

I'm used to fdisk, so I'm going to try to document some equivalent commands and notes to help me convert since I'm working with larger drives.

## Table of Contents

1. Basic Commands
    1. Show All Disks
    2. Open Specific Disk
2. Commands Inside
3. Specifics
    1. Creating 10GB ext4 Partition on /dev/sda



## 1. Basic Commands

### 1.1. Show Disks

```bash
# fdisk
sudo fdisk -l

# parted
sudo parted -l
```

### 1.2. Open a Disk

```bash
# fdisk
sudo fdisk /dev/sdX

# parted
sudo parted /dev/sdX
```

## 2. Commands Inside

These are command that are ran once we are inside parted and have selected a disk.

### 2.1. Show Partitions

These commands show the partitions on the loaded disk

```bash
# fdisk
p

# parted
p
```

### 2.2. Deleting Partitions

```bash
# fdisk
d

# parted
rm NUMBER
```

### 2.3. Create Partition and Set Type

```bash
# fdisk
n
    # Selecting sizing
t
    # Enter Type Number

# parted
mkpart PART-TYPE [FS-TYPE] START END
```

## 3. Specifics

### 3.1. Creating 10GB ext4 Partition on /dev/sda

```bash
# Locate the disk
sudo parted -l

# Open the Disk
$udo parted /dev/sda

### You should now have a "(parted)" prompt

# Show the Partitions to ensure there are none
p

> Model: Seagate Expansion Desk (scsi)
> Disk /dev/sda: 2000GB
> Sector size (logical/physical): 512B/512B
> Partition Table: loop
> Disk Flags: 
> 
> Number  Start  End  Size  File system  Flags

# Create GPT Table
mktable gpt

# Create the partition


```