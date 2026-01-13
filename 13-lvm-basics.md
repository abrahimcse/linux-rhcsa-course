# Chapter 13: LVM Basics (Logical Volume Manager)

## 📌 What is LVM?

LVM (Logical Volume Manager) is a flexible disk management system in Linux that allows you to create, resize, and manage disk storage dynamically without downtime.

### Why LVM is Important?

* Resize partitions easily
* Combine multiple disks into one logical storage
* Better storage management for servers
* Used heavily in RHEL / RHCSA / Production servers

---

## 🧱 LVM Architecture

```
Physical Disk → Physical Volume (PV)
PV → Volume Group (VG)
VG → Logical Volume (LV)
LV → Filesystem → Mount Point
```

### Components

| Component | Description                       |
| --------- | --------------------------------- |
| PV        | Physical disk or partition        |
| VG        | Pool of storage created from PVs  |
| LV        | Virtual partition created from VG |

---

## 🔍 Check LVM Status

```bash
pvs
vgs
lvs
```

Detailed view:

```bash
pvdisplay
vgdisplay
lvdisplay
```

---

## 🧪 Step-by-Step LVM Setup Example

### 1️⃣ Prepare Disk

```bash
lsblk
fdisk /dev/sdb
# Create partition type 8e (Linux LVM)
```

### 2️⃣ Create Physical Volume (PV)

```bash
pvcreate /dev/sdb1
```

Verify:

```bash
pvs
```

---

### 3️⃣ Create Volume Group (VG)

```bash
vgcreate vg_data /dev/sdb1
```

Check:

```bash
vgs
```

---

### 4️⃣ Create Logical Volume (LV)

Create 5GB LV:

```bash
lvcreate -L 5G -n lv_data vg_data
```

Or use all space:

```bash
lvcreate -l 100%FREE -n lv_data vg_data
```

Verify:

```bash
lvs
```

---

### 5️⃣ Create Filesystem

```bash
mkfs.ext4 /dev/vg_data/lv_data
# or
mkfs.xfs /dev/vg_data/lv_data
```

---

### 6️⃣ Mount Logical Volume

```bash
mkdir /data
mount /dev/vg_data/lv_data /data
```

Verify:

```bash
df -h
```

---

## 🔄 Persistent Mount (fstab)

```bash
blkid /dev/vg_data/lv_data
```

Add to `/etc/fstab`:

```bash
UUID=xxxxxx  /data  xfs  defaults  0 0
```

Test:

```bash
mount -a
```

---

## 📈 Extend Logical Volume

### 1️⃣ Extend LV

```bash
lvextend -L +2G /dev/vg_data/lv_data
```

### 2️⃣ Resize Filesystem

For ext4:

```bash
resize2fs /dev/vg_data/lv_data
```

For xfs:

```bash
xfs_growfs /data
```

---

## 📉 Reduce Logical Volume (⚠️ Risky)

> ⚠️ XFS does NOT support shrinking

Steps (ext4 only):

```bash
umount /data
e2fsck -f /dev/vg_data/lv_data
resize2fs /dev/vg_data/lv_data 4G
lvreduce -L 4G /dev/vg_data/lv_data
mount /data
```

---

## ➕ Add New Disk to Existing VG

```bash
pvcreate /dev/sdc
vgextend vg_data /dev/sdc
```

---

## 🧹 Remove LVM

```bash
umount /data
lvremove /dev/vg_data/lv_data
vgremove vg_data
pvremove /dev/sdb1
```

---

## 🧠 Real-World Use Case

* Database storage expansion
* Log volume expansion
* Production server disk growth without downtime

---

## 🧪 Practice Tasks

1. Create a VG using two disks
2. Create LV and mount it
3. Extend LV by 1GB
4. Make mount persistent
5. Check disk usage

---

## 📝 Exam Tips (RHCSA)

* Remember order: **PV → VG → LV**
* Know commands: `pvcreate`, `vgcreate`, `lvcreate`
* XFS resize only supports **grow**, not shrink
* Always run `mount -a` after editing fstab

---

## ✅ Summary

LVM provides powerful, flexible, and safe disk management. It is a must-know topic for Linux system administrators and RHCSA exam candidates.

