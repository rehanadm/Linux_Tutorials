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

# SSH Authentication Flow

```text
Client Machine
     |
     |--- Private Key Authentication --->
     |
Remote Linux Server
     |
Authorized using Public Key
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

# Useful Commands

| Command     | Description          |
| ----------- | -------------------- |
| ssh-keygen  | Generate SSH keys    |
| ssh-copy-id | Copy public key      |
| ssh-add     | Add key to SSH agent |
| ssh-agent   | Manage SSH keys      |
| ssh -v      | Debug SSH connection |

---

# Example Automation Use Cases

* Ansible passwordless authentication
* Automated backups
* CI/CD deployments
* Server orchestration
* Secure remote administration

---

# Author
Abdul Rehan

GitHub Repository:
https://github.com/rehanadm/rehanadm.github.io
