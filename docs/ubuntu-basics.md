## UBUNTU BASICS
> Basics commands to use Ubuntu  
> Inside WSL / Ubuntu `CMD`:
```bash
# To create and open files
nano
touch file.txt
cat > file.txt
echo "Hello World" > file.txt
printf "First line of text\nSecond line of text\n" > file.txt
```

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
> [!NOTE]  
> If you want to start with the kickstarter you need to have the version 0.10  
> In case you are below follow thise steps:  
```bash
sudo add-apt-repository ppa:neovim-ppa/unstable
sudo apt update
sudo apt install neovim

# To add the kickstarter
git clone https://github.com/nvim-lua/kickstart.nvim.git "${XDG_CONFIG_HOME:-$HOME/.config}"/nvim
```
You can finally start using neovim by typing `nvim`  
> `:` is the shortcut to access the command inside `Neovim`  
```bash
nvim
:checkhealth
```

### Programming Languages and Dependencies
> Inside WSL in Ubuntu `CMD`

Neovim and its plugins often require additional programming languages and tools. Here's what you might need:

#### Lua (for Neovim configuration)
```bash
# Install Lua and LuaRocks
sudo apt install luarocks

```

Check [Neovim Setup & Plugins](/docs/neovim-setup.md) to follow up with Neovim use
