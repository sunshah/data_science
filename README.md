# data_science
Data science repository

# Introduction

This repository contains EDA and models for BoffinAI.

# Connecting to GitHub with SSH

## About SSH
With SSH keys, you can connect and communicate between client (local Git client) and remote server (GitHub). An SSH key is an alternative way to connect to GitHub without supplying your username and password at each visit.

SSH keys come in pairs, a public key that gets shared with services like GitHub, and a private key that is stored only on your computer. If they keys match, you're granted access.

## Checking for existing SSH keys
Before you generate an SSH key, you can check to see if you already have any SSH keys on your machine. You can check to see if any exist by moving into your `.ssh` directory and listing its contents:  
1. Open Terminal.
2. List the contents of your `.ssh` directory: 

        $ cd ~/.ssh   
        $ ls
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
    By cloning the repo, you're creating a local copy of it. A folder will appear in your workspace directory that is a copy of the cloned rep.

## Day-to-day Workflow
A git workflow process is seen by many as essential for any project. A common workflow looks like:  
- Check out new branch.
- Work on that branch, making several commits.
- Merge changes back into the master branch in a single, curated commit.  

The idea is that a single large commit keeps the master branch neater than lots of small commits. Let's go through each step in more detail.  

1. Create a new branch to work on:

        $ git checkout -b <branch>
2. Write code, commit regularly:

        # Add all files to the stage
        $ git add .
        # Commit files
        $ git commit -m "<message>"
    Commit the staged snapshot regularly. Instead of launching a text editor, use `<message>` as a description of this commit. 
3. 

## Editing your .bashrc
The `.bashrc` is a file which is called by bash on each start of a new interactive shell. The file can be used to setup the environment, export variables, create aliases and functions and more:

1. In order to edit the file, type:

        $ vi ~/.bashrc
2. Once you managed to edit the file, start a new connection or simply type:

        $ source ~/.bashrc
    The setting you added should now be a part of your bash shell environment.

# VIM
What is VIM?
## Basic VIM Commands
- `j/k` - move up/down

# Setup(OSX)

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
