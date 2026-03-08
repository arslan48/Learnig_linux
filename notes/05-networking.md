# 05 - Networking

Basic networking commands for checking connectivity, interfaces, and troubleshooting.

---

## Network Interfaces

```bash
ip a                    # Show all network interfaces and IPs
ip link                 # Show link layer info
ifconfig                # Older command (may need net-tools installed)
```

---

## Connectivity

```bash
ping google.com             # Test connection (Ctrl+C to stop)
ping -c 4 google.com        # Ping exactly 4 times
traceroute google.com       # Show path packets take to destination
curl https://example.com    # Fetch content from a URL
wget https://example.com    # Download file from URL
```

---

## DNS

```bash
nslookup google.com     # Query DNS for a domain
dig google.com          # Detailed DNS lookup
host google.com         # Simple DNS lookup
cat /etc/resolv.conf    # View current DNS server config
```

---

## Ports and Connections

```bash
ss -tuln                # Show open ports and listening services
ss -tulnp               # Same but also show process name
netstat -tuln           # Older alternative (needs net-tools)
lsof -i :80             # See what is using port 80
```

---

## Firewall (ufw)

UFW = Uncomplicated Firewall, the default on Ubuntu.

```bash
sudo ufw status             # Check firewall status
sudo ufw enable             # Enable firewall
sudo ufw disable            # Disable firewall
sudo ufw allow 22           # Allow SSH port
sudo ufw allow 80           # Allow HTTP
sudo ufw deny 3306          # Block MySQL port
sudo ufw delete allow 80    # Remove a rule
```

---

## SSH

```bash
ssh user@192.168.1.10           # Connect to remote machine
ssh -p 2222 user@host           # Connect on custom port
ssh-keygen                      # Generate SSH key pair
ssh-copy-id user@host           # Copy public key to remote server
scp file.txt user@host:/path/   # Copy file to remote machine
```

---

## Network Config Files

| File | Purpose |
|------|---------|
| `/etc/hosts` | Local hostname to IP mapping |
| `/etc/resolv.conf` | DNS server config |
| `/etc/network/interfaces` | Network interface config (Debian-based) |
| `/etc/hostname` | Machine hostname |

---

## Download and Transfer

```bash
wget https://example.com/file.zip              # Download file
curl -O https://example.com/file.zip          # Download with curl
curl -I https://example.com                   # Fetch only HTTP headers
rsync -avz source/ user@host:/destination/    # Sync files over SSH
```
