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

## Zsh Functions

| Function | Description | Code |
|----------|-------------|------|
| `posix-source` | Function to source POSIX-style environment files | ```bash<br>posix-source() {<br>  while IFS= read -r line; do<br>    if [[ $line =~ ^[[:space:]]*# ]] \|\| [[ -z $line ]]; then<br>      continue<br>    fi<br>    export "$line"<br>  done < "$1"<br>}``` |

## Environment Variables

| Variable | Value | Description |
|----------|-------|-------------|
| `EDITOR` | `nvim` | Default editor |
| `SHELL` | `/etc/profiles/per-user/${username}/bin/zsh` | Default shell |

## Zsh Plugins

| Plugin | Description |
|--------|-------------|
| **zsh-autosuggestions** | Provides command suggestions based on history |
| **zsh-syntax-highlighting** | Highlights commands as you type |

## Git Configuration

### Delta Options

| Option | Value | Description |
|--------|-------|-------------|
| `line-numbers` | `true` | Show line numbers in diffs |
| `side-by-side` | `true` | Use side-by-side diff view |
| `navigate` | `true` | Enable navigation in diffs |

### Git Settings

| Setting | Value | Description |
|---------|-------|-------------|
| `push.default` | `"current"` | Push current branch by default |
| `push.autoSetupRemote` | `true` | Automatically set up remote tracking |
| `merge.conflictstyle` | `"diff3"` | Use diff3 conflict style |
| `diff.colorMoved` | `"default"` | Color moved lines in diffs |

## Starship Prompt Configuration

| Module | Status | Value | Description |
|--------|--------|-------|-------------|
| AWS | Disabled | - | AWS module |
| GCloud | Disabled | - | Google Cloud module |
| Kubernetes | Enabled | - | Kubernetes module |
| Git branch style | - | `242` | Git branch styling |
| Directory style | - | `blue` | Directory styling |
| Directory truncation | - | `8` | Directory truncation length |
| Python | Disabled | - | Python module |
| Ruby | Disabled | - | Ruby module |
| Hostname style | - | `bold green` | Hostname styling |

## Tools Integration

| Tool | Status | Description | Options |
|------|--------|-------------|---------|
| **FZF** | Enabled | Provides fuzzy finding capabilities | Zsh integration |
| **LSD** | Enabled | Modern `ls` replacement with better formatting | Aliases enabled |
| **Zoxide** | Enabled | Smart directory jumping | `--cmd cd` |
| **Broot** | Enabled | Interactive tree view and file manager | Zsh integration |
| **Direnv** | Enabled | Automatic environment loading for projects | nix-direnv enabled |

## NixOS WSL Configuration

### WSL Settings

| Setting | Value | Description |
|---------|-------|-------------|
| Automount root | `/mnt` | WSL automount root directory |
| Windows path integration | Disabled | Include Windows PATH in WSL |
| Host generation | Disabled | Generate hosts file |
| Start menu launchers | Enabled | Create start menu shortcuts |
| Docker Desktop integration | Disabled | Docker Desktop integration |

### Docker

| Setting | Value | Description |
|---------|-------|-------------|
| Docker on boot | Enabled | Start Docker on system boot |
| Auto-prune | Enabled | Automatically clean up Docker resources |

## System Packages

### Unstable Packages (Bleeding Edge)

| Package | Description |
|---------|-------------|
| bat | Better cat command |
| bottom | System monitor |
| coreutils | Core utilities |
| curl | HTTP client |
| du-dust | Disk usage analyzer |
| fd | Find alternative |
| findutils | Find utilities |
| fx | JSON viewer |
| git | Version control |
| git-crypt | Git encryption |
| htop | Process monitor |
| jq | JSON processor |
| killall | Process killer |
| mosh | SSH alternative |
| procs | Process viewer |
| ripgrep | Text searcher |
| sd | String replacer |
| tmux | Terminal multiplexer |
| tree | Directory tree |
| unzip | Archive extractor |
| wget | HTTP downloader |
| zip | Archive creator |
| lazygit | Git UI |
| btop | System monitor |

### Stable Packages

| Package | Description |
|---------|-------------|
| nixvim | Custom Neovim configuration |
| nitch | System information display |
| mkcert | Certificate generator |
| httpie | HTTP client |
| tree-sitter | Syntax highlighting |
| vscode-langservers-extracted | HTML, CSS, JSON, ESLint language servers |
| yaml-language-server | YAML language server |
| nil | Nix language server |
| alejandra | Nix formatter |
| deadnix | Nix linter |
| prettier | Code formatter |
| shellcheck | Shell script linter |
| shfmt | Shell script formatter |
| statix | Nix linter |

## Startup Behavior

| Behavior | Description |
|----------|-------------|
| Runs `nitch` | Display system information on shell startup |
| Disables zsh greeting | `unsetopt PROMPT_SP` |
| Sources any-nix-shell | Nix integration (commented out) |

## VS Code Integration

| Step | Action | Description |
|------|--------|-------------|
| 1 | Uncomment systemd user service block | In `wsl.nix` file |
| 2 | Replace `[my-user]` | With your Windows username |
| 3 | Adjust code binary path | If needed for your setup |

This configuration provides a comprehensive development environment with extensive shortcuts and integrations for efficient workflow management.