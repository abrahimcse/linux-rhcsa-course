# 10 – Systemctl & Services in Linux (RHEL)

## Chapter Overview

In modern Linux (RHEL 7+), **systemd** manages services and the system state.

**systemctl** is the command to control these services.

In this chapter, you will learn:

* How to check service status
* How to start, stop, restart services
* How to enable/disable services at boot
* Managing system targets (runlevels)

This chapter is written for **absolute beginners**, with simple commands and examples.

---

## What Is a Service?

A **service** is a program that runs in the background to perform specific tasks.

Examples:

* `sshd` → SSH server
* `httpd` → Apache web server
* `firewalld` → Firewall manager

Services are managed by **systemd** in RHEL.

---

## Check Service Status

```bash
systemctl status service_name
```

Example:

```bash
systemctl status sshd
```

Output shows:

* Active status (running/stopped)
* Enabled/disabled at boot
* Process ID (PID)

---

## Starting and Stopping Services

Start service:

```bash
systemctl start sshd
```

Stop service:

```bash
systemctl stop sshd
```

Restart service:

```bash
systemctl restart sshd
```

Reload service (apply config without restart):

```bash
systemctl reload sshd
```

---

## Enable/Disable Services at Boot

Enable service (start automatically at boot):

```bash
systemctl enable sshd
```

Disable service:

```bash
systemctl disable sshd
```

Check if enabled:

```bash
systemctl is-enabled sshd
```

---

## Reload Daemon

After adding/modifying service files:

```bash
systemctl daemon-reload
```

---

## List All Services

```bash
systemctl list-units --type=service
```

Show all active services:

```bash
systemctl list-units --type=service --state=running
```

---

## Managing System Targets (Runlevels)

Common targets:

* `graphical.target` → GUI mode
* `multi-user.target` → CLI mode, networking enabled
* `rescue.target` → Single user, troubleshooting

Check current target:

```bash
systemctl get-default
```

Change default target:

```bash
systemctl set-default multi-user.target
```

---

## Practice Tasks

1. Check status of `sshd` service
2. Start, stop, restart `firewalld`
3. Enable `httpd` at boot
4. Check list of running services
5. Change default target to `multi-user`

---

## RHCSA Exam Tips

* Practice `systemctl` commands for status, start/stop, enable/disable
* Understand difference between start/enable
* Learn default targets and switching targets
* Reload daemon after modifying service files

---

## Summary

* `systemctl` manages services in RHEL
* Services run in background to perform tasks
* You can start, stop, restart, enable, disable services
* System targets define system state at boot
* Practice daily for RHCSA exam
