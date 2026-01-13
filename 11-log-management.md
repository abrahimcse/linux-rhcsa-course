# 11 – Log Management in Linux (RHEL)

## Chapter Overview

Logs are **records of system activity**. They help administrators understand what is happening inside the system.

In real servers, **logs are the first place to check when something goes wrong**.

In this chapter, you will learn:

* What logs are
* Where logs are stored
* How to read logs
* How to use `journalctl`

This chapter is written for **absolute beginners**, with easy explanations.

---

## What Is a Log?

A **log** is a text file that stores information about:

* System events
* Errors and warnings
* User actions
* Application activities

Example:

* Login success or failure
* Service start or stop
* Application crash

---

## Where Are Logs Stored?

Most logs are stored in:

```text
/var/log
```

List log files:

```bash
ls /var/log
```

---

## Important Log Files

| Log File          | Purpose                        |
| ----------------- | ------------------------------ |
| /var/log/messages | General system messages        |
| /var/log/secure   | Authentication & security logs |
| /var/log/cron     | Cron job logs                  |
| /var/log/boot.log | Boot process logs              |
| /var/log/dnf.log  | Package management logs        |

---

## Viewing Log Files

### Using `cat`

```bash
cat /var/log/messages
```

### Using `less` (recommended)

```bash
less /var/log/messages
```

Useful keys in `less`:

* `q` → quit
* `/error` → search word
* `n` → next match

### Using `tail`

```bash
tail /var/log/messages
```

View last 20 lines:

```bash
tail -n 20 /var/log/messages
```

Live log view:

```bash
tail -f /var/log/messages
```

---

## Searching Logs

Using `grep`:

```bash
grep error /var/log/messages
```

Case-insensitive search:

```bash
grep -i failed /var/log/secure
```

---

## systemd Journal (journalctl)

Modern RHEL uses **systemd journal** instead of only text logs.

View all logs:

```bash
journalctl
```

View latest logs:

```bash
journalctl -e
```

Follow logs live:

```bash
journalctl -f
```

---

## View Logs for a Service

Example: SSH service logs

```bash
journalctl -u sshd
```

View logs since last boot:

```bash
journalctl -b
```

View logs by time:

```bash
journalctl --since "1 hour ago"
```

---

## Log Levels

| Level   | Meaning                 |
| ------- | ----------------------- |
| emerg   | System unusable         |
| alert   | Immediate action needed |
| crit    | Critical issue          |
| err     | Error                   |
| warning | Warning                 |
| notice  | Normal but important    |
| info    | Information             |
| debug   | Debugging               |

Example:

```bash
journalctl -p err
```

---

## Log Rotation (Basic Idea)

Logs grow over time. Linux rotates logs to:

* Save disk space
* Keep logs manageable

Tool used:

```text
logrotate
```

Config files:

```text
/etc/logrotate.conf
/etc/logrotate.d/
```

(No deep config needed for beginners)

---

## Common Beginner Mistakes

* Not checking logs when error occurs
* Using `cat` for large log files
* Ignoring log permissions

---

## Practice Tasks

1. List files in `/var/log`
2. View `/var/log/messages` using `less`
3. Search for failed login attempts
4. Use `journalctl` to view ssh logs
5. Follow logs live using `tail -f`

---

## RHCSA Exam Tips

* Know where logs are stored
* Practice `journalctl` commands
* Be comfortable with `less`, `tail`, `grep`

---

## Summary

* Logs record system activity
* `/var/log` is main log directory
* `journalctl` is very important in RHEL
* Logs are essential for troubleshooting

