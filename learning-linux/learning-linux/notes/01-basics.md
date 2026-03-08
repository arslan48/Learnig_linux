# 01 - Basic Commands

Basic Linux commands used in the terminal on a daily basis.

---

## Navigation

```bash
pwd           # Print current directory path
ls            # List files in current directory
ls -la        # List all files including hidden, with details
cd foldername # Change into a directory
cd ..         # Go back one directory
cd ~          # Go to home directory
cd /          # Go to root directory
```

---

## Files and Directories

```bash
touch file.txt          # Create an empty file
mkdir foldername        # Create a new directory
mkdir -p a/b/c          # Create nested directories
cp file.txt backup.txt  # Copy a file
mv file.txt /path/      # Move a file
mv old.txt new.txt      # Rename a file
rm file.txt             # Delete a file
rm -r foldername        # Delete a folder and its contents
```

---

## Viewing File Content

```bash
cat file.txt        # Print file content
less file.txt       # View file page by page (q to quit)
head file.txt       # Show first 10 lines
tail file.txt       # Show last 10 lines
tail -f log.txt     # Follow file updates in real time
```

---

## Searching

```bash
grep "word" file.txt        # Search for a word in a file
grep -r "word" ./folder     # Search recursively in a folder
find . -name "file.txt"     # Find a file by name
find . -type d              # Find all directories
```

---

## System Info

```bash
uname -a        # Kernel and system info
hostname        # Machine name
whoami          # Current logged-in user
date            # Current date and time
uptime          # How long system has been running
df -h           # Disk usage (human readable)
free -h         # RAM usage
```

---

## Help

```bash
man ls          # Manual page for any command
ls --help       # Short help for a command
whatis ls       # One-line description of a command
```
