# 02. Linux File System (RHEL Focused)

Welcome to the next chapter. After installing Linux, it is important to understand how files and directories are organized.

This chapter is designed for **absolute beginners**.

---

## What Is a File System?

A **file system** is how Linux stores and organizes files on the disk.

It controls:

* How files are saved
* How directories are structured
* How to access files efficiently

Linux uses **hierarchical file system**, starting from root `/`.

---

## Linux Directory Structure (Important Folders)

Linux directories are like folders in Windows, but they have specific purposes.

### Root Directory `/`

* Top-level directory of Linux
* All other directories are under `/`

### `/bin`

* Contains essential commands (binaries)
* Example: `ls`, `cat`, `cp`

### `/boot`

* Contains Linux kernel and boot loader files

### `/dev`

* Device files (like hard drives, USB, printers)

### `/etc`

* Configuration files for system and services

### `/home`

* User home directories
* Example: `/home/student`

### `/lib`

* Shared libraries for system programs

### `/opt`

* Optional software packages

### `/root`

* Home directory for **root** user

### `/tmp`

* Temporary files created by programs

### `/usr`

* User programs and documentation
* `/usr/bin` for additional commands

### `/var`

* Variable data: logs, mail, databases, spool files

---

## File Types in Linux

* **Regular files:** Text, documents, images
* **Directories:** Contain files and other directories
* **Links:** Shortcut or pointer to a file or directory
* **Device files:** Represent hardware devices
* **Sockets & Pipes:** Used for communication between programs

---

## File System Commands (Basic)

### 1. List files

```bash
ls
ls -l
ls -a
ll
```

### 2. Show current directory

```bash
pwd
```

### 3. Change directory

```bash
cd /home/student
cd ..
cd /
```

### 4. Create directory

```bash
mkdir myfolder
```

### 5. Remove directory

```bash
rmdir myfolder
```

### 6. Check disk usage

```bash
df -h
du -sh /home/student
```

### 7. File details

```bash
file myfile.txt
```

---

## Absolute vs Relative Paths

* **Absolute path:** Full path from root `/`
  Example: `/home/student/myfile.txt`

* **Relative path:** Path from current directory
  Example: `myfile.txt` if you are in `/home/student`

> Tip: Always understand where you are using `pwd` before accessing files

---

## Practice Tasks

1. Open terminal and type `pwd`
2. List files in `/` using `ls /`
3. Create a folder `practice` in your home directory
4. Navigate inside `practice` folder
5. Create a text file: `touch myfile.txt`
6. Check file type: `file myfile.txt`
7. Delete file and folder after practice

---

## Important Notes

* Root `/` is the base; do not delete important system files
* Always work in your **home directory** for practice
* Use `man` command to learn about commands

```bash
man ls
man mkdir
```

---

## What Is Next?

Next chapter will cover **File Operations**:

* Creating, copying, moving, deleting files
* Viewing file content
* Using Linux commands in real scenarios

Go to **03-file-operations.md** to continue learning.

---

Happy Linux Learning 🐧
Practice daily to get comfortable with directories and files.
