# CryptoClustering Project

This project aims to analyze cryptocurrency market data by performing clustering analysis using K-means and Principal Component Analysis (PCA). The goal is to identify patterns in cryptocurrency price changes over different time periods, optimize cluster groupings using PCA, and visualize the clustering results.

## Table of Contents

- [Overview](#overview)
- [Technologies Used](#technologies-used)
- [Data Preparation](#data-preparation)
- [Cluster Analysis](#cluster-analysis)
- [Principal Component Analysis](#principal-component-analysis)
- [Visualization](#visualization)
- [Results](#results)
- [Questions and Insights](#questions-and-insights)
- [Requirements](#requirements)
- [How to Run](#how-to-run)

## Overview

This project uses cryptocurrency market data from the `crypto_market_data.csv` file to perform the following tasks:

1. **Data Preparation**: Normalize the data using StandardScaler from scikit-learn.
2. **Clustering Analysis**: Use K-means clustering to identify distinct cryptocurrency groups based on price changes over various time periods.
3. **Optimization with PCA**: Reduce the dimensionality of the dataset using Principal Component Analysis (PCA) to optimize the clustering process.
4. **Visualization**: Visualize the clustering results using scatter plots and compare the effects of clustering with original vs. PCA-reduced data.

## Technologies Used

- Python
- Pandas
- Scikit-learn
- hvPlot
- Jupyter Notebook

## Data Preparation

### Data Loading

The data is loaded from a CSV file called `crypto_market_data.csv` into a pandas DataFrame. This dataset contains the market data of various cryptocurrencies, including their price changes over different time periods.

### Data Normalization

The data is normalized using the `StandardScaler()` from scikit-learn to ensure that all features (such as `price_change_percentage_24h`, `price_change_percentage_7d`, etc.) are on the same scale. This is crucial for K-means clustering to work effectively.

## Cluster Analysis

### Finding the Best k-value

To determine the optimal number of clusters for K-means, the Elbow Method was used. This involves calculating the inertia for different values of `k` (from 1 to 11) and plotting the inertia values to visually identify the "elbow", which represents the optimal number of clusters.

### K-means Clustering

Once the best value for `k` is determined, K-means clustering is performed to group the cryptocurrencies into clusters. The clusters are predicted and added as a new column in the DataFrame.

### Scatter Plot

A scatter plot is generated using `hvPlot` to visualize the clusters, with `price_change_percentage_24h` on the x-axis and `price_change_percentage_7d` on the y-axis. The plot is colored by cluster labels, and each point is labeled with the cryptocurrency's name in the hover effect.

## Principal Component Analysis

### Reducing Dimensionality

Principal Component Analysis (PCA) is used to reduce the features of the dataset to three principal components. This step helps to visualize the data in fewer dimensions and optimize the clustering process by removing redundant features.

### Explained Variance

The explained variance is calculated to understand how much of the original data's information is captured by each principal component. In this case, the three principal components together explain 89.4% of the variance in the data.

### PCA-based Clustering

After performing PCA, K-means clustering is applied again to the PCA-reduced data, and the optimal `k` value is reassessed using the Elbow Method. The clustering results are visualized with a scatter plot of the first two principal components (`PC1` and `PC2`).

## Visualization

### Elbow Curve Comparison

Two elbow curves are plotted: one using the original scaled data and another using the PCA-transformed data. This helps compare how the dimensionality reduction process impacts the clustering.

### Cluster Comparison

Scatter plots are also compared side-by-side to visualize the clusters formed by the original scaled data and the PCA-reduced data. This comparison shows how using fewer features (via PCA) leads to tighter and more distinct clusters.

## Results

- **Best k-value**: Both the original scaled data and the PCA-reduced data indicate that the optimal value for `k` is 4.
- **Impact of PCA**: Reducing the number of features via PCA results in tighter, more distinct clusters, as dimensionality reduction eliminates noise and redundancy in the data.

## Questions and Insights

- **What is the best value for k?**
  - The best value for `k` is 4 for both the original scaled data and the PCA-reduced data.
- **What is the total explained variance of the three principal components?**
  - The three principal components explain a total of **89.4%** of the variance.
- **What is the impact of using fewer features to cluster the data?**
  - Using PCA for dimensionality reduction results in more distinct and well-defined clusters, as it helps to focus on the most important features, removing noise and correlations between features.

## Requirements

To run the project locally, you will need:

- Python 3.x
- The following Python libraries:
  - pandas
  - scikit-learn
  - hvplot
  - matplotlib
  - jupyter

You can install the required libraries using `pip`(pip install pandas scikit-learn hvplot matplotlib jupyter).

## How to Run

### Clone this repository:

https://github.com/msmith150/CryptoClustering.git

### Navigate to the project directory:

cd CryptoClustering

### Navigate to the project directory:

jupyter notebook

### Open the Crypto_Clustering.ipynb file in Jupyter and run the cells to see the analysis.

## Conclusion

This project demonstrates how K-means clustering, combined with PCA, can be used to analyze and optimize cryptocurrency market data. By reducing the dimensionality of the data, we can achieve more meaningful and distinct clusters that help in understanding the trends and movements in cryptocurrency markets.
