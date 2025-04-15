### Node.js and NPM Setup

> Many Neovim plugins require Node.js and npm (Node Package Manager)  
> Inside WSL / Ubuntu `CMD`  

#### Node.js Setup Using NVM (Recommended for WSL)

When using WSL, you might encounter path conflicts with Windows Node.js installations set up Node.js using Node Version Manager (nvm)

#### Checking for Path Conflicts

> First, check if you're accidentally using Windows Node.js:

```bash
# Check which Node.js and npm executables are being used
which npm
which node

# If you see paths like /mnt/c/Program Files/nodejs/npm, you're using Windows Node.js
```

#### Fixing Path Conflicts

> If you're using Windows Node.js, remove it from your WSL path:

```bash
# Edit your .bashrc file
nano ~/.bashrc

# Add this line to remove Windows Node.js from PATH
export PATH=$(echo $PATH | sed -E 's;:/mnt/c/Program Files/nodejs;;g')

# Apply changes
source ~/.bashrc
```

#### Installing Node Version Manager (nvm)

> [!WARNING]
> `NVM` is the *recommended* way to install and manage Node.js in `UBUNTU`

```bash
# Install nvm
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash

# Close and reopen your terminal, or source your profile
source ~/.bashrc
```

#### Installing Node.js with nvm

```bash
# Install the latest LTS version of Node.js
nvm install --lts

# Set it as the default
nvm use --lts
```

#### Verifying Installation

```bash
# Check Node.js and npm versions
node -v
npm -v

# Verify installation paths (should be in ~/.nvm/...)
which node
which npm
```

#### Configuring npm Global Installation Path
> This avoids permission issues when installing global packages  

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
> You can install packages globally or locally to a project  

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
> Many Neovim plugins require the Neovim Node.js provider  

```bash
# Install Neovim Node.js provider
npm install -g neovim

# Verify installation in Neovim
:checkhealth
```
