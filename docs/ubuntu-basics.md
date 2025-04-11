## Prerequisites

Before we begin setting up Neovim and Git, we need to install some essential tools and dependencies.

### Basic Tools Installation
> Inside WSL in Ubuntu `CMD`
```bash
# Update package lists
sudo apt update

# Install Git, essential build tools, and dependencies
sudo apt install -y git make unzip gcc ripgrep xclip

# Install Neovim
sudo apt install -y neovim 

# Verify Neovim installation
nvim --version
```

### Programming Languages and Dependencies
> Inside WSL in Ubuntu `CMD`

Neovim and its plugins often require additional programming languages and tools. Here's what you might need:

#### Lua (for Neovim configuration)
```bash
# Install Lua and LuaRocks
sudo apt install luarocks

```


