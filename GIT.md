## GIT
### GITHUB
#### GH CLI
> To understand the process you can follow: https://github.com/cli/cli/blob/trunk/docs/install_linux.md
Copy and paste it in Ubuntu `CMD`:
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
#### SSH
