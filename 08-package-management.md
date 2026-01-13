# 08 – Package Management in Linux (RHEL/DNF & YUM)

## Chapter Overview

In Linux, **packages** are software programs or applications.

Package management is a **core skill for Linux administrators**. It allows you to:

* Install new software
* Update software
* Remove unwanted software
* Keep the system secure

This chapter is written for **absolute beginners** and is **RHEL-focused**.

---

## Package Managers in RHEL

RHEL uses **YUM** and **DNF** for package management:

| Manager | Description                      |
| ------- | -------------------------------- |
| YUM     | Older package manager (RHEL 7)   |
| DNF     | Newer package manager (RHEL 8/9) |

> Note: DNF is backward compatible with YUM commands.

---

## Installing Packages

### Using DNF

```bash
dnf install package_name
```

Example:

```bash
dnf install vim
```

* Installs Vim editor
* Resolves dependencies automatically

### Using YUM

```bash
yum install package_name
```

---

## Updating Packages

### Update a specific package

```bash
dnf update package_name
```

### Update all packages

```bash
dnf update -y
```

* `-y` automatically answers yes to prompts

---

## Removing Packages

### Remove a package

```bash
dnf remove package_name
```

Example:

```bash
dnf remove vim
```

> Warning: Be careful, removing system packages can break the system

---

## Searching for Packages

### Search by name or description

```bash
dnf search keyword
```

Example:

```bash
dnf search editor
```

### Check package info

```bash
dnf info package_name
```

---

## Listing Installed Packages

```bash
dnf list installed
```

Filter with grep:

```bash
dnf list installed | grep vim
```

---

## Repositories

Repositories (repos) are sources for packages.

### Enable repository

```bash
dnf config-manager --set-enabled repo_name
```

### Disable repository

```bash
dnf config-manager --set-disabled repo_name
```

### List enabled repositories

```bash
dnf repolist
```

---

## Cleaning Cache

DNF/YUM keeps cache for faster installation.

```bash
dnf clean all
```

* Removes cached packages

---

## Updating the System Kernel

Check available kernels:

```bash
dnf list kernel
```

Update kernel:

```bash
dnf update kernel
```

Reboot after update:

```bash
reboot
```

---

## Useful Tips

* Always check repository before installing packages
* Prefer `dnf` for RHEL 8/9
* Avoid `yum` on newer RHEL unless needed
* Keep system updated regularly

---

## Practice Tasks

1. Install `nano` editor
2. Search for `git` package
3. Update all packages
4. Remove `nano` after practice
5. List installed packages and filter with `grep`

---

## RHCSA Exam Tips

* Know how to install, remove, update packages
* Understand how to search packages
* Be confident with DNF commands

---

## Summary

* Packages are software programs
* DNF/YUM manage software installation, updates, removal
* Repositories provide packages
* Always keep the system updated and clean


