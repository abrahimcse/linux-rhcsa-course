# 19. Firewalld (Firewall Management)

## Chapter Overview

This chapter explains **firewalld**, the default firewall service in RHEL. Firewall controls **which traffic is allowed or blocked**. This is a **must-know RHCSA topic**.

---

## What is Firewall?

Firewall is a security system that:

* Allows trusted traffic
* Blocks unwanted traffic

---

## What is firewalld?

firewalld is:

* Dynamic firewall
* Uses zones
* Easy to manage

Service name:

```bash
firewalld
```

---

## Check firewalld Status

```bash
systemctl status firewalld
```

---

## Firewalld Zones

Common zones:

| Zone     | Usage            |
| -------- | ---------------- |
| public   | Default          |
| trusted  | Allow all        |
| internal | Internal network |

Check active zone:

```bash
firewall-cmd --get-active-zones
```

---

## List Allowed Services

```bash
firewall-cmd --list-all
```

---

## Allow Service (HTTP)

Temporary:

```bash
firewall-cmd --add-service=http
```

Permanent:

```bash
firewall-cmd --add-service=http --permanent
firewall-cmd --reload
```

---

## Allow Port

```bash
firewall-cmd --add-port=8080/tcp --permanent
firewall-cmd --reload
```

---

## Remove Service

```bash
firewall-cmd --remove-service=http --permanent
firewall-cmd --reload
```

---

## Change Default Zone

```bash
firewall-cmd --set-default-zone=public
```

---

## RHCSA Exam Tips

✔ Use firewall-cmd
✔ Remember --permanent + reload
✔ Prefer services over ports

---

## Practice Tasks

1. Allow SSH service
2. Allow custom port
3. Remove service

---

## Summary

firewalld protects Linux from network attacks. Know zones, services, and commands.


