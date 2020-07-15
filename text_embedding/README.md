# Introduction

This directory contains EDA and models for e-commerce recommendations.

# Environment Setup

Environment creation from an existing requirement file
`conda create -n nlp --file requirements`

## Listing Environments
Ensure newly created `nlp` environment exists
`conda info --envs`

## Activating Environment
`conda activate nlp`

## Exporting Environment
This exports all the packages installed in this environment. Please update
requirements if you install new packages
`conda list -e > requirements`

# Data Acquisition
These instructions are to obtain the dataset that is explored further in the Jupyter notebook files.
- Create a new folder called `data` and navigate into it
- Download the data from [data source](https://www.kaggle.com/cclark/product-item-data/download) into the data folder
- Rename the csv file to `ecommerce_product_listing.csv`
- The `data` folder is part of the .gitignore hence it is not included in any commits made. This is done to make our commits lightweight.
