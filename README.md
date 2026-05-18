# RHCSA Linux Tutorials Repository

A practical Linux administration repository based on the RHCSA (Red Hat Certified System Administrator) syllabus. This repository provides hands-on tutorials, administration commands, shell scripting examples, troubleshooting scenarios, and real-world Linux operational tasks.

The content is useful for:

* RHCSA Exam Preparation
* Linux Administrators
* DevOps Engineers
* Infrastructure Engineers
* Cloud Engineers
* Beginners learning Enterprise Linux

---

# RHCSA Topics Covered

## Understand and Use Essential Tools

### Access Systems

* Local & Remote Console Access
* SSH Remote Login
* SSH Key-Based Authentication

### File Management

* Create, Copy, Move, and Delete Files
* Create Directories
* Hard Links & Soft Links
* Wildcards

### Text Processing

* grep
* awk
* sed
* cut
* sort
* uniq

### File Viewing & Editing

* vim Editor
* cat
* less
* head
* tail

### Input-Output Redirection

```
>
>>
2>
&
|
tee
```

### Archive & Compression

* tar
* gzip
* bzip2
* zip / unzip

---

# Operate Running Systems

## Boot Process Management

* Reboot & Shutdown Systems
* Boot Targets
* Rescue Mode
* Emergency Mode

## Process Management

* ps
* top
* kill
* nice
* jobs

## Service Management

```bash id="eh7nll"
systemctl
journalctl
```

* Start/Stop Services
* Enable/Disable Services
* Service Troubleshooting

## Log Management

* System Logs
* Journal Logs
* Log Rotation

## Scheduled Tasks

* cron Jobs
* at Command

## Software Management

### RHEL Package Management

```bash id="o3m8p9"
rpm
yum
dnf
```

* Install Packages
* Remove Packages
* Update Packages
* Repository Management

---

# Configure Local Storage

## Disk Management

* lsblk
* fdisk
* parted

## Filesystem Management

* mkfs
* mount
* umount
* /etc/fstab

## Swap Management

* Create Swap
* Enable/Disable Swap

## LVM Administration

* Physical Volumes
* Volume Groups
* Logical Volumes
* Extend & Reduce LVM

Commands:

```bash id="h82m1d"
pvcreate
vgcreate
lvcreate
lvextend
resize2fs
xfs_growfs
```

---

# Create and Configure File Systems

## Filesystem Permissions

* chmod
* chown
* chgrp

## Special Permissions

* SUID
* SGID
* Sticky Bit

## Access Control Lists (ACL)

```
getfacl
setfacl
```

## File Search Operations

```
find
locate
which
whereis
```

---

# Deploy, Configure, and Maintain Systems

## Networking Configuration

* Configure IP Address
* Hostname Configuration
* DNS Configuration
* Static Routes

Commands:

```
nmcli
ip
ping
ss
netstat
dig
nslookup
```

## Firewall Management

* firewalld
* firewall-cmd

## Time Synchronization

* chronyd
* timedatectl

---

# Manage Users and Groups

## User Administration

* useradd
* usermod
* userdel
* passwd

## Group Administration

* groupadd
* groupmod
* groupdel

## Password Policies

* Password Aging
* Account Locking
* sudo Access

---

# Security Management

## SELinux Administration

* SELinux Modes
* SELinux Contexts
* SELinux Troubleshooting

Commands:

```
getenforce
setenforce
restorecon
semanage
```

## SSH Security

* Disable Root Login
* Configure SSH Authentication
* Secure Remote Access

---

# Container & Automation Basics

## Bash Shell Scripting

* Variables
* Loops
* Conditions
* Functions

## Automation Scripts

* Health Check Scripts
* Backup Scripts
* Log Rotation Scripts
* Monitoring Scripts

---

# Troubleshooting Scenarios

* Boot Failures
* Disk Space Issues
* Service Failures
* Permission Issues
* Network Connectivity Problems
* SELinux Errors
* Package Dependency Issues

---

# Practical Linux Commands

```
ls
cp
mv
rm
find
grep
awk
sed
tar
df
du
free
top
ps
systemctl
journalctl
chmod
chown
nmcli
firewall-cmd
```

---

# Repository Goal

This repository focuses on practical Linux administration and RHCSA-oriented operational skills used in enterprise production environments.

---

# Supported Platforms

* Red Hat Enterprise Linux (RHEL)
* CentOS
* Oracle Linux (OEL)
* Ubuntu
* Debian

---

# GitHub Repository

https://github.com/rehanadm/Linux_Tutorials/tree/main

---

# Author

Abdul Rehan
