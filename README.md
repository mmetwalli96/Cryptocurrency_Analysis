# Cryptocurrency Analysis

Use unsupervised learning to group cryptocurrencies. The following steps were followed, preprocessed the data for PCA, reduced the data dimensions using PCA, clustered the cryptocurrencies using K-Means, and visualised the results. 

## Data Preprocessing for Principal Component Analysis

The first step to begin this analysis is the data preparation. Here the column <b><i>IsTrading</i></b> was removed, the coin names were dropped, the rows containing NaN values were excluded, he data was standardized, and finally the categorical data were transformed to numerical ones by <b><i>get_dummies</i></b> function. 

Here is the piece of code used to perform data preparation:

```
# Remove the "IsTrading" column.
crypto_df = crypto_df[['CoinName', 'Algorithm', 'ProofType', 'TotalCoinsMined', 'TotalCoinSupply']]

# Remove rows that have at least 1 null value.
crypto_df = crypto_df.dropna()

# Keep the rows where coins are mined.
crypto_df = crypto_df[crypto_df['TotalCoinsMined'] > 0]

# Create a new DataFrame that holds only the cryptocurrencies names.
crypto_names_df = crypto_df['CoinName']

# Drop the 'CoinName' column since it's not going to be used on the clustering algorithm.
crypto_df = crypto_df[['Algorithm', 'ProofType', 'TotalCoinsMined', 'TotalCoinSupply']]

# Use get_dummies() to create variables for text features.
crypto_df = pd.concat((crypto_df['TotalCoinSupply'].astype(float), crypto_df['TotalCoinsMined'], crypto_df['Algorithm'], crypto_df['ProofType']), axis = 1)
x = crypto_df
x = pd.get_dummies(x)

# Standardize the data with StandardScaler().
data_scaler = StandardScaler()
x = data_scaler.fit_transform(x)

```
## Reduction of Data Dimensionality 

Principal Component Analysis (PCA) was used to reduce the dimension of the data to three main components to simplify the training of the model and ease the visualisation of the clustered data. 


The number of components was chosen to be three for two reasons, the first reason is the possibility to visualize the clustered data in three-dimensional space. As for the second and last one, preserving the information that is in the data. Going higher or lower than three will violate one of the two reasons. 

Here is a snippet of the data after performing PCA:  

<img width="273" alt="Screen Shot 2022-02-10 at 1 14 45 PM" src="https://user-images.githubusercontent.com/59425631/153471393-407ca977-67fd-4e7d-8645-974a13e1c0a2.png">











