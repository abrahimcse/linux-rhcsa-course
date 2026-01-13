# 07 – Process Management in Linux (RHEL)

## Chapter Overview

Linux is a **multi-tasking operating system**. This means it can run **many programs (processes)** at the same time.

As a Linux administrator, you must know:

* How to view running processes
* How to control them (stop, start, kill)
* How to check CPU and memory usage

This chapter is written for **absolute beginners**, using **easy English** and clear examples.

---

## What Is a Process?

A **process** is any program or command running on Linux.

Example:

* Running `bash` shell
* `firefox` browser
* `sshd` server

Each process has:

* **PID (Process ID)**: Unique number
* **Owner**: User who started the process
* **Status**: Running, sleeping, stopped, etc.

---

## Viewing Processes

### 1. Using `ps` command

```bash
ps
```

* Shows processes in current shell

```bash
ps aux
```

* Shows all processes
* `a` → all users
* `u` → user-friendly format
* `x` → includes processes not attached to terminal

### 2. Using `top` command

```bash
top
```

* Interactive view of running processes
* Shows CPU, memory, and process info
* Press `q` to quit

### 3. Using `htop` (optional)

```bash
htop
```

* Better visual view (needs installation)
* Navigate with arrow keys
* Press `F10` to quit

---

## Process States

| State | Meaning                           |
| ----- | --------------------------------- |
| R     | Running                           |
| S     | Sleeping                          |
| T     | Stopped                           |
| Z     | Zombie (finished but not cleaned) |

Check state in `ps aux` under **STAT** column.

---

## Controlling Processes

### Kill a Process

```bash
kill PID
```

Force kill:

```bash
kill -9 PID
```

### Stop / Suspend a Process

```bash
kill -STOP PID
```

### Resume a Process

```bash
kill -CONT PID
```

### Background and Foreground

Run command in background:

```bash
sleep 100 &
```

* `&` puts process in background

Bring background process to foreground:

```bash
fg %1
```

List background jobs:

```bash
jobs
```

---

## CPU and Memory Usage

### Using `top`

* `%CPU` → CPU usage
* `%MEM` → Memory usage
* `RES` → Resident memory used

### Using `ps`

```bash
ps aux --sort=-%cpu | head -n 10
```

* Top 10 CPU-consuming processes

```bash
ps aux --sort=-%mem | head -n 10
```

* Top 10 memory-consuming processes

---

## Nice and Renice (Process Priority)

### Start process with priority

```bash
nice -n 10 command
```

* `10` → lower priority (default is 0)

### Change priority of running process

```bash
renice 5 -p PID
```

* `5` → higher priority than default 10

---

## System Monitor Commands

* `uptime` → shows load average
* `free -h` → memory usage
* `vmstat` → system processes and resources
* `top` / `htop` → interactive monitoring

---

## Practice Tasks

1. Run a command in background (`sleep 60 &`)
2. List all running processes
3. Kill a process by PID
4. Check CPU and memory usage using `top`
5. Change priority of a process using `nice` or `renice`

---

## RHCSA Exam Tips

* Practice `ps`, `top`, `kill`, `jobs`, `fg`
* Learn process states
* Be confident in identifying CPU/memory hogs

---

## Summary

* A process is a running program
* Linux is multi-tasking
* You can control, monitor, and prioritize processes
* Knowing process management is critical for real servers and RHCSA exam

