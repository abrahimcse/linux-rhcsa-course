# 15. Rescue & Emergency Mode (RHEL)

## Chapter Overview

This chapter explains **Rescue Mode** and **Emergency Mode** in Linux. These modes are used when the system **fails to boot normally**. This topic is **very important for RHCSA exam** and real server troubleshooting.

Assume you are a **beginner** and learning step by step.

---

## What are Rescue & Emergency Modes?

These are **special boot modes** used to:

* Fix broken system
* Reset root password
* Fix `/etc/fstab`
* Repair filesystem

---

## Rescue Mode

### What is Rescue Mode?

Rescue mode provides:

* Almost full system
* Mounted root filesystem (usually read-only)
* Network available (sometimes)

Used when system boots partially.

### Enter Rescue Mode (GRUB)

1. Reboot system
2. At GRUB menu press `e`
3. Find line starting with `linux`
4. Add at end:

```
rescue
```

5. Press `Ctrl + X`

---

## Emergency Mode

### What is Emergency Mode?

Emergency mode is:

* Minimal environment
* Root filesystem NOT mounted
* No services

Used when system is **very broken**.

### Enter Emergency Mode

Add at kernel line:

```
emergency
```

---

## Rescue vs Emergency (Difference)

| Feature  | Rescue     | Emergency   |
| -------- | ---------- | ----------- |
| Root FS  | Mounted    | Not mounted |
| Services | Limited    | None        |
| Network  | Possible   | No          |
| Usage    | Fix issues | Deep repair |

---

## Mount Root Filesystem (Emergency)

```bash
mount -o remount,rw /
```

---

## Common Recovery Tasks

### Fix `/etc/fstab`

```bash
vi /etc/fstab
```

### Reset Root Password

```bash
passwd root
```

### Check Disk

```bash
fsck -f /dev/sda2
```

---

## Exit Rescue / Emergency Mode

```bash
reboot
```

---

## RHCSA Exam Tips

✔ Know difference between rescue & emergency
✔ Know how to edit GRUB
✔ Practice fixing fstab issue

---

## Summary

Rescue and Emergency modes are **life savers** for Linux admins. Knowing them means you can recover almost any broken system.

