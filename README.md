# Cryptocurrency Analysis

Use unsupervised learning to group cryptocurrencies. The following steps were followed, preprocessed the data for PCA, reduced the data dimensions using PCA, clustered the cryptocurrencies using K-Means, and visualised the results. 

## Data Preprocessing for Principal Component Analysis

The first step to begin this analysis is the data preparation. Here the column <b><i>IsTrading</i></b> was removed, the coin names were dropped, the raws containing NaN values were excluded, and finally the categorical data were transformed to numerical ones by <b><i>get_dummies</i></b> function. 

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
