# NewbieVim
## STEP BY STEP NEOVIM & UBUNTU GUIDE
- Do not copy-paste comments in command line

## Contents table:
> You can skip parts, it is mostly for `first-timer`
* [WSL SETUP](#wsl-setup) `Windows Subsystem for Linux`
* [QUICK TRICK FOR WSL USERS](#quick-access-to-wsl-files)
* [PREREQUISITES](#prerequisites)
* [GIT SETUP](#git-setup)
* [NEOVIM](#neovim)

## WSL SETUP
Windows Subsystem for Linux allows you to run a Linux environment directly on Windows without a virtual machine.

### Installation
> Open windows command-line shell `CMD`
```bash
# Check existing WSL distributions
wsl --list --verbose

# Start Ubuntu distribution
wsl -d Ubuntu

# Exit WSL
exit

# View available distributions online
wsl --list --online

# Update and upgrade packages
sudo apt update && sudo apt upgrade
```

### Navigation and Setup Tips
> Inside WSL in Ubuntu `CMD`
```bash
# Return to home directory
cd ~

# Copy files from Windows to WSL
cp /mnt/c/Users/your-username/somefile.txt ~

# View all files including hidden ones
ls -a
```

### Quick Access to WSL Files
Create a shortcut at: `C:/Windows/System32/wsl.exe ~`

### Create Script to Open WSL in File Explorer
> Inside WSL in Ubuntu `CMD`
```bash
# Create the script
echo 'explorer.exe .' > ~/open-home.sh

# Make it executable
chmod +x ~/open-home.sh

# Run it anytime to open current directory
~/open-home.sh
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

### Programming Languages and Dependencies
> Inside WSL in Ubuntu `CMD`

Neovim and its plugins often require additional programming languages and tools. Here's what you might need:

#### Lua (for Neovim configuration)
```bash
# Install Lua and LuaRocks
sudo apt install luarocks

```

### Additional Tools for Development

> **Note**: You don't need to install all of these languages and tools at once. Start with the ones needed for your immediate tasks, and add others as needed.

#### Python
```bash
# Install Python and pip
sudo apt install -y python3 python3-pip

# Install Neovim Python module
pip3 install pynvim
```

#### Node.js and npm
```bash
# Install Node.js and npm using nvm (Node Version Manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.5/install.sh | bash

# Reload shell configuration
source ~/.bashrc

# Install latest LTS version of Node.js
nvm install --lts

# Install Neovim Node.js provider
npm install -g neovim
```

#### Rust
```bash
# Install Rust using rustup
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Add Rust to your path (follow the instructions from the installer)
source $HOME/.cargo/env
```

#### Go
```bash
# Install Go
sudo apt install -y golang

# Set up Go environment variables
echo 'export GOPATH=$HOME/go' >> ~/.bashrc
echo 'export PATH=$PATH:/usr/local/go/bin:$GOPATH/bin' >> ~/.bashrc
source ~/.bashrc
```

#### Zig
```bash
# Download latest Zig release
wget https://ziglang.org/download/0.11.0/zig-linux-x86_64-0.11.0.tar.xz

# Extract the archive
tar -xf zig-linux-x86_64-0.11.0.tar.xz

# Move to /usr/local
sudo mv zig-linux-x86_64-0.11.0 /usr/local/zig

# Add to PATH
echo 'export PATH=$PATH:/usr/local/zig' >> ~/.bashrc
source ~/.bashrc
```

## GIT SETUP

### Basic Configuration
> Inside WSL in Ubuntu `CMD`
> You may want to use your github `EMAIL`
> - Go to GitHub → Settings → Emails
> - Look for something like:
> - your-github-username@users.noreply.github.com
```bash
# Set username and email
git config --global user.name "name"
git config --global user.email "email"

# Verify configuration
git config --get user.name
git config --get user.email

# Remove configuration settings if needed
git config --unset key    # Remove single setting
git config --unset-all key    # Remove all instances

# View all Git configurations
cat ~/.gitconfig

# Set default branch name
git config --global init.defaultBranch master
```

### Configuration Levels
Git has four configuration levels, each overriding the previous one:

1. **System** (`/etc/gitconfig`): Configures Git for all users on the system
2. **Global** (`~/.gitconfig`): Configures Git for all projects of a user
3. **Local** (`.git/config`): Configures Git for a specific project
4. **Worktree** (`.git/config.worktree`): Configures Git for part of a project

### Creating and Managing a Repository
```bash
# Create and initialize a new repository
mkdir project-name
cd project-name
git init

# Check repository status
git status
```

### Understanding File States
- **Untracked**: Not being tracked by Git
- **Staged**: Marked for inclusion in the next commit
- **Committed**: Saved to the repository's history

### Committing Changes
> Inside WSL in Ubuntu `CMD`
```bash
# Add specific file to staging
git add filename.txt

# Add all untracked/modified files
git add .

# Commit staged changes
git commit -m "Your descriptive message"

# Update the most recent commit
git commit --amend -m "Updated commit message"
```

### Viewing History
```bash
# View commit history
git log

# View limited number of commits without pager
git log -n 5 --no-pager
```

### Working with Remotes
```bash
# Add a remote repository
git remote add origin https://github.com/username/repository.git

# Push to remote repository
git push -u origin master

# Pull from remote repository
git pull origin master
```

## NEOVIM
> **Note**: for clarity, all the shortcuts and keymaping will be inside the file name

### Basic Usage

#### Starting Neovim
```bash
# Open Neovim
nvim

# Open a specific file
nvim filename.md

# Open multiple files in tabs
nvim -p file1.md file2.md file3.md
```

#### Essential

Neovim operates in different modes:

**Normal Mode** 'n' (default when you open Neovim):

**Insert Mode** 'i' (for typing text):

**Command Mode** ':' (accessing by pressing esc and then :)

### Setting Up Neovim Configuration

Neovim configuration is stored in `~/.config/nvim/` directory:

```bash
# Create Neovim config directory
mkdir -p ~/.config/nvim

# Create init.vim or init.lua file
touch ~/.config/nvim/init.vim
# OR
touch ~/.config/nvim/init.lua
```

