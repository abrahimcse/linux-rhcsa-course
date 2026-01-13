# 01. Linux Installation (RHEL Focused)

Welcome to the first practical chapter of this course.
Here we will learn how to **install Red Hat Enterprise Linux (RHEL)** on a virtual machine.

This chapter is designed for **absolute beginners**. You do not need prior Linux knowledge.

---

## Why Installation Is Important

Before learning Linux commands, you need a system to practice on.
We use a **virtual machine (VM)** so you can safely practice without affecting your main computer.

You can also install Linux on a physical machine later.

---

## Prerequisites

1. **A computer** with minimum 8 GB RAM recommended
2. **VirtualBox** or **VMware Workstation Player**
3. **RHEL ISO image** (RHEL 9 recommended)
4. Internet connection for updates (optional)

---

## Step 1: Install VirtualBox / VMware

### VirtualBox

1. Go to [https://www.virtualbox.org](https://www.virtualbox.org)
2. Download VirtualBox for your operating system (Windows/Mac/Linux)
3. Install VirtualBox with default options

### VMware Workstation Player

1. Go to [https://www.vmware.com/products/workstation-player](https://www.vmware.com/products/workstation-player)
2. Download and install VMware Player
3. Choose default options during installation

> Tip: VirtualBox is free, VMware Player is free for personal use

---

## Step 2: Download RHEL ISO

1. Go to [https://developers.redhat.com](https://developers.redhat.com)
2. Register / login (free developer account)
3. Download **RHEL 9 x86_64 ISO**
4. Save ISO to a folder on your computer

---

## Step 3: Create a New Virtual Machine

### VirtualBox

1. Open VirtualBox → Click **New**
2. Name: `RHEL9`
3. Type: **Linux**, Version: **Red Hat (64-bit)**
4. Memory: 2048 MB minimum (4096 MB recommended)
5. Hard disk: Create a virtual hard disk (20 GB or more)
6. Select **VHD** or **VDI** format (default)
7. Storage type: Dynamically allocated
8. Finish VM creation

### VMware Player

1. Open VMware → Click **Create a New Virtual Machine**
2. Select **Installer disc image (ISO)** → Browse RHEL ISO
3. Set VM name: `RHEL9`
4. Disk size: 20 GB minimum
5. Finish wizard

---

## Step 4: Boot from ISO

1. Start the VM
2. It will boot into **RHEL installer**
3. Choose **Install Red Hat Enterprise Linux 9**
4. Select **language and keyboard** → Next

---

## Step 5: Configure Installation

1. **Installation Destination:** Select the virtual hard disk
2. **Network & Hostname:** Enable network, set hostname (e.g., `rhel9.local`)
3. **Software Selection:** Choose **Server with GUI** (optional)
4. Review all settings → Click **Begin Installation**

---

## Step 6: Set Root Password & Create User

1. Root password: Choose a strong password
2. Create a normal user: e.g., `student`
3. Finish installation → Reboot VM

---

## Step 7: First Login

1. Login as **normal user** `student` or **root**
2. Open **Terminal**
3. Test CLI:

```bash
whoami
pwd
ls
```

---

## Step 8: Post Installation Checks

* Check IP address:

```bash
ip a
```

* Check disk usage:

```bash
df -h
```

* Update system (requires internet):

```bash
sudo dnf update -y
```

---

## Optional: Install Guest Additions (VirtualBox only)

1. In VirtualBox menu: **Devices → Insert Guest Additions CD**
2. Mount CD inside VM:

```bash
sudo mount /dev/cdrom /mnt
cd /mnt
sudo ./VBoxLinuxAdditions.run
```

3. Reboot VM

This allows:

* Full screen
* Copy-paste between host and VM
* Shared folders

---

## Important Notes

* Always use a **non-root user** for daily work
* Use **sudo** to perform administrative tasks
* Practice commands in the terminal after installation
* VM allows you to **undo mistakes safely**

---

## What Is Next?

After installation, you will learn:

* File system structure
* Important directories
* Paths and basic commands

Go to **02-filesystem.md** to continue learning.

---

Happy Linux Learning 🐧
Start practicing commands every day.
