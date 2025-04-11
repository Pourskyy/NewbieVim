# NewbieVim
## STEP BY STEP NEOVIM & UBUNTU GUIDE
- Do not copy-paste comments in command line

```bash
NEWBIEVIM/
├── README.md                  # Main landing page with overview
├── docs/                      # Documentation directory
│   ├── wsl-setup.md           # WSL installation and configuration
│   ├── ubuntu-basics.md       # Ubuntu prerequisites and setup
│   ├── git-github-setup.md    # Git and GitHub configuration
│   ├── neovim-setup.md        # Neovim installation and plugins
│   └── language-guides/       # Subdirectory for programming languages
│       ├── python-setup.md    # Python specific setup
│       ├── nodejs-setup.md    # Node.js specific setup
│       └── rust-setup.md      # Other languages as needed
├── config-files/              # Example configuration files
│   ├── .bashrc                # Example bashrc file
│   ├── init.vim               # Example Neovim config
│   └── .gitconfig             # Example Git config
└── scripts/                   # Helpful scripts
    ├── setup-wsl.sh           # Automation script for WSL setup
    └── install-deps.sh        # Script to install dependencies
```
## Contents table:
> You can skip parts, it is mostly for `first-timer`
* [WSL SETUP](/docs/wsl-setup.md) `Windows Subsystem for Linux`
* [QUICK TRICK FOR WSL USERS](#quick-access-to-wsl-files)
* [PREREQUISITES](#prerequisites)
* [GIT SETUP](/git-github-setup.md)
* [NEOVIM](/neovim-setup.md)

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
> Inside WSL in Ubuntu `CMD`\
> You may want to use your github `EMAIL`
> - Go to GitHub → Settings → Emails
> - Look for something like: your-github-username@users.noreply.github.com
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
# Set main for GitHub
git config --global init.defaultBranch main
```

### Configuration Levels
Git has four configuration levels, each overriding the previous one:

1. **System** (`/etc/gitconfig`): configures Git for all users on the system
2. **Global** (`~/.gitconfig`): configures Git for all projects of a user
3. **Local** (`.git/config`): configures Git for a specific project
4. **Worktree** (`.git/config.worktree`): configures Git for part of a project

### Creating and Managing a Repository
```bash
# Create and initialize a new repository
mkdir project-name
cd project-name
git init

# Check repository status
git status
```

#### Understanding File States
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
# Add a remote repository FOR GITHUB CLI
git remote add origin https://github.com/username/repository.git

# Add a remote repository FOR GIT
git remote add origin git@github.com:username/repository.git

# Push to remote repository
git push -u origin master

# Pull from remote repository
git pull origin master
```

## NEOVIM
> **Note**: for clarity, all the shortcuts and keymaping will be inside [`keymaps.txt`](#keymaps.txt)

**Basic Usage**

#### Starting Neovim
```bash
# Open Neovim
nvim

# Open a specific file
nvim filename.md

# Open multiple files in tabs
nvim -p file1.md file2.md file3.md
```

#### Essential Mods

> Neovim operates in different modes:

- **Normal Mode** 'n' (default when you open Neovim)

- **Insert Mode** 'i' (for typing text)

- **Command Mode** ':' (accessing by pressing esc and then ':')

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

## Development Environment Setup

### Python Setup

After installing Neovim, you'll need to set up Python for various plugins and development tasks.

#### Checking Python Installation
```bash
# Verify Python version
python3 --version

# Check Python location
which python3
# Output will typically show: /usr/bin/python3
```

#### Creating a Python Virtual Environment
Virtual environments let you manage Python packages separately for different projects.

```bash
# Install necessary packages
sudo apt update
sudo apt install python3-pip
sudo apt install python3-venv

# Create directory for Python environments
cd ~/.config
mkdir py_env
cd py_env

# Create a default virtual environment
python3 -m venv default_env
```

#### Activating the Environment Automatically
```bash
# Add activation command to your bashrc
echo 'source ~/.config/py_env/default_env/bin/activate' >> ~/.bashrc

# Reload your bashrc
source ~/.bashrc
```

#### Verifying Neovim Python Integration
```bash
# Open Neovim
nvim

# Check Neovim health
:checkhealth
```
Look for the **python / pip / venv** status in the health check output.

#### Installing Python Packages
You can install packages either from the terminal or within Neovim:

```bash
# Install packages from terminal
pip install requests

# Install packages from within Neovim
:!pip install requests
```

### Node.js and NPM Setup

Many Neovim plugins require Node.js and npm (Node Package Manager).

#### Checking Node.js Installation
```bash
# Check Node.js version
node --version

# Check npm version
npm --version
```

#### Installing Node.js and npm
```bash
# Update package lists
sudo apt update

# Install Node.js and npm
sudo apt install nodejs npm
```

#### Configuring npm Global Installation Path
This avoids permission issues when installing global packages:

```bash
# Create directory for global packages
mkdir -p ~/.npm-global

# Configure npm to use the new directory
npm config set prefix '~/.npm-global'

# Add the directory to PATH
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc

# Apply changes
source ~/.bashrc
```

#### Installing npm Packages
You can install packages globally or locally to a project:

```bash
# Install packages globally (available system-wide)
npm install -g package-name

# Install packages locally (project-specific)
cd ~/my_project

# Initialize a new Node.js project (creates package.json)
npm init -y

# Install and save dependency to package.json
npm install package_name --save
```

#### Node.js for Neovim Plugins
Many Neovim plugins require the Neovim Node.js provider:

```bash
# Install Neovim Node.js provider
npm install -g neovim

# Verify installation in Neovim
:checkhealth
```
Look for the **Node.js provider** status in the health check output.
