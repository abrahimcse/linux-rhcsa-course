# 04 - File Permissions in Linux (RHEL)

## Chapter Overview

In Linux, **permissions** control who can **read**, **write**, or **execute** a file or directory.

As a Linux administrator (RHCSA level), this is **one of the MOST important topics**. Wrong permissions can break applications or create security risks.

Don’t worry - we will learn this **slowly and clearly**, assuming you are a **complete beginner**.

---

## Why File Permissions Are Important

Linux is a **multi-user operating system**.

That means:

* Many users can log in at the same time
* Each user should access **only what they are allowed to**

Permissions help Linux to:

* Protect system files
* Protect user data
* Prevent accidental or malicious damage

---

## Basic Permission Types

Linux has **three main permission types**:

| Permission | Symbol | Meaning                                 |
| ---------- | ------ | --------------------------------------- |
| Read       | r      | View file content / list directory      |
| Write      | w      | Modify file / create-delete files       |
| Execute    | x      | Run file as a program / enter directory |

---

## Permission Groups (Who Can Access)

Each file or directory has **three user groups**:

| Group  | Meaning                    |
| ------ | -------------------------- |
| Owner  | The user who owns the file |
| Group  | Users in the same group    |
| Others | Everyone else              |

---

## Viewing Permissions (ls -l)

Use this command to see permissions:

```bash
ls -l
```

Example output:

```bash
-rwxr-xr-- 1 root root 1024 test.sh
```

Let’s break this down.

---

## Understanding Permission Format

```text
-rwxr-xr--
```

| Part | Meaning                         |
| ---- | ------------------------------- |
| -    | File type (- file, d directory) |
| rwx  | Owner permissions               |
| r-x  | Group permissions               |
| r--  | Others permissions              |

So this means:

* Owner → read, write, execute
* Group → read, execute
* Others → read only

---

## File Types

| Symbol | Type         |
| ------ | ------------ |
| -      | Regular file |
| d      | Directory    |
| l      | Link         |

Example:

```bash
drwxr-xr-x
```

This is a **directory**.

---

## Changing Permissions (chmod)

### Using Symbolic Method

```bash
chmod u+x file.txt
```

| Symbol | Meaning           |
| ------ | ----------------- |
| u      | Owner             |
| g      | Group             |
| o      | Others            |
| +      | Add permission    |
| -      | Remove permission |

Example:

```bash
chmod g-w file.txt
```

Removes write permission from group.

---

## Numeric Permission Method

Each permission has a number:

| Permission | Value |
| ---------- | ----- |
| Read       | 4     |
| Write      | 2     |
| Execute    | 1     |

Add values together.

Example:

```bash
chmod 755 file.sh
```

| User   | Value | Meaning |
| ------ | ----- | ------- |
| Owner  | 7     | rwx     |
| Group  | 5     | r-x     |
| Others | 5     | r-x     |

---

## Common Permission Examples

| Command             | Meaning           |
| ------------------- | ----------------- |
| chmod 644 file      | Normal text file  |
| chmod 755 script.sh | Executable script |
| chmod 700 file      | Private file      |

---

## Changing Ownership (chown)

```bash
chown user file
```

Change owner and group:

```bash
chown user:group file
```

Example:

```bash
chown rahim:developers app.log
```

---

## Changing Group Only (chgrp)

```bash
chgrp developers file.txt
```

---

## Directory Permissions Explained

| Permission | Directory Meaning   |
| ---------- | ------------------- |
| r          | List files          |
| w          | Create/delete files |
| x          | Enter directory     |

Important:

* Without **x**, you cannot access the directory

---

## Special Permissions (Basic Intro)

| Permission | Name                        |
| ---------- | --------------------------- |
| SUID       | Run as owner                |
| SGID       | Run as group                |
| Sticky bit | Protect files in shared dir |

Example:

```bash
chmod +t /tmp
```

---

## Real Life Example

```bash
mkdir project
chmod 770 project
chown rahim:dev project
```

Meaning:

* Owner and group can fully access
* Others have no access

---

## Common Beginner Mistakes

* Giving **777** permission unnecessarily
* Changing permissions on system files
* Not understanding directory execute permission

---

## Practice Tasks

1. Create a file and set permission to `644`
2. Create a script and make it executable
3. Create a directory only accessible by owner

---

## RHCSA Exam Tips

* Understand numeric permissions well
* Practice `chmod`, `chown`, `chgrp`
* Directory permissions are very important

---

## Summary

* Linux uses permissions for security
* Permissions control access
* Always use minimum required permissions

