# 03. File Operations in Linux (RHEL Focused)

In this chapter, you will learn how to **work with files and directories** in Linux.

File operations are used every day by Linux administrators.
This chapter is written for **beginners**, with simple explanations and clear examples.

---

## What Are File Operations?

File operations mean:

* Creating files and folders
* Copying files and folders
* Moving and renaming files
* Deleting files and folders
* Viewing file content

All these tasks are done using **Linux commands**.

---

## Create Files

### Create an Empty File

```bash
touch file1.txt
```

This command creates an empty file named `file1.txt`.

### Create Multiple Files

```bash
touch file2.txt file3.txt file4.txt
```
### Edit file using (vi,vim,nano editor)
```bash
vi file1.txt
vim file1.txt
nano file1.txt
```

---

## Create Directories

### Create a Directory

```bash
mkdir mydir
```

### Create Nested Directories

```bash
mkdir -p parent/child/grandchild
```

---

## Copy Files and Directories

### Copy a File

```bash
cp file1.txt copy_file1.txt
```

### Copy File to Another Directory

```bash
cp file1.txt /tmp/
```

### Copy a Directory

```bash
cp -r mydir mydir_backup
```

---

## Move and Rename Files

### Rename a File

```bash
mv file1.txt newfile1.txt
```

### Move File to Another Directory

```bash
mv newfile1.txt /tmp/
```

### Rename a Directory

```bash
mv mydir myfolder
```

---

## Delete Files and Directories

### Delete a File

```bash
rm file2.txt
```

### Delete Multiple Files

```bash
rm file3.txt file4.txt
```

### Delete an Empty Directory

```bash
rmdir emptydir
```

### Delete a Directory with Files

```bash
rm -r myfolder
```

> ⚠️ Warning: `rm` command is dangerous. Deleted files cannot be recovered easily.

---

## View File Content

### View Full File

```bash
cat myfile.txt
```

### View Large File Page by Page

```bash
less myfile.txt
```

Press:

* `Space` → next page
* `b` → previous page
* `q` → quit

### View First Lines

```bash
head myfile.txt
```

### View Last Lines

```bash
tail myfile.txt
```

---

## File and Directory Information

### Show Detailed List

```bash
ls -l
```

### Show Hidden Files

```bash
ls -a
```

### Check File Type

```bash
file myfile.txt
```

---

## Useful Shortcuts

* `.` → current directory
* `..` → parent directory
* `~` → home directory

Example:

```bash
cd ~
cd ..
```

---

## Practice Tasks

1. Go to your home directory
2. Create a directory named `practice03`
3. Create three files inside it
4. Copy one file to `/tmp`
5. Rename one file
6. View file content using `cat` and `less`
7. Delete all files and the directory

---

## Important Notes

* Always double-check before using `rm`
* Use `ls` and `pwd` frequently
* Practice in your **home directory**

---

## What Is Next?

In the next chapter, you will learn about:

* Linux file permissions
* Read, write, execute access
* chmod and chown commands

Go to **04-permissions.md** to continue learning.

---

Happy Linux Learning 🐧
Practice daily to become confident with file operations.
