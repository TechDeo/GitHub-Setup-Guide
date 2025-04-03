# GitHub Setup Guide 🚀

A comprehensive step-by-step guide on installing Git, setting up SSH authentication, and connecting to GitHub for seamless version control.

## 📌 Introduction

This repository provides detailed instructions on how to install Git, configure your Git environment, set up SSH authentication, and connect your local machine to GitHub. Whether you're a beginner or looking to refresh your knowledge, this guide will help you establish a solid Git workflow.

## 📖 Table of Contents

- [Installation](#-installation)
- [Configuring Git](#-configuring-git)
- [Generating SSH Key](#-generating-ssh-key)
- [Connecting to GitHub](#-connecting-to-github)
- [Basic Git Commands](#-basic-git-commands)
- [Common Git Workflows](#-common-git-workflows)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)

## 🔧 Installation

Follow the instructions below to install Git on your system:

### Windows

1. Download and install Git from [git-scm.com](https://git-scm.com/download/win)
2. During installation, select "Use Git from the Windows Command Prompt"
3. Open Command Prompt or Git Bash and verify installation:
   ```
   git --version
   ```

### macOS

Using Homebrew:
```bash
brew install git
```

Or download the installer from [git-scm.com](https://git-scm.com/download/mac)

### Linux (Ubuntu/Debian)

```bash
sudo apt update && sudo apt install git
```

Verify installation:
```bash
git --version
```

## 🛠 Configuring Git

After installation, set up your Git user details:

```bash
git config --global user.name "YourGitHubUsername"
git config --global user.email "your-email@example.com"
```

To check your configuration:

```bash
git config --global --list
```

Additional recommended configurations:

```bash
# Set default branch name
git config --global init.defaultBranch main

# Set default editor (replace with your preferred editor)
git config --global core.editor "code --wait"  # For VS Code

# Enable colorful output
git config --global color.ui auto
```

## 🔑 Generating SSH Key

To authenticate with GitHub securely, generate an SSH key:

```bash
ssh-keygen -t ed25519 -C "your-email@example.com"
```
(Use `ssh-keygen -t rsa -b 4096 -C "your-email@example.com"` for older systems)

Press Enter to save the key in the default location (`~/.ssh/`).

### Starting the SSH Agent

```bash
# For macOS and Linux
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519  # or id_rsa for RSA keys

# For Windows (Git Bash)
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519  # or id_rsa for RSA keys
```

### Adding SSH Key to GitHub

1. Copy the key:
   ```bash
   # For macOS
   pbcopy < ~/.ssh/id_ed25519.pub
   
   # For Linux
   cat ~/.ssh/id_ed25519.pub
   
   # For Windows (Git Bash)
   cat ~/.ssh/id_ed25519.pub | clip
   ```
   
2. Go to GitHub → Settings → SSH and GPG Keys
3. Click "New SSH key", give it a descriptive title (e.g., "Work Laptop"), paste the copied key, and save

### Test SSH Connection

```bash
ssh -T git@github.com
```

Expected output:
```
Hi YourGitHubUsername! You've successfully authenticated, but GitHub does not provide shell access.
```

## 🔗 Connecting to GitHub

### Create a Repository on GitHub

1. Go to [GitHub](https://github.com) and sign in
2. Click "New Repository" and name it (e.g., "git-setup-guide")
3. Choose public or private visibility
4. (Optional) Add a README, .gitignore, and license
5. Copy the SSH repository URL: `git@github.com:YourGitHubUsername/repository-name.git`

### Clone an Existing Repository

```bash
git clone git@github.com:YourGitHubUsername/repository-name.git
cd repository-name
```

### Initialize a Local Repository and Push to GitHub

```bash
# Navigate to your project folder
cd path/to/your/project

# Initialize Git
git init

# Stage files
git add .

# Commit changes
git commit -m "Initial commit"

# Rename the branch to main
git branch -M main

# Link to GitHub
git remote add origin git@github.com:YourGitHubUsername/repository-name.git

# Push to GitHub
git push -u origin main
```

## 📝 Basic Git Commands

```bash
# Check repository status
git status

# Add all changes
git add .

# Add specific file
git add filename.txt

# Commit changes
git commit -m "Descriptive commit message"

# Push changes to GitHub
git push origin main

# Pull latest changes
git pull origin main

# View commit history
git log

# View simplified commit history
git log --oneline

# Create a new branch
git checkout -b branch-name

# Switch branches
git checkout branch-name

# Merge a branch into current branch
git merge branch-name

# Fetch updates from remote without merging
git fetch origin
```

## 🔄 Common Git Workflows

### Feature Branch Workflow

```bash
# Create a feature branch
git checkout -b feature/new-feature

# Make changes and commit
git add .
git commit -m "Add new feature"

# Push to GitHub
git push -u origin feature/new-feature

# Create a pull request on GitHub

# After PR is approved and merged, switch back to main
git checkout main
git pull origin main
```

### Handle Merge Conflicts

```bash
# When conflicts arise during merge
git status  # To see conflicted files
# Edit files to resolve conflicts
git add .  # Mark as resolved
git commit  # Complete the merge
```

## ❓ Troubleshooting

### Authentication Issues

- Verify your SSH key is added to GitHub
- Ensure SSH agent is running: `eval "$(ssh-agent -s)"`
- Add your key to the agent: `ssh-add ~/.ssh/id_ed25519`
- Test connection: `ssh -T git@github.com`

### Failed Push

If you can't push changes due to remote changes:
```bash
git pull --rebase origin main
git push origin main
```

### Undo Last Commit

```bash
# Keep changes but undo commit
git reset --soft HEAD~1

# Discard changes and undo commit
git reset --hard HEAD~1
```

## 🤝 Contributing

Feel free to open issues or submit pull requests to improve this guide!

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/improvement`
3. Commit your changes: `git commit -m 'Add some improvement'`
4. Push to the branch: `git push origin feature/improvement`
5. Open a Pull Request

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

🔗 Author: [TechDeo](https://github.com/TechDeo)  
📅 Last Updated: 2025-04-03
