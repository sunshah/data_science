# Introduction

This directory contains NLP methods and techniques to model similarity between descriptions of e-commerce product listing.

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
- Create a new folder called `data` and navigate into it
- We'll be using a text similarity dataset from [Kaggle](https://www.kaggle.com/rishisankineni/text-similarity?select=train.csv). Download the dataset (`train.csv` and `test.csv`) to a directory named `data`. 
- Once you have a satisfactory model, test your model on an e-commerce [Kaggle](https://www.kaggle.com/cclark/product-item-data) dataset. Download the data to the `data` directory and rename file to `ecommerce_product_listing.csv`. You may need to update your methodology for the new dataset.
- The `data` folder is part of the .gitignore hence it is not included in any commits made. This is done to make our commits lightweight.
