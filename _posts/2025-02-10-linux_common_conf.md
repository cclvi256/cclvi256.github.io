---
title: Common Configurations for Linux
date: 2025-02-10 20:00:00 +0800
categories:
  - Linux
tags:
  - Linux
  - System Configuration
  - System Administration
math: true
---

## Install Common Packages

For Red Hat based systems: 

```bash
sudo dnf install -y git gcc gcc-c++ llvm clang lldb make cmake tmux htop btop zsh neovim curl
```

For Arch based systems:

```bash
sudo pacman -Syu git gcc llvm clang lldb make cmake tmux htop btop zsh neovim curl
```

For Debian based systems:

```bash
sudo apt update
sudo apt install -y git gcc g++ llvm clang lldb make cmake tmux htop btop zsh neovim curl
```

## Set Up ZSH

```bash
sh -c "$(curl -fsSL https://install.ohmyz.sh/)"
```

This command will automatically install oh-my-zsh and set `zsh` as the default shell.
After these are done, you will get into a zsh session.
Then install the `zsh-autosuggestions` and `zsh-syntax-highlighting` plugins:

```zsh
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Next, edit the `~/.zshrc` file:

```zsh
plugins=(
  git
  zsh-autosuggestions
  zsh-syntax-highlighting
)
```

On my own opinion, I will also change the theme to `candy` and then set the `HYPHEN_INSENSITIVE` option to `true`:

```zsh
ZSH_THEME="candy"
HYPHEN_INSENSITIVE="true"
```

I like the most simple locale settings, so I will also change locale to `C.UTF-8`. If this is my own device. If this machine is not mine, I will set this in my `~/.zshrc`:

```zsh
export LC_ALL=C.UTF-8
```

## TMUX Configuration

You can see the TMUX help document by pressing `Ctrl + B` (abbrev. `C-b`) and then `?`.

By default, TMUX have no mouse support. You can enable it temporarily by pressing `C-b` and then `:` to enter the command mode, then type `set -g mouse on` and press Enter.

If you want to enable mouse support permanently, you can add the following line to your `~/.tmux.conf`:

```tmux
set -g mouse on
```
