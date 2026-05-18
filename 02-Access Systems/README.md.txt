# Access Systems - Linux Administration

This section covers RHCSA-related system access topics including local console access, remote SSH access, and SSH key-based authentication for secure Linux administration.

---

# Topics Covered

* Local Console Access
* Remote Console Access
* SSH Remote Login
* SSH Key-Based Authentication
* SSH Security Best Practices
* SSH Troubleshooting

---

# Local Console Access

Local console access allows administrators to directly log in to a Linux system using a physical keyboard and monitor attached to the server.

## Common Usage

* Initial server setup
* Recovery mode access
* Password reset operations
* Troubleshooting boot failures
* Single-user mode administration

## Switch Between Virtual Consoles

Linux provides multiple TTY consoles.

### Access Console Terminals

```bash
Ctrl + Alt + F1
Ctrl + Alt + F2
Ctrl + Alt + F3
```

Return to graphical interface:

```bash
Ctrl + Alt + F1
```

OR

```bash
Ctrl + Alt + F7
```

(Depends on Linux distribution)

---

# Remote Console Access

Remote access allows administrators to manage Linux systems remotely across networks.

## Common Remote Access Protocols

| Protocol | Purpose                 |
| -------- | ----------------------- |
| SSH      | Secure remote login     |
| SCP      | Secure file copy        |
| SFTP     | Secure file transfer    |
| VNC      | Remote graphical access |

---

# SSH Remote Login

SSH (Secure Shell) is the standard secure protocol for remote Linux administration.

## Basic SSH Syntax

```bash
ssh username@server-ip
```

Example:

```bash
ssh admin@192.168.1.10
```

---

# SSH Login Using Custom Port

```bash
ssh -p 2222 admin@192.168.1.10
```

---

# Copy Files Using SCP

## Copy File to Remote Server

```bash
scp backup.tar.gz admin@192.168.1.10:/backup
```

## Copy File from Remote Server

```bash
scp admin@192.168.1.10:/backup/file.txt .
```

---

# SSH Service Management

## RHEL / CentOS / OEL

```bash
systemctl status sshd
systemctl restart sshd
systemctl enable sshd
```

## Ubuntu / Debian

```bash
systemctl status ssh
systemctl restart ssh
```

---

# SSH Configuration File

Main SSH daemon configuration file:

```bash
/etc/ssh/sshd_config
```

Common configurations:

```ini
Port 22
PermitRootLogin no
PasswordAuthentication yes
PubkeyAuthentication yes
```

After changes restart SSH service:

```bash
systemctl restart sshd
```

---

# SSH Key-Based Authentication Setup Guide

## Overview

SSH key-based authentication provides secure passwordless login between Linux servers or client systems. It uses a cryptographic key pair:

* **Private Key** → Stored securely on client machine
* **Public Key** → Copied to target server

This method improves security, automation capability, and administrative efficiency.

---

# Advantages of SSH Key Authentication

* More secure than password authentication
* Enables passwordless login
* Required for automation tools like Ansible
* Prevents brute-force password attacks
* Simplifies server administration

---

# Environment

| Component      | Details                            |
| -------------- | ---------------------------------- |
| Client Machine | Linux / Windows with OpenSSH       |
| Target Server  | RHEL / Ubuntu / CentOS / OEL / AIX |
| Protocol       | SSH                                |
| Default Port   | 22                                 |

---

# Step 1: Generate SSH Key Pair

Run the following command on the client machine:

```bash
ssh-keygen -t rsa -b 4096
```

OR using modern ED25519 encryption:

```bash
ssh-keygen -t ed25519
```

Press Enter to save keys in default location:

```bash
~/.ssh/id_rsa
```

Generated files:

| File       | Purpose     |
| ---------- | ----------- |
| id_rsa     | Private Key |
| id_rsa.pub | Public Key  |

---

# Step 2: Copy Public Key to Remote Server

## Method 1: Using ssh-copy-id (Recommended)

```bash
ssh-copy-id user@server-ip
```

Example:

```bash
ssh-copy-id admin@192.168.1.10
```

---

## Method 2: Manual Method

Create SSH directory on remote server:

```bash
mkdir -p ~/.ssh
chmod 700 ~/.ssh
```

Append public key:

```bash
cat id_rsa.pub >> ~/.ssh/authorized_keys
```

Set permissions:

```bash
chmod 600 ~/.ssh/authorized_keys
```

---

# Step 3: Login Using SSH Key

```bash
ssh user@server-ip
```

Example:

```bash
ssh admin@192.168.1.10
```

If configured correctly, password prompt will not appear.

---

# Step 4: Disable Password Authentication (Optional but Recommended)

Edit SSH configuration:

```bash
sudo vi /etc/ssh/sshd_config
```

Update following parameters:

```ini
PubkeyAuthentication yes
PasswordAuthentication no
PermitRootLogin no
```

Restart SSH service:

## RHEL / CentOS / OEL

```bash
sudo systemctl restart sshd
```

## Ubuntu / Debian

```bash
sudo systemctl restart ssh
```

---

# Verify SSH Connectivity

Run:

```bash
ssh -v user@server-ip
```

Verbose output helps troubleshoot authentication issues.

---

# Common Troubleshooting

## Permission Issues

Correct permissions are mandatory:

```bash
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

---

## SELinux Issues (RHEL/OEL)

Restore security context:

```bash
restorecon -Rv ~/.ssh
```

---

## SSH Service Status

Check SSH daemon:

```bash
systemctl status sshd
```

---

# Security Best Practices

* Never share private keys
* Use passphrase-protected keys
* Disable root login
* Disable password authentication
* Rotate keys periodically
* Use ED25519 where supported

---

# Useful SSH Commands

| Command     | Description          |
| ----------- | -------------------- |
| ssh         | Remote login         |
| ssh-keygen  | Generate SSH keys    |
| ssh-copy-id | Copy public key      |
| scp         | Secure file copy     |
| sftp        | Secure file transfer |
| ssh-add     | Add key to SSH agent |
| ssh -v      | Debug SSH connection |

---

# Automation Use Cases

* Ansible passwordless authentication
* Automated deployments
* Remote server administration
* Backup automation
* CI/CD pipelines
* Infrastructure orchestration

---

# Author

Abdul Rehan

GitHub Repository:
https://github.com/rehanadm/Linux_Tutorials
