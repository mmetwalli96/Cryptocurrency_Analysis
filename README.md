# Cryptocurrency Analysis

Use unsupervised learning to group cryptocurrencies. The following steps were followed, preprocessed the data for PCA, reduced the data dimensions using PCA, clustered the cryptocurrencies using K-Means, and visualised the results. 

## Data Preprocessing for Principal Component Analysis

The first step to begin this analysis is the data preparation. Here the column <b><i>IsTrading</i></b> was removed, the coin names were dropped, the rows containing NaN values were excluded, the data was standardized, and finally the categorical data were transformed to numerical ones by <b><i>get_dummies</i></b> function. 

## Reduction of Data Dimensionality 

Principal Component Analysis (PCA) was used to reduce the dimension of the data to three main components to simplify the training of the model and ease the visualisation of the clustered data. 


The number of components was chosen to be three for two reasons, the first reason is the possibility to visualize the clustered data in three-dimensional space. As for the second and last one, preserving the information that is in the data. Going higher or lower than three will violate one of the two reasons. 

Here is a snippet of the data after performing PCA:  

<img width="273" alt="Screen Shot 2022-02-10 at 1 14 45 PM" src="https://user-images.githubusercontent.com/59425631/153471393-407ca977-67fd-4e7d-8645-974a13e1c0a2.png">











