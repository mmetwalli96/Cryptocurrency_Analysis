# Cryptocurrency Analysis

Use unsupervised learning to group cryptocurrencies. The following steps were followed, preprocessed the data for PCA, reduced the data dimensions using PCA, clustered the cryptocurrencies using K-Means, and visualised the results. 

## Data Preprocessing for Principal Component Analysis

The first step to begin this analysis is the data preparation. Here are the processes which were followed in the analysis: 

- The column <b><i>IsTrading</i></b> was removed.
- The column holding coin names was dropped. 
- The rows containing NaN values were excluded.
- The data was standardized.
- The categorical data were transformed to numerical ones by <b><i>get_dummies</i></b> function. 

## Reduction of Data Dimensionality 

Principal Component Analysis (PCA) was used to reduce the dimension of the data to three main components to simplify the training of the model and ease the visualisation of the clustered data. 


The number of components was chosen to be three for two reasons, the first reason is the possibility to visualize the clustered data in three-dimensional space. As for the second and last one, preserving the information that is in the data. Going higher or lower than three will violate one of the two reasons. 

Here is a snippet of the data after performing PCA:  

<img width="273" alt="Screen Shot 2022-02-10 at 1 14 45 PM" src="https://user-images.githubusercontent.com/59425631/153471393-407ca977-67fd-4e7d-8645-974a13e1c0a2.png">


## Deciding the Number of Centroids in K-Means Algorithm

To choose the number of expected clusters, the Elbow curve was plotted and the number is picked where the elbow shape is located on the graph as show in the below figure. Following the previously mentioned process, the number was chosen to be four.  


![elbow_curve](https://user-images.githubusercontent.com/59425631/153475187-9f66fdf8-94d8-4655-a7f7-1b3330aeeead.png)

## Model Evaluation and Results Discussion 

<img width="979" alt="Screen Shot 2022-02-10 at 2 00 40 PM" src="https://user-images.githubusercontent.com/59425631/153478102-23bb4b24-e30a-4df0-a942-550d33dbe248.png">

After training the model, it was able to separate the data nicely into four classes as shown in the above figure. Upon further inspection of the clustered data, it is possible to say that the algorithm significantly favoured the grouping based on the column name <b><i>ProofType</i></b>. The snippet of the data results below can confirm this deduction.  

<img width="720" alt="Screen Shot 2022-02-10 at 2 01 30 PM" src="https://user-images.githubusercontent.com/59425631/153478200-fda26031-ba62-4a90-95ce-4948f015277b.png">

