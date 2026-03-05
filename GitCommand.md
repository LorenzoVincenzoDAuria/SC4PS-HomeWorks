# Guide: Connecting a Remote Linux Folder to GitHub & Git Cheat Sheet

This guide explains how to connect a local directory on an AlmaLinux virtual machine to a GitHub repository using SSH, along with a quick reference for common Git commands.

## 1. Install and Configure Git (AlmaLinux)
First, ensure Git is installed and configured with your GitHub credentials.

```bash
# Update packages and install Git
sudo dnf update -y
sudo dnf install git -y

# Configure your Git profile
git config --global user.name "YourGitHubUsername"
git config --global user.email "your.email@example.com"
```

## 2. Set Up SSH Authentication
To securely push and pull code without entering a password every time, use an SSH key.

```bash
# Generate a new SSH key (press Enter to accept default prompts)
ssh-keygen -t ed25519 -C "your.email@example.com"

# Display the public key
cat ~/.ssh/id_ed25519.pub
```
**Action required:** Copy the output of the last command, go to your GitHub account settings -> **SSH and GPG keys** -> **New SSH key**, and paste the key there.

## 3. Initialize and Connect the Repository
Navigate to your project folder on the virtual machine and connect it to GitHub.

```bash
cd /path/to/your/project_folder

# Initialize the local directory as a Git repository
git init

# Rename the default branch to 'main'
git branch -M main

# Link your local folder to the GitHub repository
# IMPORTANT: Replace the URL with your actual GitHub SSH link
git remote add origin git@github.com:YourUsername/YourRepositoryName.git
```

---

## 4. Everyday Git Commands (Cheat Sheet)

Here is a quick reference for the most common Git commands you will use during development:

### Checking Status
Always check the status of your files before committing.
```bash
git status
```

### Adding Files (Staging)
Add files to the staging area to prepare them for a commit.
```bash
# Add a specific file
git add filename.c

# Add all changed files in the current directory
git add .
```

### Committing Changes
Save your staged changes with a descriptive message.
```bash
git commit -m "Your descriptive commit message here"
```

### Pushing Code
Send your committed local changes to the remote GitHub repository.
```bash
# Push to the main branch (use -u the very first time to set the upstream)
git push -u origin main

# For all subsequent pushes, you can just use:
git push
```

### Pulling and Fetching Updates
Retrieve updates from GitHub to your local machine.
```bash
# Fetch downloads the latest changes from the remote without merging them
git fetch origin

# Pull downloads the latest changes AND merges them into your current branch
git pull origin main
```

### Viewing History
Look at the history of your previous commits.
```bash
# Full commit history
git log

# A compact, one-line version of the history
git log --oneline
```
