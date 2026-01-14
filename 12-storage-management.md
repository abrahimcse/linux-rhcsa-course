# 12 - Storage Management in Linux (RHEL)

## Chapter Overview

Storage management is a **core responsibility** of a Linux administrator. Servers use disks to store:

* Operating system
* Applications
* Databases
* User data

In this chapter, you will learn **basic storage concepts** step by step, assuming you are a **complete beginner**.

---

## What Is Storage?

**Storage** means the place where data is saved permanently.

Examples:

* Hard Disk (HDD)
* Solid State Drive (SSD)
* Virtual Disk (VM disk)

Linux treats storage devices as **files**.

---

## Disk Naming in Linux

Linux gives disks special names.

| Disk Type    | Example      |
| ------------ | ------------ |
| SATA / SCSI  | /dev/sda     |
| NVMe         | /dev/nvme0n1 |
| Virtual Disk | /dev/vda     |

Partitions look like:

* `/dev/sda1`
* `/dev/sda2`

---

## Checking Available Disks

```bash
lsblk
```

Shows:

* Disks
* Partitions
* Mount points

Another useful command:

```bash
fdisk -l
```

---

## What Is a Partition?

A **partition** is a logical division of a disk.

Why partitions are used:

* Separate OS and data
* Better management
* Security and organization

---

## Creating a Partition (fdisk)

> ⚠️ Practice only on **empty disks** or lab VMs

```bash
fdisk /dev/sdb
```

Basic steps inside fdisk:

* `n` → new partition
* `p` → primary
* `w` → write changes

---

## Filesystems

A **filesystem** decides how data is stored and read.

Common Linux filesystems:

| Filesystem | Use             |
| ---------- | --------------- |
| xfs        | Default in RHEL |
| ext4       | Common Linux FS |
| vfat       | USB drives      |

---

## Creating a Filesystem

Create XFS filesystem:

```bash
mkfs.xfs /dev/sdb1
```

Create EXT4 filesystem:

```bash
mkfs.ext4 /dev/sdb1
```

---

## Mounting a Filesystem

Create mount point:

```bash
mkdir /data
```

Mount disk:

```bash
mount /dev/sdb1 /data
```

Check mount:

```bash
df -h
```

---

## Unmounting a Filesystem

```bash
umount /data
```

Note:

* No process should use the directory

---

## Permanent Mount (/etc/fstab)

To mount disk automatically at boot:

Edit file:

```bash
vi /etc/fstab
```

Example entry:

```text
/dev/sdb1   /data   xfs   defaults   0 0
```

Test fstab:

```bash
mount -a
```

---

## Checking Disk Usage

```bash
df -h
```

* Disk usage

```bash
du -sh /data
```

* Directory size

---

## Mount Options (Basic)

Common options:

* `defaults`
* `ro` → read-only
* `rw` → read-write
* `noexec` → disable execution

---

## Common Beginner Mistakes

* Formatting wrong disk
* Forgetting to mount after reboot
* Wrong fstab entry (system may not boot)

---

## Practice Tasks

1. Add a new virtual disk
2. Create a partition
3. Format with XFS
4. Mount to `/data`
5. Make mount permanent
6. Check disk usage

---

## RHCSA Exam Tips

* Practice `lsblk`, `fdisk`, `mkfs`, `mount`
* Understand `/etc/fstab`
* Be careful with disk operations

---

## Summary

* Disks are storage devices
* Partitions organize disks
* Filesystems store data
* Mounting makes storage usable
* Storage management is critical for servers

