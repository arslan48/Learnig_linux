# 07 - Package Management (pacman)

pacman is the package manager used on Arch Linux and Arch-based systems (Manjaro, EndeavourOS, etc.). It handles installing, updating, and removing software.

---

## Basic Commands

```bash
sudo pacman -Sy                     # Refresh package database
sudo pacman -Syu                    # Full system upgrade (sync + upgrade)
sudo pacman -S packagename          # Install a package
sudo pacman -R packagename          # Remove a package (keep dependencies)
sudo pacman -Rs packagename         # Remove package + unneeded dependencies
sudo pacman -Rns packagename        # Remove package, deps, and config files
sudo pacman -Sc                     # Remove old cached packages
```

---

## Searching

```bash
pacman -Ss keyword                  # Search for packages in repos
pacman -Si packagename              # Show details about a repo package
pacman -Qs keyword                  # Search installed packages
pacman -Qi packagename              # Show details about installed package
pacman -Q                           # List all installed packages
pacman -Qu                          # List packages with available updates
```

---

## Common Workflow

```bash
sudo pacman -Syu
```

Always sync + upgrade together. Running `-Su` without `-Sy` can cause partial upgrades — which Arch explicitly warns against.

---

## pacman Flags Cheat Sheet

| Flag | Meaning |
|------|---------|
| `-S` | Sync (install from repo) |
| `-R` | Remove |
| `-Q` | Query (local database) |
| `-U` | Upgrade (install local `.pkg.tar.zst`) |
| `-F` | File database search |
| `y` | Refresh package database |
| `u` | Upgrade installed packages |
| `s` | Search |
| `i` | Info |
| `q` | Quiet output |
| `n` | Also remove config files (with `-R`) |

---

## Installing Local Packages

For manually downloaded `.pkg.tar.zst` files:

```bash
sudo pacman -U /path/to/package.pkg.tar.zst
```

---

## AUR — Arch User Repository

The AUR contains community-maintained packages not in the official repos. You need an AUR helper to use it easily.

### Using yay (most popular AUR helper)

```bash
yay -S packagename                  # Install from AUR or official repos
yay -Syu                            # Upgrade everything including AUR
yay -Ss keyword                     # Search AUR + official repos
yay -R packagename                  # Remove a package
```

### Installing yay itself

```bash
sudo pacman -S --needed git base-devel
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```

---

## Package Cache

```bash
sudo pacman -Sc                     # Remove old cached package versions
sudo pacman -Scc                    # Remove entire package cache (be careful)
du -sh /var/cache/pacman/pkg/       # Check cache size
```

---

## Orphaned Packages

```bash
pacman -Qdt                         # List orphaned packages (unneeded deps)
sudo pacman -Rns $(pacman -Qdtq)    # Remove all orphans
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
| `fastfetch` | System info display (neofetch successor) |
| `base-devel` | Build tools (gcc, make, etc.) — needed for AUR |