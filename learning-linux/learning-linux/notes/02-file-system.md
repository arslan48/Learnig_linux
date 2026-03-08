# 02 - File System

How the Linux file system is structured and how to navigate it.

---

## Directory Structure

Linux uses a single root `/` — everything starts from here, unlike Windows which uses drive letters (C:, D:).

```
/
├── bin/        # Essential user commands (ls, cp, mv)
├── boot/       # Boot loader files, kernel
├── dev/        # Device files (hard drives, USB, etc.)
├── etc/        # System configuration files
├── home/       # User home directories (/home/arslan)
├── lib/        # Shared libraries
├── media/      # Mount point for removable drives
├── mnt/        # Temporary mount points
├── opt/        # Optional/third-party software
├── proc/       # Virtual filesystem for running processes
├── root/       # Home directory of root user
├── sbin/       # System administration commands
├── tmp/        # Temporary files (cleared on reboot)
├── usr/        # User programs and data
└── var/        # Variable data (logs, databases, mail)
```

---

## Absolute vs Relative Paths

**Absolute path** — starts from root `/`:
```bash
cd /home/arslan/Documents
```

**Relative path** — starts from current location:
```bash
cd Documents
cd ../Downloads
```

---

## Hidden Files

Files starting with `.` are hidden in Linux.

```bash
ls -a           # Show hidden files
ls -la          # Show hidden files with details
```

Examples of hidden files:
- `.bashrc` — shell configuration
- `.ssh/` — SSH keys folder
- `.gitconfig` — Git configuration

---

## File Types

In Linux, everything is treated as a file.

| Symbol | Type |
|--------|------|
| `-` | Regular file |
| `d` | Directory |
| `l` | Symbolic link |
| `b` | Block device |
| `c` | Character device |

Check using `ls -la` — the first character shows the type.

---

## Links

```bash
ln file.txt hardlink.txt        # Hard link
ln -s file.txt softlink.txt     # Symbolic (soft) link
```

Symbolic links are like shortcuts. Hard links point directly to the same data on disk.

---

## Disk and Storage

```bash
df -h               # Show disk usage of all mounted filesystems
du -sh foldername   # Show size of a specific folder
lsblk               # List all block devices (drives, partitions)
mount               # Show all mounted filesystems
```
