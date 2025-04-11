## GIT

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
> The git push -u origin master command sets up the local branch to track the remote master branch, simplifying future pushes and pulls  

### GITHUB
> Two possibilities:
> **HTTPS** | **SSH**
#### GH CLI
> To understand the process you can follow [GitHub Documentation](https://github.com/cli/cli/blob/trunk/docs/install_linux.md)
> Copy and paste it in Ubuntu `CMD`:
```bash
(type -p wget >/dev/null || (sudo apt update && sudo apt-get install wget -y)) \
	&& sudo mkdir -p -m 755 /etc/apt/keyrings \
    && out=$(mktemp) && wget -nv -O$out https://cli.github.com/packages/githubcli-archive-keyring.gpg \
    && cat $out | sudo tee /etc/apt/keyrings/githubcli-archive-keyring.gpg > /dev/null \
	&& sudo chmod go+r /etc/apt/keyrings/githubcli-archive-keyring.gpg \
	&& echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/githubcli-archive-keyring.gpg] https://cli.github.com/packages stable main" | sudo tee /etc/apt/sources.list.d/github-cli.list > /dev/null \
	&& sudo apt update \
	&& sudo apt install gh -y
```
- It first checks if wget is installed and installs it if needed
- It properly creates the /etc/apt/keyrings directory if it doesn't exist
- It uses a temporary file to download the key
- It ensures proper permissions on the keyring file with chmod go+r
- It adds the -y flag to apt install commands to avoid prompting
- It combines everything into a single command chain with error handling

To login to github:
```bash
gh auth login
# The anwsers you may want to go for:
# GitHub.com
# HTTPS
# Y
# Login with a web browser
```
- Open a browser on another device (like your phone or another computer)
- Go to https://github.com/login/device
- Enter the one-time code shown (XXXX-XXXX)
- Authorize the CLI  
DONE!
##### Now let's see how to manage repository
List your repositories
```bash
gh repo list
```
Clone a repository
```bash
gh repo clone username/repository
```
Create a new repository
```bash
gh repo create repository-name
```
Fork a repository
```bash
gh repo fork username/repository
```
Working with Pull Requests
Create a pull request
```bash
gh pr create
```
List pull requests
```bash
gh pr list
```
Check out a pull request locally
```bash
gh pr checkout PR_NUMBER
```
Working with Issues
Create an issue
```bash
gh issue create
```
List issues
```bash
gh issue list
```
Other Useful Commands
View repository on GitHub
```bash
gh repo view --web
```
Create a release
```bash
gh release create TAG_NAME
```
### SSH
Go at the root `cd ~`  
- **Step 1**: Creating an SSH key
> An SSH key is like a special digital house key that lets your computer securely talk to GitHub without typing your password every time
```bash
bashCopyssh-keygen -t ed25519 -C "your_email@example.com"
```
Replace "your_email@example.com" with the email you use for GitHub 
- KeyPath: press `Enter` to accept the default location  
- Password: press `Enter` twice to leave blank password  

- **Step 2**: Starting the key manager
> This part tells your computer to keep track of your new digital key
```bash
bashCopyeval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```
> Start a program called "SSH agent" that manages your keys  
> Tell the agent about your new key so it can use it  

- **Step 3**: Viewing your public key  
> This step lets you see the public part of your key (the part you'll share with GitHub)
```bash
bashCopycat ~/.ssh/id_ed25519.pub
```
Shows the content of your public key file you'll see a long string of text that starts with "ssh-ed25519" and ends with your email this is what you'll copy to paste into GitHub in the next step  

Think of it like this: You're creating a special lock and key you keep the private key (id_ed25519) secret on your computer while sharing the matching public lock (id_ed25519.pub) with GitHub so only your computer can access your account  
> Add the SSH key to your GitHub account:

- **Step 4**: `Go to GitHub → Settings → SSH and GPG keys`  
Click `New SSH key`  
Paste your copied key and save  

- **Step 5**: Test your connection  

```bash
bashCopyssh -T git@github.com
```
- **Step 6**: Configure your Git username and email:
```bash
bashCopygit config --global user.name "Your Name"
git config --global user.email "your_email@example.com"
```
Now you can clone repositories using SSH URLs and push/pull without entering your password each time.

✅ Ensure Git is Configured to Use SSH
```bash
git config --global url."git@github.com:"
```
> **NOT** "https://github.com/"  
> Don't forget to use GitHub email:  
> Go to GitHub → Settings → Emails  
> Look for something like:  
> `your-github-username@users.noreply.github.com`
```bash
git config --global user.email
# "xxxx@users.noreply.github.com"
```

In case you need to change your author's email Inside the project  
```bash
git commit --amend --reset-author
```
