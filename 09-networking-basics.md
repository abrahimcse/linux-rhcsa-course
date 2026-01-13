# 09 – Networking Basics in Linux (RHEL)

## Chapter Overview

Networking is an important skill for a Linux administrator. Without networking, servers cannot communicate.

In this chapter, you will learn:

* How to check network interfaces
* Assign IP addresses
* Test connectivity
* Basic hostname and DNS

This chapter is written for **beginners**, with simple examples.

---

## Check Network Interfaces

### Using `ip` command

```bash
ip a
```

* Lists all network interfaces
* Shows IP address, MAC, state

### Using `ifconfig` (older systems)

```bash
ifconfig -a
```

---

## Check Connectivity

### Ping a host

```bash
ping google.com
```

* Tests if network is working
* Press `Ctrl + C` to stop

### Traceroute (path to host)

```bash
traceroute google.com
```

* Shows route packets take

---

## Assign IP Address

### Temporary IP (resets after reboot)

```bash
ip addr add 192.168.1.10/24 dev eth0
```

### Remove IP

```bash
ip addr del 192.168.1.10/24 dev eth0
```

### Bring interface up/down

```bash
ip link set eth0 up
ip link set eth0 down
```

---

## Check Default Gateway

```bash
ip route
```

* Shows default gateway and routes

Add default gateway:

```bash
ip route add default via 192.168.1.1
```

---

## Check DNS Configuration

DNS settings are in `/etc/resolv.conf`

```bash
cat /etc/resolv.conf
```

```
nameserver 8.8.8.8
nameserver 8.8.4.4
```

---

## Hostname Management

Check hostname:

```bash
hostnamectl status
```

Set hostname temporarily:

```bash
hostname newhostname
```

Set hostname permanently:

```bash
hostnamectl set-hostname newhostname
```

---

## Common Network Tools

| Command    | Purpose             |
| ---------- | ------------------- |
| ping       | Check connectivity  |
| traceroute | Path to host        |
| netstat    | Network connections |
| ss         | Socket statistics   |
| curl       | Test HTTP requests  |
| wget       | Download files      |

---

## Firewall Basics (RHEL / firewalld)

Check firewall status:

```bash
firewall-cmd --state
```

Open port 80:

```bash
firewall-cmd --permanent --add-port=80/tcp
firewall-cmd --reload
```

Close port 80:

```bash
firewall-cmd --permanent --remove-port=80/tcp
firewall-cmd --reload
```

---

## Practice Tasks

1. Check network interfaces
2. Ping google.com
3. Assign temporary IP to interface
4. Check default gateway
5. View `/etc/resolv.conf`
6. Change hostname temporarily and permanently
7. Open and close a port in firewall

---

## RHCSA Exam Tips

* Know `ip` and `ping` commands well
* Understand `/etc/resolv.conf` and default gateway
* Practice hostname change commands
* Firewall basics may appear in exam

---

## Summary

* Networking is essential for servers
* `ip` is main command for interfaces
* Ping, traceroute, netstat/ss help troubleshooting
* Hostname, DNS, gateway are important
* Firewalld basics are part of Linux admin tasks
