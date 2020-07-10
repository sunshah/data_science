# Introduction

This repository contains EDA and models for BoffinAI.


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
`conda env export > <environment_name>.yml`
