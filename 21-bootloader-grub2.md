# 21. Bootloader GRUB2 (Recovery & Troubleshooting 🔥)

## Chapter Overview

GRUB2 is the **Linux bootloader**. If GRUB breaks, the system will **not boot**. This chapter focuses on **recovery**, which is a **hot RHCSA exam topic**.

---

## What is GRUB2?

GRUB2 loads the **Linux kernel** into memory.

Important files:

* `/etc/default/grub`
* `/boot/grub2/grub.cfg`

⚠️ Never edit `grub.cfg` directly.

---

## GRUB Menu Basics

At boot time:

* Press `Esc` or `Shift`
* GRUB menu appears

---

## Temporary GRUB Edit (Exam Favorite)

1. Select kernel
2. Press `e`
3. Find line starting with `linux`
4. Add:

```
rd.break
```

5. Press `Ctrl + X`

---

## Reset Root Password (GRUB Recovery)

```bash
mount -o remount,rw /sysroot
chroot /sysroot
passwd root
touch /.autorelabel
exit
reboot
```

---

## Rebuild GRUB Configuration

BIOS system:

```bash
grub2-mkconfig -o /boot/grub2/grub.cfg
```

UEFI system:

```bash
grub2-mkconfig -o /boot/efi/EFI/redhat/grub.cfg
```

---

## RHCSA Exam Tips

✔ Know rd.break
✔ Know grub2-mkconfig
✔ Root password recovery steps

