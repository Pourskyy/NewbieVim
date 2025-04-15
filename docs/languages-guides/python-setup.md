### Python Setup

After installing Neovim, feel free to set up Python  

#### Checking Python Installation
> Inside WSL / Ubuntu `CMD`  
```bash
# Verify Python version
python3 --version

# Check Python location
which python3
# Output will typically show: /usr/bin/python3
```

#### Creating a Python Virtual Environment
> Virtual environments let you manage Python packages separately for different projects  

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

After setting up your Python virtual environment, verify it's properly activated:

```bash
# Check which pip is being used
which pip

# It should point to ~/.config/py_env/default_env/bin/pip
# If it shows /usr/bin/pip or similar, the virtual environment isn't activated
```
#### Activating the Environment Automatically
> CAREFUL YOU LOAD AUTOMATICALLY IT MAY CAUSE ERRORS  
```bash
# Add activation command to your bashrc
echo 'source ~/.config/py_env/default_env/bin/activate' >> ~/.bashrc

# Reload your bashrc
source ~/.bashrc
```
For easier activation, add an alias to your `.bashrc`:

```bash
# Edit .bashrc
nano ~/.bashrc

# Add this line
alias activatep='source ~/.config/py_env/default_env/bin/activate'

# Apply changes
source ~/.bashrc

# Now you can activate your environment by typing:
activatep
```

#### Verifying Neovim Python Integration
> Look for the **python / pip / venv** status
```bash
# Open Neovim
nvim

# Check Neovim health
:checkhealth
```

#### Troubleshooting Virtual Environment Issues

> If your virtual environment isn't activating properly:

```bash
# Exit current venv if active
deactivate  

# Remove old potentially corrupted venv
rm -rf ~/.config/py_env/default_env  

# Create fresh virtual environment
python3 -m venv ~/.config/py_env/default_env

# Activate it
source ~/.config/py_env/default_env/bin/activate
```

#### Project-Specific Virtual Environments (Recommended)

For better isolation, consider using project-specific environments:

```bash
# Navigate to your project directory
cd ~/code/NewProject

# Create a virtual environment in this directory
python3 -m venv venv

# Activate it
source venv/bin/activate

# Install project dependencies
pip install requests

# When done, deactivate
deactivate
```
#### Installing Python Packages
> You can install packages either from the terminal or within Neovim `CMD`

```bash
# Install packages from terminal
pip install requests

# Install packages from within Neovim
:!pip install requests
```
