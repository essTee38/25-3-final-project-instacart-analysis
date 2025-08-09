# Customer Segmentation Based on Instacart Dataset


## Brief Description
This project uses Instacart Market Basket dataset and aims to segment customers based on their historical purchases and shopping behaviour using Unsupervised Machine Learning, specifically using K-means. By analysing how often customers shopped, what they bought, and how and what they re-ordered, we aim to identify distinct groups of customers.

### Possible Further Exploration
While the scope of this project stops once customers segments are identified, these segments can then be linked to groups of products in hopes of creating a product recommendation system for customers. Ultimately, a great product recommendations could drive customer retention, or perhaps even attract new customers due to positive feedback from existing customers and hence drive revenue growth for the grocers.

## DATA
The data used in this project can be downloaded from:
https://www.kaggle.com/datasets/psparks/instacart-market-basket-analysis
Refer also to the modelcard.md and data_sheet.md within this project.

## MODEL 
- Model Type: Unsupervised Clustering  
- Algorithm: K-Means Clustering  
- Framework: Scikit-learn (Python)  
- Features: User-level shopping behavior including total orders per customer, reorder rates, average basket size, top departments (that products bought belong to), order frequency.

## HYPERPARAMETER OPTIMSATION
The following hyperparameters were explored and tuned to improve clustering performance:

- Number of clusters (`n_clusters`): Tried values from 2 to 40 using the Elbow Method. Final model used 15 clusters, even though Elbow Method graph indicates k=27 as optimum (as this number will results in overfitting/clusters that aren't meaningful).
- Initialisation (`init`): Used `k-means++` for smarter centroid seeding.
- Number of initialisations (`n_init`): Increased from default 10 to 20 to ensure better convergence.
- Max iterations (`max_iter`): Used default of 300.
- Random seed (`random_state`): Set to 42 for reproducibility.

**Feature Engineering Notes**:
- User-level features were scaled using `StandardScaler` before clustering.
- Used one-hot encoding for the categorical feature: top department.

## RESULTS
The k=15 chosen resulted in non-optimum clustering. From the qualitative assessment on the resulting clusters against the median features for each cluster, some clusters are very similar to others. This observation is further supported by the Davies-Bouldin Index value which is ~1.5, indicating that the clusters are not that distinct from each other. 
Since we chose the value of k=15 from the Elbow Method, we must first assess other methods to determine or predict the optimum number of clusters to segment into, ideally even trying a range of k values. 

As a follow up from this project, and before using the segmentation results for anything else e.g. a product recommendation system, we must first ensure that the segmentation yields a reasonable result. To achieve that, we could firstly evaluate other methods for obtaining optimum k value e.g. Silhouette Score for K-means.
In addition, we should also explore other clustering methods such as DBSCAN and Gaussian Mixture Models - and compare the results with that of the enhanced K-means. 

## RUNNING THE NOTEBOOKS
The notebook can be run locally once the csv files has been downloaded and placed under ./data folder. 
Data can be downloaded from: https://www.kaggle.com/datasets/psparks/instacart-market-basket-analysis

The notebook uses 5 csv files:
1. orders.csv
2. order_products__prior.csv
3. products.csv
4. aisles.csv
5. departments.csv
6. 
