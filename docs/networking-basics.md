# Networking and System Basics

This guide covers fundamental concepts of computers, networking, and servers that every power user should understand.

---

## Table of Contents

1. [Computer Fundamentals](#computer-fundamentals)
2. [Operating Systems](#operating-systems)
3. [Networking Basics](#networking-basics)
4. [IP Addresses and DNS](#ip-addresses-and-dns)
5. [Ports and Protocols](#ports-and-protocols)
6. [Servers and Services](#servers-and-services)
7. [Network Security](#network-security)
8. [Practical Networking Commands](#practical-networking-commands)
9. [Cloud Computing Basics](#cloud-computing-basics)

---

## Computer Fundamentals

### Hardware Components

| Component | Function |
|-----------|----------|
| **CPU** | Central Processing Unit - executes instructions |
| **RAM** | Random Access Memory - temporary fast storage |
| **Storage** | HDD/SSD - permanent data storage |
| **Motherboard** | Connects all components |
| **GPU** | Graphics Processing Unit - visual processing |
| **NIC** | Network Interface Card - network connectivity |
| **PSU** | Power Supply Unit - provides power |

### Storage Types

| Type | Speed | Durability | Cost |
|------|-------|------------|------|
| HDD | Slower | Moving parts | Lower |
| SSD | Fast | No moving parts | Medium |
| NVMe | Fastest | No moving parts | Higher |

### Memory vs Storage

- **RAM (Memory):** Fast, temporary, lost when powered off
- **Storage (Disk):** Slower, permanent, persists after power off

---

## Operating Systems

### What is an Operating System?

The OS manages hardware resources and provides services for programs:

- **Process management:** Running programs
- **Memory management:** Allocating RAM
- **File system:** Organizing stored data
- **Device drivers:** Hardware communication
- **User interface:** GUI or CLI

### Windows

Windows is the most common desktop operating system, used for:

- Desktop computing
- Gaming
- Enterprise environments
- Development

---

## Networking Basics

### What is a Network?

A network connects devices to share resources and communicate.

### Network Types

| Type | Description | Example |
|------|-------------|---------|
| **LAN** | Local Area Network | Home/office network |
| **WAN** | Wide Area Network | Internet |
| **WLAN** | Wireless LAN | WiFi network |
| **VPN** | Virtual Private Network | Secure remote connection |

### OSI Model (Simplified)

| Layer | Name | Function | Example |
|-------|------|----------|---------|
| 7 | Application | User interface | HTTP, FTP |
| 4 | Transport | Reliable delivery | TCP, UDP |
| 3 | Network | Routing | IP |
| 2 | Data Link | Local delivery | Ethernet, WiFi |
| 1 | Physical | Actual transmission | Cables, signals |

### Network Devices

| Device | Function |
|--------|----------|
| **Router** | Connects networks, assigns IPs |
| **Switch** | Connects devices in a LAN |
| **Modem** | Converts signals for ISP |
| **Access Point** | Provides WiFi |
| **Firewall** | Filters network traffic |

---

## IP Addresses and DNS

### IP Addresses

Every device on a network has an IP address:

**IPv4:** `192.168.1.100` (4 billion addresses)
**IPv6:** `2001:0db8:85a3:0000:0000:8a2e:0370:7334` (practically unlimited)

### Private vs Public IPs

| Type | Range | Use |
|------|-------|-----|
| **Private** | 10.x.x.x, 172.16-31.x.x, 192.168.x.x | Internal network |
| **Public** | Everything else | Internet-facing |

### Special Addresses

| Address | Meaning |
|---------|---------|
| `127.0.0.1` | Localhost (your machine) |
| `0.0.0.0` | All interfaces |
| `255.255.255.255` | Broadcast |

### DNS (Domain Name System)

DNS translates domain names to IP addresses:

```text
google.com → 142.250.80.46
```

**DNS Lookup Process:**

1. Browser checks cache
2. Asks local DNS resolver
3. Resolver queries root servers
4. Follows chain to authoritative server
5. Returns IP address

### Common DNS Records

| Record | Purpose | Example |
|--------|---------|---------|
| **A** | IPv4 address | `example.com → 93.184.216.34` |
| **AAAA** | IPv6 address | `example.com → 2606:2800:220:1:...` |
| **CNAME** | Alias | `www.example.com → example.com` |
| **MX** | Mail server | `example.com → mail.example.com` |
| **TXT** | Text info | SPF, DKIM records |

---

## Ports and Protocols

### What are Ports?

Ports identify specific services on a device. Think of IP as a building address and port as an apartment number.

### Common Ports

| Port | Service | Protocol |
|------|---------|----------|
| 20/21 | FTP | File transfer |
| 22 | SSH | Secure shell |
| 23 | Telnet | Remote access (insecure) |
| 25 | SMTP | Email sending |
| 53 | DNS | Name resolution |
| 80 | HTTP | Web (unencrypted) |
| 443 | HTTPS | Web (encrypted) |
| 3306 | MySQL | Database |
| 5432 | PostgreSQL | Database |
| 6379 | Redis | Cache/database |
| 27017 | MongoDB | Database |

### TCP vs UDP

| TCP | UDP |
|-----|-----|
| Connection-oriented | Connectionless |
| Reliable, ordered | Fast, no guarantees |
| Web, email, file transfer | Streaming, gaming, DNS |

---

## Servers and Services

### What is a Server?

A server is a computer that provides services to other computers (clients):

- **Web server:** Serves websites (Apache, Nginx)
- **Database server:** Stores data (MySQL, PostgreSQL)
- **File server:** Shares files (NFS, Samba)
- **Mail server:** Handles email (Postfix, Exchange)

### Web Server Basics

**Request/Response Cycle:**

1. Client sends HTTP request
2. Server processes request
3. Server returns response
4. Client renders content

### Common Server Software

| Type | Software |
|------|----------|
| **Web Server** | Nginx, Apache, Caddy |
| **Application** | Node.js, Python/Gunicorn, Ruby/Puma |
| **Database** | MySQL, PostgreSQL, MongoDB |
| **Cache** | Redis, Memcached |
| **Reverse Proxy** | Nginx, HAProxy, Traefik |

### Process Management

```bash
# List running processes
ps aux

# Find specific process
ps aux | grep nginx

# Kill process
kill PID
kill -9 PID  # Force kill

# System services
systemctl status nginx
systemctl start nginx
systemctl stop nginx
systemctl restart nginx
systemctl enable nginx  # Start on boot
```

---

## Network Security

### Firewalls

Firewalls filter network traffic based on rules:

```bash
# UFW (Ubuntu)
sudo ufw enable
sudo ufw allow 22    # Allow SSH
sudo ufw allow 80    # Allow HTTP
sudo ufw deny 23     # Block Telnet
sudo ufw status

# iptables (Low-level)
sudo iptables -L     # List rules
```

### HTTPS/TLS

HTTPS encrypts web traffic:

1. **Certificate:** Proves server identity
2. **Encryption:** Protects data in transit
3. **Integrity:** Detects tampering

**Free certificates:** Let's Encrypt

### Security Best Practices

1. **Keep systems updated**
2. **Use strong passwords/keys**
3. **Enable firewalls**
4. **Use HTTPS everywhere**
5. **Minimize open ports**
6. **Regular backups**
7. **Monitor logs**

---

## Practical Networking Commands

### Connectivity Testing

```powershell
# Check if host is reachable
ping google.com
ping -n 4 google.com  # 4 pings only

# Trace route to host
tracert google.com
```

### DNS Lookup

```powershell
# Basic lookup
nslookup google.com
```

### Network Information

```powershell
# Show IP configuration
ipconfig
ipconfig /all  # Detailed information

# Show routing table
route print

# Show active connections
netstat -an    # All connections
netstat -b     # Show process names (requires admin)
```

### Testing Ports

```powershell
# Check if port is open using PowerShell
Test-NetConnection hostname -Port 80

# Or using telnet (if enabled)
telnet hostname 80
```

### Download and Transfer

```powershell
# Download file using PowerShell
Invoke-WebRequest -Uri https://example.com/file.zip -OutFile file.zip

# Test HTTP endpoint
Invoke-WebRequest -Uri https://example.com -Method Head
```

---

## Cloud Computing Basics

### What is Cloud Computing?

Cloud computing provides on-demand computing resources over the internet.

### Service Models

| Model | Description | Examples |
|-------|-------------|----------|
| **IaaS** | Infrastructure | AWS EC2, Azure VMs, GCP Compute |
| **PaaS** | Platform | Heroku, Google App Engine |
| **SaaS** | Software | Gmail, Dropbox, Salesforce |

### Major Cloud Providers

| Provider | Services |
|----------|----------|
| **AWS** | Most extensive, market leader |
| **Azure** | Microsoft, enterprise focus |
| **GCP** | Google, data/ML focus |
| **DigitalOcean** | Developer-friendly, simpler |
| **Linode** | Simple, affordable VPS |

### Common Cloud Services

| Category | AWS | Azure | GCP |
|----------|-----|-------|-----|
| Compute | EC2 | VMs | Compute Engine |
| Storage | S3 | Blob Storage | Cloud Storage |
| Database | RDS | SQL Database | Cloud SQL |
| Serverless | Lambda | Functions | Cloud Functions |
| Containers | ECS/EKS | AKS | GKE |

### Key Concepts

| Term | Description |
|------|-------------|
| **Virtual Machine** | Simulated computer on physical hardware |
| **Container** | Lightweight, isolated application environment |
| **Load Balancer** | Distributes traffic across servers |
| **CDN** | Caches content at edge locations |
| **Auto-scaling** | Automatically adjusts resources |

---

## Quick Reference

### Network Troubleshooting Checklist

1. **Check physical connection** (cables, WiFi)
2. **Verify IP configuration** (`ip addr`, `ipconfig`)
3. **Test local connectivity** (`ping gateway`)
4. **Test internet connectivity** (`ping 8.8.8.8`)
5. **Test DNS resolution** (`ping google.com`)
6. **Check specific service** (`curl`, `telnet`)
7. **Review firewall rules**
8. **Check service status** (`systemctl status`)
9. **Review logs** (`/var/log/`)

### Essential Commands Cheatsheet

```powershell
# Network info
ipconfig                   # Show IP addresses
ipconfig /all              # Detailed network info
route print                # Show routes

# Connectivity
ping -n 4 host             # Test connectivity
tracert host               # Trace route

# DNS
nslookup domain            # DNS lookup

# Ports/Services
netstat -an                # Show all connections
Test-NetConnection host -Port port  # Test port
```

---

## Further Resources

- **Networking Fundamentals:** [networklessons.com](https://networklessons.com/)
- **Windows Networking:** [docs.microsoft.com/windows-server/networking](https://docs.microsoft.com/en-us/windows-server/networking/)
- **Cloud Computing Basics:** [aws.amazon.com/getting-started](https://aws.amazon.com/getting-started/)
- **DNS Explained:** [howdns.works](https://howdns.works/)
- **Security Best Practices:** [owasp.org](https://owasp.org/)

---

**Happy networking!** 🌐
