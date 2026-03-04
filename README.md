# 🚀 Terminal Efficiency: The Mac Guide

Welcome to the Terminal Efficiency interest group! This repository contains everything you need to transform your terminal from a "scary black box" into your most powerful developer tool.

## 📅 Agenda

1. **The "Bare" Shell:** What is Zsh, and why does it look so boring out of the box?
2. **Oh My Zsh (The Framework):** Going from boring to colorful in 10 seconds, and managing themes.
3. **Superpowers (Zsh Plugins):** Installing the "holy trinity" for terminal productivity:
   - *Git Plugin:* See the status of your code directly in the prompt.
   - *Syntax Highlighting:* Catch typos *before* you press Enter.
   - *Autosuggestions:* Let the terminal guess what you want to type ("Ghost text").
4. **Aliases (Custom Shortcuts):** How to create your own custom commands to save thousands of keystrokes.
5. **Q&A and "Install Party":** Setting this up on your own MacBooks!

---

## 🍏 The Install Party: Mac Setup Guide

This guide will walk you through setting up a modern, efficient terminal environment on your macOS machine. We will use `brew` (Homebrew) for almost everything to keep your system clean and easy to maintain.

### Step 0: Install Homebrew (The Package Manager)
macOS doesn't come with a built-in package manager. Homebrew fixes this, allowing us to install software directly from the command line.

Copy and paste this entire line into your terminal and press `Enter`:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Install a good text/IDE editor
   
```sh
brew install helix
```

Install Oh my Zsh

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"   
```

Install plugins for Zsh

```sh
brew install zsh-autosuggestions zsh-syntax-highlighting   
```

Enable the plugins `~/.zshrc`
```sh
hx ~/.zshrc
   
```

When you are in helix editor
```
# Navigate with `arrows`, press `I` for instert mode
# Add these line with cmd+V

source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh
source $(brew --prefix)/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh

# Esc, `:`, `wq` write and quite, then enter
```

Alias (shortcuts)
```
# My custom shortcuts

alias c="clear"
```

For usage without brew
```sh
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions


# hx ~/.zshrc
plugins=(git zsh-syntax-highlighting zsh-autosuggestions)
   
```
