# 17. Cron & AT Jobs (Task Scheduling)

## Chapter Overview

This chapter explains **task scheduling** in Linux using **cron** and **at**. Used to automate jobs like backups, cleanup, and reports. Very important for **RHCSA and real servers**.

---

## What is Cron?

Cron is used to **run jobs repeatedly** at fixed times.

Examples:

* Daily backup
* Log cleanup
* Monitoring scripts

---

## Cron Syntax

```
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week (0-7)
│ │ │ └──── Month (1-12)
│ │ └────── Day of month (1-31)
│ └──────── Hour (0-23)
└────────── Minute (0-59)
```

---

## Edit Crontab

```bash
crontab -e
```

List jobs:

```bash
crontab -l
```

Remove jobs:

```bash
crontab -r
```

---

## Cron Examples

Run every day at 1 AM:

```bash
0 1 * * * /backup.sh
```

Every 5 minutes:

```bash
*/5 * * * * /script.sh
```

---

## Cron Service

```bash
systemctl status crond
```

---

## What is AT?

AT runs a job **only once** at a specific time.

---

## AT Commands

Schedule job:

```bash
at 5pm
```

Inside at prompt:

```bash
bash /script.sh
Ctrl+D
```

List jobs:

```bash
atq
```

Remove job:

```bash
atrm job_id
```

---

## Cron vs AT

| Feature  | Cron          | AT             |
| -------- | ------------- | -------------- |
| Run type | Repeated      | One time       |
| Usage    | Regular tasks | One-time tasks |

---

## RHCSA Exam Tips

✔ Know cron format
✔ Know crontab commands
✔ Difference between cron & at

---

## Practice Tasks

1. Create daily cron job
2. Schedule at job
3. Verify job list

---

## Summary

Cron and AT automate Linux work and save time. Essential skill for Linux admins.

