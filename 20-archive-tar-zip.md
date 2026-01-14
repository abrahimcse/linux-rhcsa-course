# 20. Archive & Compression (tar, zip, gzip)

## Chapter Overview

This chapter explains **file archiving and compression** in Linux. Used daily for **backup, transfer, and storage**. Important for **RHCSA and admin work**.

---

## What is Archive?

Archive means:

* Combine many files into one file

Example:

```bash
tar file = many files
```

---

## tar Command Basics

Create archive:

```bash
tar -cvf backup.tar /data
```

Extract archive:

```bash
tar -xvf backup.tar
```

List archive:

```bash
tar -tvf backup.tar
```

---

## tar with Compression

### gzip (.tar.gz)

Create:

```bash
tar -czvf backup.tar.gz /data
```

Extract:

```bash
tar -xzvf backup.tar.gz
```

---

### bzip2 (.tar.bz2)

```bash
tar -cjvf backup.tar.bz2 /data
```

---

### xz (.tar.xz)

```bash
tar -cJvf backup.tar.xz /data
```

---

## zip Command

Create zip:

```bash
zip -r backup.zip /data
```

Unzip:

```bash
unzip backup.zip
```

---

## Common tar Options

| Option | Meaning |
| ------ | ------- |
| c      | create  |
| x      | extract |
| v      | verbose |
| f      | file    |
| z      | gzip    |

---

## RHCSA Exam Tips

✔ tar is more important than zip
✔ Remember flags order
✔ Practice extract commands

---

## Practice Tasks

1. Archive a directory
2. Compress using gzip
3. Extract archive

---

## Summary

Archiving saves space and makes file transfer easy. tar is essential Linux skill.

