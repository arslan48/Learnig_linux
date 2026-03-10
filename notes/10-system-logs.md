# 10 - System Logs

Linux logs everything — system events, errors, login attempts, service activity. Knowing where logs are and how to read them is essential for troubleshooting.

---

## Log Directory

All logs are stored in `/var/log/`.

```bash
ls /var/log/            # List all log files
```

### Important Log Files

| File | What it logs |
|------|--------------|
| `/var/log/syslog` | General system activity |
| `/var/log/auth.log` | Authentication, sudo, SSH logins |
| `/var/log/kern.log` | Kernel messages |
| `/var/log/dpkg.log` | Package installations via apt |
| `/var/log/boot.log` | Boot process messages |
| `/var/log/ufw.log` | Firewall activity |
| `/var/log/apache2/` | Apache web server logs |

---

## Reading Logs

```bash
cat /var/log/syslog                     # Print entire log
less /var/log/syslog                    # Scroll through log
tail /var/log/syslog                    # Last 10 lines
tail -n 50 /var/log/syslog             # Last 50 lines
tail -f /var/log/syslog                 # Follow live updates
head /var/log/syslog                    # First 10 lines
grep "error" /var/log/syslog           # Filter for errors
grep "error" /var/log/syslog -i        # Case-insensitive search
```

---

## journalctl — systemd Journal

On modern Ubuntu systems, logs are also managed by systemd via `journalctl`.

```bash
journalctl                              # All logs
journalctl -b                           # Logs since last boot
journalctl -b -1                        # Logs from previous boot
journalctl -f                           # Follow live logs
journalctl -n 50                        # Last 50 entries
journalctl -p err                       # Only errors
journalctl -u servicename              # Logs for a specific service
journalctl --since "1 hour ago"        # Logs from last hour
journalctl --since "2026-03-01"        # Logs from a specific date
```

---

## Checking Service Logs

```bash
systemctl status servicename           # Status + recent logs
journalctl -u ssh                      # SSH service logs
journalctl -u cron                     # Cron service logs
```

---

## Log Rotation

Logs are automatically rotated (compressed and archived) to prevent them from filling the disk.

Config file: `/etc/logrotate.conf`
Per-service configs: `/etc/logrotate.d/`

```bash
sudo logrotate -f /etc/logrotate.conf  # Force rotation manually
```

---

## Writing to Logs

```bash
logger "This is a test message"                        # Write to syslog
logger -t myscript "Backup completed successfully"     # With a tag
```

Useful in bash scripts to log activity:

```bash
#!/bin/bash
logger -t backup "Starting backup"
cp -r /data /backup
logger -t backup "Backup finished"
```

---

## Checking for Failed Logins

```bash
sudo grep "Failed password" /var/log/auth.log
sudo grep "Invalid user" /var/log/auth.log
lastb                                   # List bad login attempts
last                                    # List successful logins
```
