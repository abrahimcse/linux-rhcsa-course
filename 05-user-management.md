# 05 – User Management in Linux (RHEL)

## Chapter Overview

Linux is a **multi-user operating system**. That means many users can work on the same system at the same time.

As a Linux administrator (RHCSA level), you must know:

* How to create users
* How to delete users
* How to manage passwords
* How to control user access

This chapter is written for a **complete beginner**. No prior Linux knowledge is required.

---

## What Is a User in Linux?

A **user** is a person or service that can log in and use the system.

Examples:

* Human users (developers, admins)
* System users (services like nginx, mysql)

Linux keeps user information in system files.

---

## Types of Users

| User Type   | Description                       |
| ----------- | --------------------------------- |
| Root        | Super administrator (full access) |
| Normal User | Regular user with limited access  |
| System User | Used by services and applications |

Important:

* **root** can do anything
* Normal users need permission

---

## User Information Files

| File        | Purpose             |
| ----------- | ------------------- |
| /etc/passwd | User account info   |
| /etc/shadow | Encrypted passwords |
| /etc/group  | Group info          |

Never edit these files manually as a beginner.

---

## Viewing Existing Users

```bash
cat /etc/passwd
```

Each line represents one user.

---

## Creating a User (useradd)

Basic command:

```bash
useradd username
```

Example:

```bash
useradd abrahim
```

This creates:

* User account
* User ID (UID)

---

## Creating User with Home Directory

```bash
useradd -m abrahim
```

Home directory:

```text
/home/abrahim
```

---

## Setting Password (passwd)

```bash
passwd abrahim
```

System will ask you to enter password.

---

## Switching User (su)

```bash
su abrahim
```

Switch to root:

```bash
su -
```

---

## Login Shell

Each user has a default shell.

Common shells:

* /bin/bash
* /bin/sh

Check shell:

```bash
cat /etc/passwd | grep abrahim
```

---

## User ID (UID) and Group ID (GID)

| Type | Meaning         |
| ---- | --------------- |
| UID  | User ID number  |
| GID  | Group ID number |

Normal users usually start from UID **1000**.

---

## Modifying a User (usermod)

Change shell:

```bash
usermod -s /bin/bash abrahim
```

Change home directory:

```bash
usermod -d /home/newabrahim abrahim
```

---

## Locking and Unlocking User

Lock user:

```bash
usermod -L abrahim
```

Unlock user:

```bash
usermod -U abrahim
```

---

## Deleting a User (userdel)

Delete user only:

```bash
userdel abrahim
```

Delete user with home directory:

```bash
userdel -r abrahim
```

---

## Password Aging Policy

Check password policy:

```bash
chage -l abrahim
```

Set password expiry:

```bash
chage -M 90 abrahim
```

---

## Sudo Access (Basic Intro)

Normal users cannot run admin commands.

Add user to sudo group:

```bash
usermod -aG wheel abrahim
```

(RHEL uses **wheel** group)

---

## Checking Logged-in Users

```bash
who
```

```bash
w
```

---

## Common Beginner Mistakes

* Forgetting to set password
* Deleting users without backup
* Giving root access unnecessarily

---

## Practice Tasks

1. Create a new user
2. Set password
3. Lock and unlock the user
4. Delete the user with home directory

---

## RHCSA Exam Tips

* Practice useradd, usermod, userdel
* Understand UID and GID
* Password policies are important

---

## Summary

* Linux supports multiple users
* Root has full access
* User management is core admin skill

