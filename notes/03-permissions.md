# 03 - Permissions

Linux uses a permission system to control who can read, write, or execute files.

---

## Permission Structure

Every file has three permission groups:

```
-rwxr-xr--
```

| Character | Meaning |
|-----------|---------|
| `-` | File type (- = file, d = directory) |
| `rwx` | Owner permissions |
| `r-x` | Group permissions |
| `r--` | Others permissions |

---

## Permission Types

| Letter | Symbol | Meaning |
|--------|--------|---------|
| Read | r | View file content / list directory |
| Write | w | Modify file / create files in directory |
| Execute | x | Run file as program / enter directory |

---

## Viewing Permissions

```bash
ls -l file.txt
# Output: -rw-r--r-- 1 arslan arslan 1024 Mar 8 12:00 file.txt
```

---

## chmod — Changing Permissions

### Using Numbers (Octal)

| Number | Permission |
|--------|------------|
| 7 | rwx |
| 6 | rw- |
| 5 | r-x |
| 4 | r-- |
| 0 | --- |

```bash
chmod 755 file.sh       # Owner: rwx, Group: r-x, Others: r-x
chmod 644 file.txt      # Owner: rw-, Group: r--, Others: r--
chmod 600 secret.txt    # Owner: rw-, Group: ---, Others: ---
```

### Using Letters

```bash
chmod +x script.sh      # Add execute for everyone
chmod u+w file.txt      # Add write for owner only
chmod o-r file.txt      # Remove read from others
chmod g=r file.txt      # Set group permission to read only
```

---

## chown — Changing Ownership

```bash
chown arslan file.txt               # Change owner
chown arslan:arslan file.txt        # Change owner and group
chown -R arslan foldername/         # Change ownership recursively
```

---

## sudo — Run as Root

```bash
sudo command            # Run command as root
sudo -i                 # Open root shell
su username             # Switch to another user
```

Common use cases:
```bash
sudo apt update
sudo chmod 755 /etc/somefile
sudo chown root:root /etc/config
```

---

## Special Permissions

```bash
chmod +s file       # Setuid / Setgid bit
chmod +t /tmp       # Sticky bit (only owner can delete their files)
```

Sticky bit is commonly set on shared directories like `/tmp`.
