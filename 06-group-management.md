# 06 – Group Management in Linux (RHEL)

## Chapter Overview

In Linux, **groups** are used to manage **permissions for multiple users together**.

Instead of giving permission to users one by one, we put users into a **group** and control access easily.

This chapter is written for a **complete beginner**, explained slowly and clearly, like a professional Linux trainer teaching fresh learners.

---

## What Is a Group in Linux?

A **group** is a collection of users.

Why groups are needed:

* Easy permission management
* Better security
* Used heavily in servers and production systems

Example:

* Developers group
* Database team group
* DevOps group

---

## Types of Groups

| Group Type      | Description             |
| --------------- | ----------------------- |
| Primary Group   | Default group of a user |
| Secondary Group | Extra groups for a user |

Each user **must have one primary group**.

---

## Group Information File

Group details are stored in:

```text
/etc/group
```

View groups:

```bash
cat /etc/group
```

Each line represents one group.

---

## Creating a Group (groupadd)

Basic command:

```bash
groupadd developers
```

This creates a new group named **developers**.

---

## Checking Group Details

```bash
grep developers /etc/group
```

---

## Deleting a Group (groupdel)

```bash
groupdel developers
```

Note:

* Group must not be a primary group of any user

---

## Adding User to a Group

Add user to secondary group:

```bash
usermod -aG developers rahim
```

Important:

* `-a` means append (do not remove existing groups)

---

## Checking User Group Membership

```bash
groups rahim
```

Or:

```bash
id rahim
```

---

## Changing Primary Group

```bash
usermod -g developers rahim
```

Be careful:

* This changes the user’s main group

---

## Creating User with Group

```bash
useradd -g developers rahim
```

---

## Group ID (GID)

Each group has a **Group ID (GID)**.

| Type         | GID Range |
| ------------ | --------- |
| System Group | < 1000    |
| Normal Group | >= 1000   |

---

## Group Permissions in Files

Groups are mainly used in **file permissions**.

Example:

```bash
chown :developers project
chmod 770 project
```

Meaning:

* Owner and group have full access
* Others have no access

---

## Common Group Use Case (Real Life)

Scenario:

* 5 developers working on same project

Solution:

* Create group `devteam`
* Add all users to group
* Set directory permission

```bash
groupadd devteam
usermod -aG devteam user1
chmod 770 /project
chown :devteam /project
```

---

## Removing User from Group

```bash
gpasswd -d rahim developers
```

---

## Group Password (Basic Idea)

Groups can have passwords (rarely used).

Set group password:

```bash
gpasswd developers
```

---

## Common Beginner Mistakes

* Forgetting `-a` with usermod
* Deleting groups used by users
* Confusing primary and secondary groups

---

## Practice Tasks

1. Create a new group
2. Add user to group
3. Change user primary group
4. Remove user from group

---

## RHCSA Exam Tips

* Practice groupadd, groupdel
* Understand primary vs secondary group
* Group permissions are very important

---

## Summary

* Groups simplify permission management
* Every user has a primary group
* Groups are critical in real servers

