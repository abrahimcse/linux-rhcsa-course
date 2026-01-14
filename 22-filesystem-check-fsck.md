# 22. Filesystem Check (fsck)

## Chapter Overview

Filesystem corruption can stop Linux from booting. This chapter explains **fsck**, used to **check and repair filesystems**.

---

## What is fsck?

fsck = File System Consistency Check

Used to:

* Fix disk errors
* Repair corrupted filesystem

---

## Important Rule

⚠️ Never run fsck on a mounted filesystem.

---

## Check Filesystem Type

```bash
lsblk -f
```

---

## fsck for ext4

```bash
fsck /dev/sdb1
```

Force check:

```bash
fsck -f /dev/sdb1
```

Auto fix:

```bash
fsck -y /dev/sdb1
```

---

## xfs Filesystem

XFS does NOT use fsck.

Use:

```bash
xfs_repair /dev/sdb1
```

---

## fsck at Boot

Triggered if:

* Filesystem marked dirty
* Manual force

Force fsck at boot:

```bash
touch /forcefsck
```

---

## RHCSA Exam Tips

✔ ext4 uses fsck
✔ xfs uses xfs_repair
✔ Never fsck mounted disk

