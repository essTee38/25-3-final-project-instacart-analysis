# Datasheet Template

## Motivation

The dataset was created by Instacart for a Kaggle competition whose objective is to predict what previously purchased item a user will add in their next order. The link to the competition has not been working recently, however, the link to the data remains intact. 
https://www.kaggle.com/datasets/psparks/instacart-market-basket-analysis/data 
 
## Composition

- The dataset contains historical **grocery shopping transactions** made by real Instacart customers. Each instance represents either an individual **order**, a **product purchased within an order**, or **metadata** about a product (e.g., product name, department).
  
- Key components include:
  - **3,421,083 prior orders**
  - **206,209 unique users**
  - **49,688 unique products**
  - **134 aisles** and **21 departments**
  
- The dataset includes five main CSV files:
  - `orders.csv` – information about customer orders (e.g., order number, time of day, days since prior order)
  - `order_products__prior.csv` – items purchased in each prior order
  - `products.csv`, `aisles.csv`, and `departments.csv` – product-level metadata

- There is minimal missing data. For instance, the `days_since_prior_order` field contains null values for a user’s first order (which is expected and not considered missing in context).

- No personally identifiable information (PII) is included. The dataset has been fully anonymised — users are represented only by numeric IDs, and there are no names, addresses, emails, or payment information. There is no content from communications or other sensitive records.

## Collection process

The data contain Instacart's historical purchases data from real customers.

- The data is a sample of customer activity from Instacart in 2017. The exact sampling strategy is not documented, but it includes only users with at least four orders to ensure meaningful user history.

- The data appears to span multiple weeks or months. Instead of dates, it uses relative timing (e.g., days since prior order), and the order number per user.

- The dataset was originally released as part of a Kaggle competition in 2017, designed to challenge participants to predict products in a user’s next order.


## Preprocessing/cleaning/labelling

- **Preprocessing by Instacart**:
  - User and product IDs have been anonymised.
  - All temporal information is represented relatively (e.g., `order_hour_of_day`, `days_since_prior_order`) instead of absolute timestamps.

- **In this project**:
  - We performed preprocessing steps to aggregate user behavior across prior orders.
  - These include:
    - Calculating per-user averages (e.g., reorder rate, basket size)
    - Identifying most common departments per user
    - One-hot encoding categorical fields (e.g., top department)
    - Normalizing numeric features for clustering

- The original raw data was preserved, and all derived features were created programmatically in the analysis pipeline. No permanent deletion or modification of source data occurred.



## Uses

- Other potential uses of this dataset include:
  - Building recommendation systems
  - Performing market basket analysis (e.g., association rule mining)
  - Analysing customer retention and reorder behavior
  - Studying seasonal or temporal purchase patterns

- **Potential impacts and considerations**:
  - The dataset reflects only users who placed 4 or more orders, which may introduce selection bias toward more engaged or loyal customers.
  - All users are anonymous; demographic or location data is not available, which limits fairness or bias audits across age, gender, region, etc.
  - The dataset is historical and U.S.-based (Instacart’s market), so generalizing results to other countries or current behavior may be inaccurate.
  - Over-reliance on behavioral clustering without understanding real-world motivations may lead to misclassification or oversimplification of customers.

- **Suggested mitigations**:
  - Avoid interpreting clusters as rigid or deterministic — they are behavioral groupings, not hard categories.
  - Supplement this dataset with qualitative research or customer feedback before taking marketing actions based on clustering.

- **Tasks this dataset is not suitable for**:
  - Predicting individual identities, behaviors, or sensitive characteristics (e.g., income, demographics)
  - Fairness analysis across protected groups (since such features are absent)
  - Real-time transaction processing or up-to-date trend prediction (as the data is static and dated)


## Distribution

The dataset can be obtained from the link https://www.kaggle.com/datasets/psparks/instacart-market-basket-analysis/data
It is available publically (licence: CC0: Public Domain)

## Maintenance

The dataset does not seem to have been maintained for a period of time. The last update was made in 2018. 

