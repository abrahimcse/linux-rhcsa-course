# 18. SELinux Basics (RHCSA 🔥 Topic)

## Chapter Overview

SELinux (Security-Enhanced Linux) is one of the **most important and most feared topics** in RHCSA. This chapter explains SELinux in **very simple words**, step by step, for **complete beginners**.

If you understand this chapter, **50% fear of RHCSA is gone**.

---

## What is SELinux?

SELinux is a **security layer** in Linux that controls:

* Which process can access which file
* Which service can talk to which port

Even **root user** is restricted by SELinux.

---

## Why SELinux is Important?

* Protects system if service is hacked
* Prevents unauthorized access
* Mandatory Access Control (MAC)

Without SELinux:
❌ Service hack = full system risk

---

## SELinux Modes

| Mode       | Meaning                       |
| ---------- | ----------------------------- |
| Enforcing  | SELinux is ON (blocks access) |
| Permissive | Only logs, does not block     |
| Disabled   | SELinux OFF                   |

Check mode:

```bash
getenforce
```

---

## Change SELinux Mode (Temporary)

```bash
setenforce 0   # permissive
setenforce 1   # enforcing
```

---

## Change SELinux Mode (Permanent)

Config file:

```bash
/etc/selinux/config
```

---

## SELinux Context

Each file has a **security label**.

Check context:

```bash
ls -Z
```

Example:

```
unconfined_u:object_r:httpd_sys_content_t:s0
```

Important part:

```
httpd_sys_content_t
```

---

## Common SELinux Problem (Apache)

Apache cannot read file:

Wrong context ❌

```bash
/var/www/html/index.html
```

Fix context:

```bash
restorecon -Rv /var/www/html
```

---

## Change Context Manually

```bash
chcon -t httpd_sys_content_t file
```

⚠️ Not permanent

---

## Make Context Permanent

```bash
semanage fcontext -a -t httpd_sys_content_t "/web(/.*)?"
restorecon -Rv /web
```

---

## SELinux Booleans

Check booleans:

```bash
getsebool -a
```

Example:

```bash
getsebool httpd_can_network_connect
```

Enable boolean:

```bash
setsebool -P httpd_can_network_connect on
```

---

## SELinux Logs

```bash
ausearch -m avc
```

Or:

```bash
journalctl | grep AVC
```

---

## RHCSA Exam Tips

✔ SELinux mostly Enforcing
✔ Know getenforce / setenforce
✔ Context fixing is key
✔ Do not disable SELinux

---

## Practice Tasks

1. Check SELinux mode
2. Break apache context
3. Fix it using restorecon
4. Enable boolean

---

## Summary

SELinux protects Linux silently. Learn how to **adjust**, not disable it.

