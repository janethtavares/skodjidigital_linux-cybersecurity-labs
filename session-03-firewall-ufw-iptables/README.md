# Session 03 – Firewall Configuration with UFW and iptables

## Objective

The objective of this lab was to practice basic firewall configuration in Linux using UFW (Uncomplicated Firewall) and iptables.

The exercise focused on configuring firewall policies, allowing SSH access, blocking a specific IP address, verifying firewall rules, and saving the iptables configuration.

## Environment

- Ubuntu 24.04
- KillerCoda Ubuntu Playground
- UFW
- iptables

## 1. Checking UFW Status

The initial firewall status was checked using:

```bash
sudo ufw status
```

Initially, UFW was inactive.

## 2. Configuring Default Firewall Policies

Incoming connections were denied by default:

```bash
sudo ufw default deny incoming
```

Outgoing connections were allowed:

```bash
sudo ufw default allow outgoing
```

This configuration blocks unsolicited incoming traffic while allowing normal outbound communication.

## 3. Allowing SSH Traffic

SSH access through TCP port 22 was allowed using:

```bash
sudo ufw allow 22/tcp
```

## 4. Enabling and Verifying UFW

The firewall was enabled with:

```bash
sudo ufw enable
```

The configuration was verified using:

```bash
sudo ufw status verbose
```

The result confirmed:

- UFW status: active
- Incoming traffic: deny by default
- Outgoing traffic: allow by default
- SSH (22/tcp): allowed

## 5. Blocking a Specific IP with iptables

A rule was created to block incoming traffic from the IP address `203.0.113.50`:

```bash
sudo iptables -A INPUT -s 203.0.113.50 -j DROP
```

The rule was verified using:

```bash
sudo iptables -L -v
```

The output confirmed a `DROP` rule for traffic originating from `203.0.113.50`.

## 6. Saving the iptables Rules

The directory for storing the rules was created:

```bash
sudo mkdir -p /etc/iptables
```

The current iptables configuration was saved using:

```bash
sudo iptables-save | sudo tee /etc/iptables/rules.v4
```

The saved file was verified with:

```bash
sudo ls -l /etc/iptables/rules.v4
```

The output confirmed that `/etc/iptables/rules.v4` was successfully created.

## Key Learnings

During this lab, I learned how to:

- Check and configure the UFW firewall.
- Define default incoming and outgoing traffic policies.
- Allow SSH traffic through TCP port 22.
- Enable and verify firewall rules.
- Create an iptables rule to block traffic from a specific IP address.
- Inspect active iptables rules.
- Export and save the current iptables configuration.

## Conclusion

This lab provided practical experience with two important Linux firewall management tools: UFW and iptables.

UFW provides a simpler interface for managing common firewall policies, while iptables allows more granular control over network traffic. The exercise also demonstrated the importance of verifying firewall rules after configuration and saving the resulting configuration for later use.
