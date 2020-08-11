# data_science
Data science repository

# Introduction

This repository contains EDA and models for BoffinAI.

## Shortcuts
- [Connecting to GitHub with SSH](#connecting-to-github-with-ssh)
    - [About SSH](#about-ssh)
    - [Checking for existing SSH keys](#checking-for-existing-ssh-keys)
    - [Generating a new SSH key](#generating-a-new-ssh-key)
    - [Add your public key to GitHub](#add-your-public-key-to-github)
    - [Add your private key to the ssh-agent](#add-your-private-key-to-the-ssh-agent)
    - [Testing your SSH connectivity](#testing-your-ssh-connectivity)
- [Git Workflow](#git-workflow)
    - [Begin Workflow](#begin-workflow)
    - [Day to day Workflow](#day-to-day-workflow)
    - [Useful Git Commands](#useful-git-commands)
    - [Display git branch in bash prompt](#display-git-branch-in-bash-prompt)
- [Basic UNIX Commands](#basic-unix-commands)
- [Vim](#vim)
    - [Vim modes](#vim-modes)
    - [Basic Vim commands](#basic-vim-commands)
    - [Vim commands for movement](#vim-commands-for-movement)
    - [Vim commands for editing](#vim-commands-for-editing)
    - [Vim commands for searching text](#vim-commands-for-searching-text)
- [Setup(Conda)(OSX)](#setup(conda)(osx))
- [Setup(Conda)(Windows)](#setup(conda)(windows))

# Connecting to GitHub with SSH

## About SSH
With SSH keys, you can connect and communicate between client (local Git client) and remote server (GitHub). An SSH key is an alternative way to connect to GitHub without supplying your username and password at each visit.

SSH keys come in pairs, a public key that gets shared with services like GitHub, and a private key that is stored only on your computer. If they keys match, you're granted access.

## Checking for existing SSH keys
Before you generate an SSH key, you can check to see if you already have any SSH keys on your machine. You can check to see if any exist by moving into your `.ssh` directory and listing its contents:  
1. Open Terminal.
2. List the contents of your `.ssh` directory: 

        $ ls .ssh   
3. Check the directory listing to see if you already have a public SSH key. If you see `id_rsa.pub`, you already have a key pair and don't need to create one.

If your keys already exist, skip ahead to the **Add your public key to GitHub** section below.

## Generating a new SSH key
If you don't have an existing SSH key, you must generate a new SSH key:  
1. Paste the following command, substituting in your GitHub email: 

         $ ssh-keygen -t rsa -b 4096 -C "your_email@example.com"  

    This creates a new SSH key pair, using the provided email as a label.  

        > Generating public/private rsa key pair
2. When you're prompted to "Enter a file in which to save the key," press Enter. This accepts the default file location.  

        > Enter a file in which to save the key (/Users/you/.ssh/id_rsa): [Press Enter] 
3. At the prompt, omit or type an optional secure passphrase.  

        > Enter passphrase (empty for no passphrase): [Type a passphrase]  
        > Enter same passphrase again: [Type a passphrase again]
## Add your public key to GitHub
1. We now need to tell GitHub about your public key. Display the contents of your new public key with:  

        $ vi id_rsa.pub
2. Copy the contents of the output to your clipboard. Exit the Vim editor with the following command: `<Esc> :q! <Enter>`

    **Shortcut Tip #1:** You can quickly display the contents of your new public key with `cat`:

        $ cat ~/.ssh/id_rsa.pub  
    **Shortcut Tip #2:** You can quickly copy the contents with `pbcopy`:

        $ pbcopy < ~/.ssh/id_rsa.pub
3. Login to github.com and bring up your account **Settings**.
4. Select **SSH and GPG keys** from the side menu, then click **New SSH key**.
5. Title your key anything you'd like, and paste the contents of your keyboard into the **Key** text box. Finally, click **Add key** to save.

## Add your private key to the ssh-agent
`ssh-add` adds private key identities (from your `~/.ssh` directory) to the authentication agent (`ssh-agent`) so that the ssh-agent can take care of the authentication for you, and you don't have to type in passwords at the terminal.    
1. Add your SSH private key to the ssh-agent and store your passphrase in the keychain:

        $ ssh-add -K ~/.ssh/id_rsa
2. Verify that you have a private key generated and loaded into SSH:  

        $ ssh-add -l  
        # Lists fingerprints of all identities currently represented by agent

## Testing your SSH connectivity  
After you've set up your SSH key and added it to your GitHub account, you can test your connection:  
1. Paste the following command:

        $ ssh -vv git@github.com  
2. You may see a warning like this:

        > The authenticity of host 'github.com (IP ADDRESS)' can't be established.  
        > RSA key fingerprint is SHA256:nThbg6kXUpJWGl7E1IGOCspRomTxdCARLviKw6E5SY8.  
        > Are you sure you want to continue connecting (yes/no)?

    Verify that fingerprint of your private key matches the one listed in the warning message then type `yes`:

        > Hi {user_name}! You've successfully authenticated, but GitHub does not provide shell access.

# Git Workflow
GitHub is a user interface for a Git repository hosting service. Git is a distributed version control system accessible through a command line.

Git helps keep track of changes in code and allows for collaboration on projects of all scale.

## Begin Workflow
1. Access repository.
2. Click the green **Code** button.
3. Copy the repository address to clipboard.
4. Open Terminal.
5. Navigate to your home directory:

        $ cd ~
6. Create a workspace directory:

        $ mkdir workspace
7. Navigate to your workspace:

        $ cd workspace
8. Clone the repo to local machine:  

        $ git clone https://github.com/user_name/repo_name.git
    By cloning the repo, you're creating a local copy of it. A folder will appear in your workspace directory that is a copy of the cloned repo.

## Day to day Workflow
A git workflow process is seen by many as essential for any project. A common workflow looks like:  
- Check out new branch.
- Work on that branch, making several commits.
- Merge changes back into the master branch in a single, curated commit.  

1. Create a new working branch from `master` to work on:

        $ git checkout -b <branch>
2. Write code, commit regularly:

        # Add all files to the stage
        $ git add .
        # Commit files
        $ git commit -m "<message>"
        # Push local branch to remote
        $ git push -u origin <branch>
    Commit the staged snapshot regularly. Instead of launching a text editor, you can use `<message>` as a description of this commit. 
3. Depending on how long you've been working on your working branch and how large your team is, the local `master` branch of your project may be out of sync from the origin. Checkout and pull the latest version from `master`:

        # Move into local master branch
        $ git checkout master
        # Make sure local master is up-to-date
        $ git pull origin master
    This will fetch and merge any changes on the remote repo into the local `master` branch with all the changes.  
4. Checkout your working branch before merging `master`:  

        $ git checkout <branch>
        # Merge master INTO <branch>
        $ git merge master

## Useful Git Commands
### Git Basics
- `git clone <repo>` - Clone repo located at `<repo>` onto local machine. Original repo can be locatedon the local filesystem or on a remote machine via HTTP or SSH.
- `git config user.name <name>` - Define author name to be used for all commits in current repo. Devs commonly use `--global` flag to set config options for current user.
- `git config user.name <email>` - Define author email to be used for all commits in current repo. Devs commonly use `--global` flag to set config options for current user.
- `git add <directory>` - Stage all changes in `<directory>` for the next commit. Replace `<directory>` with a `<file>` to change a specific file.
- `git commit -m "<message>"` - Commit the staged snapshot, but instead of launching a text editor, use `<message>` as the commit message.
- `git status` - List which files are staged, unstaged, and untracked.
- `git log` - Display the entire commit history using the default format.
- `git diff` - Show unstaged changes between your index and working directory.

### Git Branches
- `git branch` - List all of the branches in your repo. Add a `<branch>` argument to create a new branch with the name `<branch>`.
- `git checkout -b <branch>` - Create and checkout new branch named `<branch>`. Drop the `-b` flag to checkout an existing branch.
- `git merge <branch>` - Merge `<branch>` into the current branch.

### Remote Repositories
- `git pull <remote>` - Fetch the specified remote's copy of current branch and immediately merge it into the local copy.
- `git push <remote> <branch>` - Push the branch to `<remote>`, along with necessary commits and objects. Creates named branch in the remote repo if it doesn't exist.

## Display git branch in bash prompt
The `.bashrc` is a file which is called by bash on each start of a new interactive shell. The file can be used to setup the environment, export variables, create aliases and functions and more:

1. In order to edit the file, type:

        $ vi ~/.bashrc
2. Add this to `~./bashrc` :

        parse_git_branch() {
             git branch 2> /dev/null | sed -e '/^[^*]/d' -e 's/* \
        (.*\)/(\1)/'
        }

        export PS1="\u@\h \[\e[32m\]\w \[\e[91m\]\$(parse_git_branch)\
        [\e[00m\]$ "
3. Once you managed to edit the file, start a new connection or simply type:

        $ source ~/.bashrc
    The setting adds the current git branch name in bash prompt with *highlighted color*. This helps developers avoid a lot of problems with working on wrong git branches.

# Basic UNIX Commands
- `mkdir [name]` -  Makes a new directory called *name*
- `mkdir -p [level1/level2/…]` - Allows you to create a series of nested directories
- `pwd` - Prints working directory
- `ls` - Lists contents of a directory
- `ls -l` - Lists contents of directory & provides add. info about file/dir
- `mv [src] [dest]` - Move a file/dir called *src* to a file/dir called *dest*
- `rm [file]` - Deletes/removes a file
- `rm -r [dir]` - Recursively deletes contents of a directory; must include **-r**
- `cd`- Used to change directory you are currently located in
- `~` - Refers to home dir
- `..` - Refers to dir above current one
- `cd ..` - Goes to dir above the current one
- `cd ~` - Goes to home directory
- `g++ -o [filename] [filename.cpp]` - Compiles source file
- `g++ [filename.cpp]` - Compiles program into a file called a.out
- `./[filename]` - Used to execute compiled program

# Vim
Vim is a highly configurable text editor built to make creating and changing any kind of text very efficient. It is included as `vi` with most UNIX systems and with Apple OS X. 

## Vim modes
Vim has two modes:
1. **Command Mode**: This is the default mode that you'll be in once you open Vim. If you're in a different mode and want to go back to command mode, just hit `<Esc>`. This mode allows you to use Vim commands and move through your document.

2. **Insert Mode**: This mode allows you to enter text into your document. You can enter insert mode by pressing the `i` key.

## Basic Vim commands
- `:w` - Saves the file you are working on
- `:w [filename]` - Allows you to save your file with the name you defined
- `:wq` - Save your file and close Vim
- `:q!` - Quit without saving the file
- `:e [file]` - Opens a file, where [file] is the name of the file you want to open

## Vim commands for movement
- `j` - Move the curson down one line
- `k` - Move the cursor up one line
- `l` - Move the cursor to the right
- `h` - Move the cursor to the left
- `w` - Puts the cursor at the start of the next word
- `b` - Puts the cursor at the start of the previous word
- `e` - Puts the cursor at the end of a word
- `0` - Places the cursor at the beginning of a line
- `$` - Places the cursor at the end of a line
- `(` - Takes your to the start of the previous sentence
- `)` - Takes you to the start of the next sentence

## Vim commands for editing
- `yy` - Copies a line
- `yw` - Copies a word
- `y$` - Copies from where your cursor is to the end of a line
- `v` - Highlights one character at a time using arrow buttons of the h, k, j, l buttons
- `V` - Highlights one line, and movement keys can allow you to highlight additional lines
- `p` - Paste whatever has been copied
- `d` - Deletes highlighted text
- `dd` - Deletes a line of text
- `dw` - Deletes a word
- `D` - Deletes everything from where your cursor is to the end of the line
- `d0` - Deletes everything from where your cursor is to the beginning of the file
- `dG` - Deletes everything from where your cursor is to the end of the file
- `x` - Deletes a single character
- `u` - Under the last operation
- `<Ctrl> + r` - Redo the last undo
- `.` - Repeats the last action

## Vim commands for searching text
- `/[keyword]` - Searches for keyword in the text
- `n` - Searches you text again in whatever direction your last search was
- `N` - Searches your text again in the opposite direction
- `:%s/[pattern]/[replacement]/g` - Replaces all occurences of [pattern] with [replacement] all at once
- `:%s/[pattern]/[replacement]/gc` - Replaces all occurences of [pattern] with [replacement] one at a time

# Setup(Conda)(OSX)

## Conda Environment Setup
Conda is a virtual environment used to isolate packages for dev/production
environments. 

### Install
[Installation Guide](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html)

### Conda Quick Guide
[Conda Cheatsheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)

### Environment Creation
`conda create --name ecommerce`

Environment creation from an existing requirement file
`conda create -n ecommerce --file requirements`

### Listing Environments
`conda info --envs`

### Activating an Environment
`conda activate <environment_name>`

### Deactivate an Environment
This will deactivate the environment for the currently active environment
`conda deactivate`

### Install a Package in Environment
`conda install <pkg_name>`

### List all Packages in Environment
`conda list`

### Check for Specific Package
`conda list -n <environment_name> <package_name>`

### Exporting an Environment
This exports all the packages installed in this environment
`conda list -e > requirements`

# Setup(Conda)(Windows)
### Install
[Installation Guide](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html)
[Download Website](https://www.anaconda.com/products/individual)
[Commands Cheat Sheet](https://docs.conda.io/projects/conda/en/4.6.0/_downloads/52a95608c49671267e40c689e0bc00ca/conda-cheatsheet.pdf)

### Installation Verification or Updating Conda
`conda info`
`conda update conda`

### Environment Creation
`conda create --name ecommerce`

### Listing Environments
`conda env list`

### Activating an Environment
`conda activate <environment_name>`

### Deactivating an Environment
`conda deactivate <environment_name>`

### Install a Package in Environment
`conda install <pkg_name>`

### Exporting an Environment
This exports all the packages installed in this environment
`conda list -e > requirements`
