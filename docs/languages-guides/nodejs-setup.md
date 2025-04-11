### Node.js and NPM Setup

> Many Neovim plugins require Node.js and npm (Node Package Manager)  
> Inside WSL / Ubuntu `CMD`  

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
Look for the **Node.js provider** status in the health check output
