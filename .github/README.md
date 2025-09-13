# NixOS-wsl

This repository is intended to be a sane, batteries-included starter template
for running a [nixvim](https://github.com/sijanthapa171/nixvim)-powered NixOS
development environment on WSL.

If you don't want to dig into NixOS too much right now, the only file you need
to concern yourself with is [home.nix](home.nix). This is where you can add and
remove binaries to your global `$PATH`.

Go to [https://search.nixos.org](https://search.nixos.org/packages) to find the
correct package names, though usually they will be what you expect them to be
in other package managers.


Make sure to look at all the `FIXME` notices in the various files which are
intended to direct you to places where you may want to make configuration
tweaks.


## Quickstart


- Get the [latest
  release](https://github.com/sijanthapa171/nixos-wsl.git)
- Install it (tweak the command to your desired paths):

```powershell
wsl --import NixOS .\NixOS\ .\nixos-wsl.tar.gz --version 2
```

- Enter the distro:

```powershell
wsl -d NixOS
```

- Get a copy of this repo (you'll probably want to fork it eventually):

```bash
git clone https://github.com/sijanthapa171/nixos-wsl.git /tmp/configuration
cd /tmp/configuration
```

- Change the username to your desired username in `flake.nix` with `nvim` (or
  whichever editor you prefer)
- Install `win32yank` with `scoop` and add it to your `$PATH` in NixOS
- Apply the configuration and shutdown the WSL2 VM

```bash
sudo nixos-rebuild switch --flake /tmp/configuration && sudo shutdown -h now
```

- Reconnect to the WSL2 VM

```bash
wsl -d NixOS
```

```bash
mv /tmp/configuration ~/configuration
```

- Go through all the `FIXME:` notices in `~/configuration` and make changes
  wherever you want
- Apply the configuration

```bash
sudo nixos-rebuild switch --flake ~/configuration
```

# Keymaps and Shortcuts

This document outlines all the keymaps, shortcuts, and aliases configured in this NixOS WSL setup.

## Shell Aliases (Zsh)

### Navigation Shortcuts

| Alias | Description | Command |
|-------|-------------|---------|
| `..` | Go up one directory | `cd ..` |
| `...` | Go up two directories | `cd ../../` |
| `....` | Go up three directories | `cd ../../../` |
| `.....` | Go up four directories | `cd ../../../../` |

### Utility Functions

| Alias | Description | Command |
|-------|-------------|---------|
| `refresh` | Reload zsh configuration | `source $HOME/.zshrc` |
| `take` | Create directory and navigate to it | `mkdir -p "$1" && cd "$1"` |
| `ttake` | Navigate to temporary directory | `cd $(mktemp -d)` |
| `show_path` | Display PATH variable formatted | `echo $PATH | tr ' ' '\n'` |

### Git Shortcuts

| Alias | Description | Command |
|-------|-------------|---------|
| `gapa` | Git add with patch | `git add --patch` |
| `grpa` | Git reset with patch | `git reset --patch` |
| `gst` | Git status | `git status` |
| `gdh` | Git diff HEAD | `git diff HEAD` |
| `gp` | Git push | `git push` |
| `gph` | Git push upstream | `git push -u origin HEAD` |
| `gco` | Git checkout | `git checkout` |
| `gcob` | Git checkout new branch | `git checkout -b` |
| `gcm` | Git checkout master | `git checkout master` |
| `gcd` | Git checkout develop | `git checkout develop` |
| `gsp` | Git stash push with message | `git stash push -m` |
| `gsa` | Git stash apply | `git stash apply stash^{/` |
| `gsl` | Git stash list | `git stash list` |
| `lg` | LazyGit | `lazygit` |

### Editor and Tools

| Alias | Description | Command |
|-------|-------------|---------|
| `nv` | Neovim | `nvim` |
| `lvim` | Neovim | `nvim` |

### Windows Integration (WSL)

| Alias | Description | Command |
|-------|-------------|---------|
| `pbcopy` | Copy to Windows clipboard | `/mnt/c/Windows/System32/clip.exe` |
| `pbpaste` | Paste from Windows clipboard | `/mnt/c/Windows/System32/WindowsPowerShell/v1.0/powershell.exe -command 'Get-Clipboard'` |
| `explorer` | Open Windows Explorer | `/mnt/c/Windows/explorer.exe` |

### Nix Shortcuts

| Alias | Description | Command |
|-------|-------------|---------|
| `gc` | Nix garbage collection | `sudo nix-collect-garbage -d` |
| `sysup` | System update | `sudo nixos-rebuild switch --flake ~/configuration` |
| `n` | Show system info | `nitch` |

### General Utilities

| Alias | Description | Command |
|-------|-------------|---------|
| `md` | Make directory | `mkdir` |
| `cls` | Clear screen | `clear` |