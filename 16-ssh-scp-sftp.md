# 16. SSH, SCP & SFTP (Remote Access)

## Chapter Overview

This chapter teaches **remote server access** using SSH, SCP, and SFTP. This is **daily work** for Linux administrators and **mandatory for RHCSA**.

---

## What is SSH?

SSH (Secure Shell) allows you to:

* Login to remote Linux server securely
* Execute commands remotely

### SSH Command

```bash
ssh user@server_ip
```

Example:

```bash
ssh root@192.168.1.10
```

---

## SSH Port

Default SSH port:

```
22
```

Check SSH service:

```bash
systemctl status sshd
```

---

## SSH Key-Based Authentication

### Generate Key

```bash
ssh-keygen
```

### Copy Key to Server

```bash
ssh-copy-id user@server_ip
```

Benefits:

* No password
* More secure

---

## What is SCP?

SCP (Secure Copy) is used to **copy files securely** between systems.

### Copy Local → Remote

```bash
scp file.txt user@server_ip:/path
```

### Copy Remote → Local

```bash
scp user@server_ip:/path/file.txt .
```

---

## What is SFTP?

SFTP provides **FTP-like interface** over SSH.

### Start SFTP

```bash
sftp user@server_ip
```

Common Commands:

```bash
ls
put file.txt
get file.txt
exit
```

---

## SSH Config File

```bash
/etc/ssh/sshd_config
```

Restart service after change:

```bash
systemctl restart sshd
```

---

## RHCSA Exam Tips

✔ Know ssh, scp syntax
✔ Understand key-based login
✔ Know ssh service name

---

## Practice Tasks

1. SSH into another VM
2. Copy file using SCP
3. Login using SFTP

---

## Summary

SSH tools allow secure remote administration. Every Linux admin uses SSH daily.
