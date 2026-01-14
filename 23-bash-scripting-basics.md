# 23. Bash Scripting Basics

## Chapter Overview

Bash scripting helps automate Linux tasks. This chapter teaches **basic scripting** for **freshers and RHCSA level**.

---

## What is Bash Script?

A bash script is a **file with Linux commands** executed automatically.

---

## First Script

```bash
#!/bin/bash
echo "Hello Linux"
```

Make executable:

```bash
chmod +x script.sh
./script.sh
```

---

## Variables

```bash
name="Linux"
echo $name
```

---

## Input from User

```bash
read username
echo "Hello $username"
```

---

## If Condition

```bash
if [ $x -gt 5 ]; then
 echo "Greater"
fi
```

---

## Loop Example

```bash
for i in 1 2 3
do
 echo $i
done
```

---

## Script for Admin Task

```bash
df -h > disk_report.txt
```

---

## RHCSA Exam Tips

✔ Know shebang
✔ chmod +x
✔ Simple if & loop
