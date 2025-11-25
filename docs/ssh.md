# SSH and Remote Access Guide

This guide covers SSH (Secure Shell) and remote access tools for securely connecting to and managing remote systems.

---

## Table of Contents

1. [What is SSH?](#what-is-ssh)
2. [SSH Installation](#ssh-installation)
3. [Basic SSH Usage](#basic-ssh-usage)
4. [SSH Key Authentication](#ssh-key-authentication)
5. [SSH Configuration](#ssh-configuration)
6. [File Transfer](#file-transfer)
7. [SSH Tunneling](#ssh-tunneling)
8. [Remote Desktop Options](#remote-desktop-options)
9. [Security Best Practices](#security-best-practices)
10. [Troubleshooting](#troubleshooting)

---

## What is SSH?

SSH (Secure Shell) is a cryptographic network protocol for secure communication between computers. It provides:

- **Encrypted connections:** All data is encrypted in transit
- **Authentication:** Password or key-based authentication
- **Remote command execution:** Run commands on remote machines
- **File transfer:** Securely copy files between systems
- **Port forwarding:** Tunnel traffic through encrypted connections

---

## SSH Installation

### Windows

**Windows 10/11 (Built-in):**

```powershell
# Check if OpenSSH is installed
Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'

# Install OpenSSH Client
Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
```

**Alternatively:** Install [Git for Windows](https://git-scm.com/download/win) which includes SSH.

### macOS

SSH is pre-installed. Open Terminal to use.

### Linux

```bash
# Ubuntu/Debian
sudo apt update
sudo apt install openssh-client

# For SSH server
sudo apt install openssh-server
```

---

## Basic SSH Usage

### Connecting to a Remote Server

```bash
# Basic connection
ssh username@hostname

# Connect with specific port
ssh -p 2222 username@hostname

# Connect with IP address
ssh username@192.168.1.100
```

### Common Connection Options

| Option | Description |
|--------|-------------|
| `-p port` | Specify port number |
| `-i keyfile` | Use specific private key |
| `-v` | Verbose output (debugging) |
| `-X` | Enable X11 forwarding |
| `-L` | Local port forwarding |
| `-R` | Remote port forwarding |

### Running Commands Remotely

```bash
# Run single command
ssh username@hostname "ls -la"

# Run multiple commands
ssh username@hostname "cd /var/log && tail -100 syslog"

# Run command with sudo
ssh username@hostname "sudo systemctl status nginx"
```

---

## SSH Key Authentication

SSH keys provide more secure authentication than passwords.

### Generating SSH Keys

```bash
# Generate RSA key (4096 bits recommended)
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

# Generate Ed25519 key (modern, recommended)
ssh-keygen -t ed25519 -C "your_email@example.com"
```

**Prompts:**

1. File location (default: `~/.ssh/id_rsa` or `~/.ssh/id_ed25519`)
2. Passphrase (optional but recommended)

### Key Files

| File | Description |
|------|-------------|
| `~/.ssh/id_rsa` | Private key (keep secret!) |
| `~/.ssh/id_rsa.pub` | Public key (share this) |
| `~/.ssh/authorized_keys` | Server file containing allowed public keys |
| `~/.ssh/known_hosts` | Cached server fingerprints |

### Copying Key to Server

```bash
# Using ssh-copy-id (easiest)
ssh-copy-id username@hostname

# Manual method
cat ~/.ssh/id_rsa.pub | ssh username@hostname "mkdir -p ~/.ssh && cat >> ~/.ssh/authorized_keys"
```

### Using SSH Keys with GitHub

```bash
# Copy public key to clipboard
# Windows
clip < ~/.ssh/id_ed25519.pub

# macOS
pbcopy < ~/.ssh/id_ed25519.pub

# Linux
xclip -selection clipboard < ~/.ssh/id_ed25519.pub
```

Then add the key in GitHub: Settings → SSH and GPG keys → New SSH key.

---

## SSH Configuration

The SSH config file (`~/.ssh/config`) simplifies connections.

### Example Configuration

```bash
# GitHub
Host github.com
    HostName github.com
    User git
    IdentityFile ~/.ssh/github_ed25519

# Work server
Host work
    HostName work.example.com
    User developer
    Port 22
    IdentityFile ~/.ssh/work_rsa

# Jump host configuration
Host production
    HostName 10.0.0.50
    User admin
    ProxyJump jumphost

Host jumphost
    HostName jump.example.com
    User admin
```

### Usage with Config

```bash
# Instead of: ssh developer@work.example.com
ssh work

# Instead of: git clone git@github.com:user/repo.git
# Just works with the config
```

### SSH Agent

SSH agent manages your keys and passphrases.

```bash
# Start SSH agent
eval "$(ssh-agent -s)"

# Add key to agent
ssh-add ~/.ssh/id_ed25519

# List loaded keys
ssh-add -l

# Remove all keys from agent
ssh-add -D
```

---

## File Transfer

### SCP (Secure Copy)

```bash
# Copy file to remote
scp file.txt username@hostname:/path/to/destination/

# Copy file from remote
scp username@hostname:/path/to/file.txt ./local/

# Copy directory recursively
scp -r folder/ username@hostname:/path/to/destination/

# With specific port
scp -P 2222 file.txt username@hostname:/path/
```

### SFTP (SSH File Transfer Protocol)

```bash
# Start SFTP session
sftp username@hostname

# SFTP commands
put local_file.txt          # Upload
get remote_file.txt         # Download
ls                          # List remote files
lls                         # List local files
cd directory                # Change remote directory
lcd directory               # Change local directory
mkdir directory             # Create remote directory
exit                        # Quit
```

### Rsync (Efficient Sync)

```bash
# Sync local to remote
rsync -avz folder/ username@hostname:/path/to/destination/

# Sync remote to local
rsync -avz username@hostname:/path/to/source/ ./local/

# Options
# -a: archive mode (preserves permissions, timestamps)
# -v: verbose
# -z: compress during transfer
# --delete: delete files not in source
# --dry-run: test without making changes
```

---

## SSH Tunneling

SSH tunnels create encrypted connections for other traffic.

### Local Port Forwarding

Access a remote service through a local port:

```bash
# Forward local port 8080 to remote localhost:80
ssh -L 8080:localhost:80 username@hostname

# Access database through tunnel
ssh -L 3307:localhost:3306 username@dbserver
# Now connect to localhost:3307 to reach remote MySQL
```

### Remote Port Forwarding

Expose local service to remote:

```bash
# Make local port 3000 available on remote port 8080
ssh -R 8080:localhost:3000 username@hostname
```

### Dynamic Port Forwarding (SOCKS Proxy)

```bash
# Create SOCKS proxy on local port 1080
ssh -D 1080 username@hostname

# Configure browser to use localhost:1080 as SOCKS proxy
```

---

## Remote Desktop Options

For graphical access to remote systems:

### RDP (Remote Desktop Protocol) - Windows

**Connect from Windows:**

1. Open "Remote Desktop Connection"
2. Enter computer name or IP
3. Click Connect

**Connect from macOS/Linux:**

```bash
# Install Remmina (Linux)
sudo apt install remmina remmina-plugin-rdp

# Or use Microsoft Remote Desktop (macOS)
```

### VNC (Virtual Network Computing)

```bash
# Install VNC server (Linux)
sudo apt install tightvncserver

# Start VNC server
vncserver :1

# Connect via SSH tunnel (secure)
ssh -L 5901:localhost:5901 username@hostname
# Then connect VNC client to localhost:5901
```

### VS Code Remote SSH

Use VS Code's Remote SSH extension:

1. Install "Remote - SSH" extension
2. Open Command Palette (`Ctrl+Shift+P`)
3. Select "Remote-SSH: Connect to Host"
4. Enter `username@hostname`

---

## Security Best Practices

### Server Configuration

Edit `/etc/ssh/sshd_config`:

```bash
# Disable root login
PermitRootLogin no

# Disable password authentication
PasswordAuthentication no

# Use only SSH protocol 2
Protocol 2

# Limit users
AllowUsers alice bob

# Change default port (optional)
Port 2222
```

Restart SSH after changes:

```bash
sudo systemctl restart sshd
```

### Client Best Practices

1. **Use SSH keys instead of passwords**
2. **Protect private keys:** Set permissions to `600`
3. **Use passphrases on keys**
4. **Verify server fingerprints**
5. **Keep software updated**
6. **Use fail2ban to block brute force attacks**

### Key Permissions

```bash
# Fix key permissions
chmod 700 ~/.ssh
chmod 600 ~/.ssh/id_rsa
chmod 644 ~/.ssh/id_rsa.pub
chmod 600 ~/.ssh/config
chmod 600 ~/.ssh/authorized_keys
```

---

## Troubleshooting

### Common Issues

**Connection refused:**

```bash
# Check if SSH service is running
sudo systemctl status sshd

# Check firewall
sudo ufw status
```

**Permission denied:**

```bash
# Verify key permissions
ls -la ~/.ssh/

# Check server logs
sudo tail -f /var/log/auth.log
```

**Host key verification failed:**

```bash
# Remove old key
ssh-keygen -R hostname

# Or manually edit known_hosts
```

### Debugging

```bash
# Verbose output
ssh -v username@hostname

# More verbose
ssh -vv username@hostname

# Maximum verbosity
ssh -vvv username@hostname
```

---

## Further Resources

- **OpenSSH Manual:** [man.openbsd.org/ssh](https://man.openbsd.org/ssh)
- **SSH Academy:** [ssh.com/academy](https://www.ssh.com/academy/)
- **GitHub SSH Documentation:** [docs.github.com/en/authentication/connecting-to-github-with-ssh](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)
- **SSH Hardening Guide:** [mozilla.github.io/ssh/](https://infosec.mozilla.org/guidelines/openssh)

---

**Happy connecting!** 🔐
