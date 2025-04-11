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


