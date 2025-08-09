# Model Card: Instacart Customer Segmentation using K-Means

This model identifies clusters of Instacart customers based on their historical shopping data and behaviours, with the goal of revealing meaningful customer segments.

## Model Description

**Input:**

- The model takes as input customer-level features derived from transaction history. These include:
  1. Total orders per customer
  2. Average basket size (total products/total orders)
  3. Re-order probability 
  4. Departments from which customers order the most (categorical, so will be one-hot encoded)
  5. Average days between orders
  6. Number of unique products per customer

All numeric features are scaled using **StandardScaler** before training.

**Output:**

- The model outputs a **cluster label** (e.g., 0, 1, 2, 3) for each user.
- Each label corresponds to a distinct customer segment inferred from shopping patterns.

**Model Architecture:**

- Unsupervised clustering model using **K-Means** algorithm from Scikit-learn.
- Key settings:
  - `n_clusters = 15` (determined using Elbow Method)
  - `init = 'k-means++'`
  - `n_init = 20`
  - `max_iter = 300`
  - `random_state = 42`


## Performance

As an **unsupervised model**, performance is evaluated using **Davies-Bouldin Index**.
References: 
- https://www.geeksforgeeks.org/machine-learning/davies-bouldin-index/
- https://codesignal.com/learn/courses/cluster-performance-unveiled/lessons/mastering-the-davies-bouldin-index-for-clustering-model-validation
This is a measure of how distinct the clusters are from each other and lower index value indicates better clustering performance. 


## Limitations

- **No ground truth**: Since this is unsupervised, we don’t have labels to verify cluster "correctness".
- **Feature selection dependent**: Clusters may change significantly if different features are chosen.
- **Static snapshot**: The model is based on historical data and does not account for future behavior shifts.
- **No demographic info**: Without age, location, or income, it’s harder to align segments with business goals. The upside is that we're less worried about biases and other ethical concerns with this exercise.
- **Temporal simplification**: Time-based variables are relative, not timestamped — this limits seasonal or trend analysis.


## Trade-offs

- **Interpretability vs Complexity**: K-Means is simple and easy to explain, but may miss complex non-linear structures in the data.
- **Fixed cluster count**: Requires the number of clusters (`k`) to be predefined. Choosing the wrong value may group users inappropriately.
- **Sensitive to scale and outliers**: Proper feature normalization is critical. Outliers can skew centroids.
- **Assumes spherical clusters**: K-Means assumes equally sized, spherical clusters, which may not reflect real-world customer behaviors.

In future work, we could explore other methods to determine the optimum k value to use in K-means (i.e. not just the Elbow Method). We could explore other methods like the Silhouette Method.
Alternatively, clustering methods like **DBSCAN** or **Gaussian Mixture Models (GMM)** could be explored to address these limitations. 



