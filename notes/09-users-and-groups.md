# 09 - User and Group Management

Linux is a multi-user system. Every file, process, and resource is owned by a user and belongs to a group.

---

## User Accounts

```bash
whoami                      # Current logged-in user
id                          # User ID, group ID and groups
id username                 # Info about a specific user
who                         # Who is logged in
w                           # Who is logged in and what they are doing
last                        # Login history
```

---

## Managing Users

```bash
sudo useradd username                   # Create a new user (basic)
sudo useradd -m username                # Create user with home directory
sudo useradd -m -s /bin/bash username   # Create user with bash shell
sudo passwd username                    # Set or change password
sudo usermod -aG groupname username     # Add user to a group
sudo userdel username                   # Delete user
sudo userdel -r username                # Delete user and home directory
```

---

## User Information Files

| File | Content |
|------|---------|
| `/etc/passwd` | List of all users |
| `/etc/shadow` | Encrypted passwords |
| `/etc/group` | List of all groups |

```bash
cat /etc/passwd             # View all users
cat /etc/group              # View all groups
getent passwd username      # Info about a specific user
```

### /etc/passwd format

```
username:x:UID:GID:comment:home:shell
arslan:x:1000:1000::/home/arslan:/bin/bash
```

---

## Managing Groups

```bash
sudo groupadd groupname             # Create a new group
sudo groupdel groupname             # Delete a group
sudo gpasswd -a username groupname  # Add user to group
sudo gpasswd -d username groupname  # Remove user from group
groups username                     # List groups a user belongs to
```

---

## Switching Users

```bash
su username             # Switch to another user
su -                    # Switch to root
sudo -i                 # Open root shell
sudo -u username cmd    # Run command as another user
exit                    # Return to previous user
```

---

## sudo Access

Users with sudo access can run commands as root.

```bash
sudo command                # Run one command as root
sudo visudo                 # Safely edit /etc/sudoers file
```

To give a user sudo access:

```bash
sudo usermod -aG sudo username
```

---

## Password Policies

```bash
sudo passwd -l username         # Lock a user account
sudo passwd -u username         # Unlock a user account
sudo passwd -e username         # Force password change on next login
chage -l username               # View password expiry info
sudo chage -M 90 username       # Set password to expire in 90 days
```
