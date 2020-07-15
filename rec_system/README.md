# Introduction

This directory contains EDA and models for e-commerce recommendations.

# Environment Setup

Environment creation from an existing requirement file
`conda create -n ecommerce --file requirements`

## Listing Environments
Ensure newly created `ecommerce` environment exists
`conda info --envs`

## Activating Environment
`conda activate ecommerce`

## Exporting Environment
This exports all the packages installed in this environment. Please update
requirements if you install new packages
`conda list -e > requirements`

# Data Acquisition
These instructions are to obtain the dataset that is explored further in the Jupyter notebook files.
- Create a new folder called `Data` and navigate into it
- Download the data from [data source](https://www.kaggle.com/mkechinov/ecommerce-events-history-in-cosmetics-shop?select=2019-Nov.csv) into the Data folder
	* You should download all the datafiles at that location (including `2019-Oct, 2019-Nov, 2019-Dec, 2020-Jan, and 2020-Feb`)
	* Alternatively, you may download only `2019-Nov` since that is what is analyzed in the Jupyter notebooks.
- The `Data` folder is part of the .gitignore hence it is not included in any commits made. This is done to make our commits lightweight.
