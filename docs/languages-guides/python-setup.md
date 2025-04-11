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
