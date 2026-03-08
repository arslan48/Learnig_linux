# 04 - Processes

A process is a running instance of a program. Linux gives full control over managing them.

---

## Viewing Processes

```bash
ps              # Show processes in current terminal session
ps aux          # Show all running processes for all users
top             # Live process monitor (press q to quit)
htop            # Better version of top (may need to install)
```

### ps aux columns explained

| Column | Meaning |
|--------|---------|
| USER | Who started the process |
| PID | Process ID (unique number) |
| %CPU | CPU usage percentage |
| %MEM | Memory usage percentage |
| COMMAND | The command that started the process |

---

## Finding a Process

```bash
ps aux | grep firefox       # Find firefox process
pgrep firefox               # Get PID of firefox directly
pidof firefox               # Same as pgrep
```

---

## Killing Processes

```bash
kill PID                # Send default signal (SIGTERM) to process
kill -9 PID             # Force kill (SIGKILL) — cannot be ignored
killall firefox         # Kill all processes named firefox
pkill firefox           # Same as killall
```

Common signals:

| Signal | Number | Meaning |
|--------|--------|---------|
| SIGTERM | 15 | Graceful termination (default) |
| SIGKILL | 9 | Force kill immediately |
| SIGHUP | 1 | Reload configuration |

---

## Background and Foreground Jobs

```bash
command &           # Run command in background
jobs                # List background jobs
fg                  # Bring last background job to foreground
fg %1               # Bring job number 1 to foreground
bg                  # Resume a stopped job in background
Ctrl + Z            # Pause/suspend current foreground job
Ctrl + C            # Kill current foreground job
```

---

## Process Priority (nice)

Lower nice value = higher priority. Range is -20 (highest) to 19 (lowest).

```bash
nice -n 10 command          # Start command with nice value 10
renice -n 5 -p PID          # Change priority of running process
```

---

## System Resource Usage

```bash
free -h             # RAM usage
vmstat              # Virtual memory statistics
iostat              # CPU and disk I/O statistics
lscpu               # CPU information
nproc               # Number of CPU cores
```
