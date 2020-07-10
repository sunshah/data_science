# Introduction

This repository contains EDA and models for BoffinAI.


# Setup(OSX)

## Conda Environment Setup
Conda is a virtual environment used to isolate packages for dev/production
environments. 

### Install
[Installation Guide](https://docs.conda.io/projects/conda/en/latest/user-guide/install/index.html)

### Environment Creation
`conda create --name ecommerce`

Environment creation from an existing requirement file
`conda create -n ecommerce --file requirements`

### Listing Environments
`conda info --envs`

### Activating an Environment
`conda activate <environment_name>`

### Install a Package in Environment
`conda install <pkg_name>`

### Exporting an Environment
This exports all the packages installed in this environment
`conda list -e > requirements`
