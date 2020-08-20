# Predicting Stock Price

## Introduction
We will use the historical stock price of the New Germany Fund (GF) to try to predict the closing price in the next five trading days.

From this project, we will learn the entire procedure of making a time series stationary before using SARIMA to model. It is a long and tedious process, with a lot of manual tweaking.

## Data Acquisition
These instructions are to obtain the dataset that is explored further in the Jupyter notebook files.

1. Create a new folder called `data` and navigate into it.
2. Download the dataset from [here](https://github.com/sunshah/data_science/tree/master/time_series) and copy it into the `data` folder:

        $ cp ~/Downloads/stock_prices_sample.csv ./data

**Note**: The `data` folder is part of the .gitignore hence it is not included in any commits made. This is done to make our commits lightweight.

You can obtain the notebook in addition to the dataset [here](https://github.com/sunshah/data_science/tree/master/time_series).