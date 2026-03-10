# 08 - Cron Jobs

Cron is a time-based job scheduler in Linux. It runs commands or scripts automatically at specified times.

---

## Crontab

Each user has their own crontab file.

```bash
crontab -e          # Edit your crontab
crontab -l          # List your cron jobs
crontab -r          # Remove all your cron jobs
sudo crontab -e     # Edit root's crontab
```

---

## Cron Syntax

```
* * * * * command
│ │ │ │ │
│ │ │ │ └── Day of week  (0-7, 0 and 7 = Sunday)
│ │ │ └──── Month        (1-12)
│ │ └────── Day of month (1-31)
│ └──────── Hour         (0-23)
└────────── Minute       (0-59)
```

`*` means every — every minute, every hour, etc.

---

## Examples

```bash
# Run every minute
* * * * * /path/to/script.sh

# Run every day at 6:30 AM
30 6 * * * /path/to/script.sh

# Run every Monday at 9 AM
0 9 * * 1 /path/to/script.sh

# Run every 1st of the month at midnight
0 0 1 * * /path/to/script.sh

# Run every 15 minutes
*/15 * * * * /path/to/script.sh

# Run at 8 AM and 8 PM every day
0 8,20 * * * /path/to/script.sh

# Run Monday to Friday at 9 AM
0 9 * * 1-5 /path/to/script.sh
```

---

## Shortcuts

| Shortcut | Equivalent | Meaning |
|----------|------------|---------|
| `@reboot` | — | Run once at startup |
| `@hourly` | `0 * * * *` | Every hour |
| `@daily` | `0 0 * * *` | Every day at midnight |
| `@weekly` | `0 0 * * 0` | Every Sunday at midnight |
| `@monthly` | `0 0 1 * *` | First day of every month |

```bash
@reboot /path/to/script.sh
@daily /path/to/backup.sh
```

---

## Redirecting Output

By default cron sends output to email. Redirect to a file instead:

```bash
# Save output to a log file
* * * * * /path/to/script.sh >> /var/log/myscript.log 2>&1

# Discard all output
* * * * * /path/to/script.sh > /dev/null 2>&1
```

---

## System-wide Cron

System cron jobs are in `/etc/cron.d/` and `/etc/crontab`.

```
/etc/cron.hourly/       # Scripts here run every hour
/etc/cron.daily/        # Scripts here run every day
/etc/cron.weekly/       # Scripts here run every week
/etc/cron.monthly/      # Scripts here run every month
```

Drop a script in the right folder and it runs automatically — no crontab entry needed.

---

## Checking Cron Logs

```bash
grep CRON /var/log/syslog          # Check cron activity
grep CRON /var/log/syslog | tail   # Last few cron events
```
