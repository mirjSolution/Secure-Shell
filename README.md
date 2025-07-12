# 🔐 SSH (Secure Shell)

This repository contains summarized notes and usage examples of **SSH (Secure Shell)**. SSH is a secure protocol that allows users to access and control remote servers.

---

## 📘 What is SSH?

**SSH (Secure Shell)** is a cryptographic network protocol for operating network services securely over an unsecured network.

Use cases:

- Securely connect to remote servers
- Transfer files using `scp` or `sftp`
- Execute remote commands or scripts
- Administer cloud or physical infrastructure

---

## 🔑 SSH Authentication Methods

### 1. **Username & Password**

- Traditional way to authenticate.
- Used when a user is created on the remote server.
- Less secure and requires manual input.

### 2. **SSH Key Pairs (Public/Private)**

- Recommended authentication method.
- **Private Key** stays on the client machine (e.g id_rsa).
- **Public Key** is copied to the remote server under `~/.ssh/authorized_keys` (e.g id_rsa_pub).
- More secure and supports automation.

---

## ⚙️ How SSH Works

1. Client runs: `ssh user@remote_ip`
2. Server listens on **port 22** by default.
3. If connection is allowed by firewall:
   - The server authenticates the client (via password or key).
   - SSH session is established.
4. You can now control the remote machine’s CLI.

---

## 🔐 Generating SSH Keys

```bash
# Generate SSH key pair using RSA
ssh-keygen -t rsa

# Default location: ~/.ssh/id_rsa (private), ~/.ssh/id_rsa.pub (public)
```

![SSH Image](Images/ssh.png)

```bash
# Check .ssh folder
ls. ssh
```

![SSH Image1](Images/ssh1.png)

---

## 📁 Setting Up SSH Access on Remote Server

### Add your public key to the remote server:

```bash
# On the remote server
mkdir -p ~/.ssh
nano ~/.ssh/authorized_keys

# Paste your public key here and save
```

### Or use `ssh-copy-id` (if available):

```bash
ssh-copy-id -i ~/.ssh/id_rsa.pub user@remote_ip
```

---

## 🔗 Connecting via SSH

```bash
# Standard connection
ssh user@remote_ip

# Specify a key (if not using default)
ssh -i ~/.ssh/my_custom_key user@remote_ip
```

---

## 📂 Copying Files via SCP

```bash
# Syntax: scp <source> <user@remote_host>:<destination_path>
scp test.sh root@192.168.1.10:/root/
```

---

## 🚀 Running Remote Scripts

```bash
# SSH into the remote server
ssh root@192.168.1.10

# Make script executable
chmod +x test.sh

# Execute it
./test.sh
```

---

## 🧱 Firewall Considerations

- Port **22** must be open on the server.
- Restrict access to specific IP addresses when possible.
- Use cloud platform firewalls or `ufw`/`iptables`.

---

## 📤 Optional: Delete DigitalOcean Server

To avoid billing, you can destroy the droplet after use:

```bash
# On DigitalOcean UI
Go to Droplets → Select Droplet → Destroy
```

---

## 💡 Summary

- SSH is essential for DevOps work and remote server management.
- SSH key pairs are secure and automate authentication.
- SCP allows secure file transfers.
- SSH is a foundational skill for deploying, managing, and automating infrastructure.

🧑‍💻 _Created by Rico John Dato-on_  
🔗 [LinkedIn](https://www.linkedin.com/in/rico-john-dato-on) • [Portfolio](https://ricodatoon.netlify.app)
