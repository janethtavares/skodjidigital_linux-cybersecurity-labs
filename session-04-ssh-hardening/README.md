# Linux & Cybersecurity – Module 5
## Session 4 – SSH Hardening and Secure Remote Access

### Objective

The goal of this lab was to strengthen SSH security by applying security best practices, including:

- Creating a new user
- Generating SSH key pairs
- Configuring passwordless authentication
- Disabling root login
- Disabling password authentication
- Validating and restarting the SSH service

---

## Environment

- Platform: KillerCoda Ubuntu Playground
- Operating System: Ubuntu 24.04
- User: root

---

# Step 1 – Create a New User

Command:

```bash
adduser teste
```

A new user named **teste** was created.

---

# Step 2 – Generate SSH Key Pair

Command:

```bash
ssh-keygen -t ed25519
```

An Ed25519 public/private key pair was generated.

---

# Step 3 – Copy the Public Key

Command:

```bash
ssh-copy-id teste@localhost
```

The public SSH key was copied to the authorized keys of the new user.

---

# Step 4 – Backup SSH Configuration

Command:

```bash
cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak
```

A backup of the SSH configuration file was created.

---

# Step 5 – Harden SSH Configuration

The following settings were configured:

```text
Port 2222
PermitRootLogin no
PasswordAuthentication no
```

These settings:

- Change the default SSH port.
- Disable root login.
- Disable password authentication.
- Enforce key-based authentication.

---

# Step 6 – Validate Configuration

Command:

```bash
sshd -t
```

The configuration was successfully validated without syntax errors.

---

# Step 7 – Restart SSH Service

Command:

```bash
systemctl restart ssh
```

The SSH service restarted successfully.

Verification:

```bash
systemctl status ssh
```

Status:

```
Active: active (running)
```

---

# Commands Used

```bash
adduser teste

ssh-keygen -t ed25519

ssh-copy-id teste@localhost

cp /etc/ssh/sshd_config /etc/ssh/sshd_config.bak

nano /etc/ssh/sshd_config

sshd -t

systemctl restart ssh

systemctl status ssh
```

---

# Skills Practiced

- User management
- SSH authentication
- Public/Private Key Authentication
- SSH Hardening
- Linux System Administration
- SSH Service Validation
- Configuration Management

---

# Conclusion

This lab demonstrated how to secure SSH access using industry best practices. By replacing password authentication with SSH keys, disabling root login, and validating the SSH service configuration, the system becomes significantly more resistant to brute-force attacks and unauthorized access.
