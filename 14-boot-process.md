# 14. Linux Boot Process (RHEL)

## Chapter Overview

This chapter explains **how Linux starts from power ON to login screen**. As a Linux administrator, understanding the boot process helps you **troubleshoot boot issues**, **recover broken systems**, and is **very important for RHCSA exam**.

We will explain everything **step by step**, in **simple words**, assuming you are a **complete beginner**.

---

## What is Boot Process?

Boot process means:

> The steps Linux follows to start the system after you press the power button.

From **Power ON → Login Screen**

---

## Boot Process Flow (High Level)

1. Power ON
2. BIOS / UEFI
3. Bootloader (GRUB2)
4. Kernel
5. Initramfs
6. systemd
7. Login Prompt

Remember this order – **RHCSA exam loves this**.

---

## Step 1: Power ON

* You press the power button
* Hardware gets electricity
* CPU, RAM, disk become active

Linux is **not started yet**.

---

## Step 2: BIOS / UEFI

### What is BIOS?

* Basic Input Output System
* Stored on motherboard

### What BIOS Does:

* Checks hardware (POST)
* Finds bootable disk
* Loads bootloader

### UEFI (Modern Systems)

* New replacement of BIOS
* Faster and more secure

Linux admins mostly just **know this**, not configure it.

---

## Step 3: Bootloader (GRUB2)

### What is Bootloader?

A small program that **loads the Linux kernel into memory**.

### RHEL Bootloader

* GRUB2

### GRUB Location

* Config file: `/etc/default/grub`
* Generated file: `/boot/grub2/grub.cfg`

### What GRUB Can Do:

* Select kernel
* Pass parameters
* Boot rescue mode

⚠️ Never edit `grub.cfg` directly.

---

## Step 4: Linux Kernel

### What is Kernel?

Kernel is the **heart of Linux OS**.

### Kernel Responsibilities:

* Talks to hardware
* Manages CPU, RAM
* Loads drivers
* Starts system processes

Kernel file location:

```
/boot/vmlinuz-<version>
```

---

## Step 5: Initramfs

### What is initramfs?

* Temporary root filesystem
* Loaded into RAM
* Helps kernel access disk

Without initramfs:
❌ Kernel cannot mount root filesystem

File location:

```
/boot/initramfs-<version>.img
```

---

## Step 6: systemd (Init System)

### What is systemd?

* First process started by kernel
* PID = 1

Check it:

```
ps -p 1
```

### systemd Responsibilities:

* Start services
* Manage targets (runlevels)
* Handle logs

---

## systemd Targets (Runlevels)

| Target            | Meaning          |
| ----------------- | ---------------- |
| graphical.target  | GUI mode         |
| multi-user.target | CLI server mode  |
| rescue.target     | Single user mode |
| emergency.target  | System repair    |

Check default target:

```
systemctl get-default
```

Change default target:

```
systemctl set-default multi-user.target
```

---

## Step 7: Login Prompt

Finally:

* systemd finishes startup
* You see login screen (CLI or GUI)

🎉 Linux is ready!

---

## Boot Time Analysis

Check boot time:

```
systemd-analyze
```

Detailed info:

```
systemd-analyze blame
```

---

## Boot Logs

Check boot logs:

```
journalctl -b
```

Previous boot:

```
journalctl -b -1
```

---

## Common Boot Problems (Admin Knowledge)

* Wrong `/etc/fstab`
* Missing initramfs
* GRUB misconfiguration
* Disk not found

---

## RHCSA Exam Tips

✔ Remember boot order
✔ Know GRUB basics
✔ Understand systemd targets
✔ Know rescue & emergency mode
✔ Practice `journalctl -b`

---

## Practice Tasks

1. Check your default target
2. List available kernels
3. View current boot logs
4. Analyze boot time

---

## Summary

* Boot process = step-by-step startup
* GRUB loads kernel
* Kernel starts systemd
* systemd starts services

Understanding boot process makes you a **real Linux Admin** 💪
