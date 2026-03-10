# 07 - Package Management (apt)

apt (Advanced Package Tool) is the package manager used on Ubuntu and Debian-based systems. It handles installing, updating, and removing software.

---

## Basic Commands

```bash
sudo apt update                     # Refresh package list from repositories
sudo apt upgrade                    # Upgrade all installed packages
sudo apt full-upgrade               # Upgrade + handle dependency changes
sudo apt install packagename        # Install a package
sudo apt remove packagename         # Remove a package (keep config files)
sudo apt purge packagename          # Remove package and config files
sudo apt autoremove                 # Remove unused dependencies
```

---

## Searching

```bash
apt search keyword                  # Search for packages by keyword
apt show packagename                # Show details about a package
apt list --installed                # List all installed packages
apt list --upgradable               # List packages with available updates
```

---

## Common Workflow

```bash
sudo apt update && sudo apt upgrade -y
```

Always run `update` before `install` — otherwise apt installs from an outdated list.

---

## dpkg — Low Level Package Tool

apt uses dpkg underneath. You can use dpkg directly for `.deb` files.

```bash
sudo dpkg -i package.deb           # Install a .deb file manually
sudo dpkg -r packagename           # Remove a package
dpkg -l                            # List all installed packages
dpkg -l | grep packagename         # Check if a package is installed
```

---

## snap — Another Package Format

Ubuntu also supports snap packages.

```bash
snap find packagename               # Search for a snap
sudo snap install packagename       # Install a snap
sudo snap remove packagename        # Remove a snap
snap list                           # List installed snaps
```

---

## Adding Repositories (PPA)

PPA = Personal Package Archive. Used to install software not in default repos.

```bash
sudo add-apt-repository ppa:user/repo
sudo apt update
sudo apt install packagename
```

To remove a PPA:

```bash
sudo add-apt-repository --remove ppa:user/repo
```

---

## Package Cache

```bash
sudo apt clean                      # Delete downloaded package files
sudo apt autoclean                  # Delete only outdated package files
du -sh /var/cache/apt/archives/     # Check cache size
```

---

## Useful Packages to Know

| Package | What it does |
|---------|--------------|
| `curl` | Transfer data from URLs |
| `wget` | Download files |
| `git` | Version control |
| `htop` | Interactive process viewer |
| `net-tools` | Networking tools (ifconfig, netstat) |
| `tree` | Show directory structure as tree |
| `unzip` | Extract zip files |
| `vim` | Terminal text editor |
| `neofetch` | System info display |
