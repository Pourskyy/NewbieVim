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

#### Activating the Environment Automatically
```bash
# Add activation command to your bashrc
echo 'source ~/.config/py_env/default_env/bin/activate' >> ~/.bashrc

# Reload your bashrc
source ~/.bashrc
```

#### Verifying Neovim Python Integration
> Look for the **python / pip / venv** status
```bash
# Open Neovim
nvim

# Check Neovim health
:checkhealth
```

#### Installing Python Packages
> You can install packages either from the terminal or within Neovim `CMD`

```bash
# Install packages from terminal
pip install requests

# Install packages from within Neovim
:!pip install requests
```


