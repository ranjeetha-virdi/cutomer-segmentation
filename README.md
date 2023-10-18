# Cutomer-Segmentation: Understanding your Customers

    
![Customer-Segmentation-Analysis-Mbaknol](https://github.com/ranjeetha-virdi/cutomer-segmentation/assets/81987445/df1b3112-d1d3-4d51-99f0-9151d0910ee3)




Customer segmentation is an effective tool for businesses to closely align their strategy and tactics with, and better target, their current and future customers. 
Every customer is different and every customer journey is different, so a single approach often isn’t going to work for all.

Customer segmentation is the process by which you divide your customers up based on common characteristics – such as demographics or behaviours, so your 
marketing team or sales team can reach out to those customers more effectively.

These customer segmentation groups can also be used to begin building a marketing persona or product user persona. This is because effective customer segmentation analysis 
is typically used to inform a brand’s messaging and positioning, helps organisations know what new products are services they might want to invest in, and uncovers ways to 
improve how the business sells. Because of this, marketing personas need to be closely aligned to those segments in order to be effective.

The “target persona” (or “marketing persona”) is, by definition, a personification of a specific customer segment so it’s not uncommon for businesses to create several personas 
to match the various customer segments they’ve created. But for that to happen, a business needs a robust set of customer segments to form a customer segmentation model. 

### Aim
#### Group over 200,000 Instacart users based on their historic purchasing patterns. 

#### Who is Instacart?
Instacart is the North American leader in online grocery delivery. Instacart shoppers offer same-day delivery and pickup services to bring fresh groceries and everyday essentials to busy people and families across the U.S. and Canada. Instacart’s delivery service is available to 85% of U.S. households and 70% of Canadian households.

## To achieve this, we will do the following:

   I. Design a Segmentation pipeline to carry out including Exploratory Data Analysis, Data Wrangling, Feature Engineering and Modeling.
   
   
   II. Reducing the features with the help of PCA.
   
   
   The basic requirements to meet this aim we need to do the following steps: 
      
      1.	Data Collection
      
      2.	Data Cleaning
      
      3.	Exploratory Data Analysis
     
      4.	Feature Preprocessing
      
      5.	Feature Engineering with PCA
     
      6.	Modeling, test the data using K-Means Algorithm
      
      7.	Hyperparameter tuning
      
      8.	Model Evaluation and find the best model 

### Data Collection

For customer segmentation of retail market, we use the dataset available at the dataset shared on Kaggle for Instacart Market Basket Analysis.
[This dataset was open-sourced by Instacart a few years ago.](https://www.kaggle.com/c/instacart-market-basket-analysis)


### Data Cleaning 

To get an overview of the dataset at hand, we have a helper function to summarize all these aspects of the data set like the unique categories,spread of numeric data to detect outliers, identify missing values etc.
In the Instacart dataset, only one metric (‘days since prior order’) had missing values and upon further investigation, these values were only missing from the first order of customers and hence, this metric was replaced with 0
The cleaning process include dropping columns like address, latitude and longitude. 

### Exploratory Data Analysis
Understanding orders were made by a single customer, number of products in a single order, how many days passed since last re-order?, which days have the most orders?: 

![orders1](https://github.com/ranjeetha-virdi/cutomer-segmentation/assets/81987445/798c231b-c717-4a78-9543-f9bb988164f7)



What is the average/median cart size? What is the trend for ordering on different days of the week? What are the most ordered/reordered products? Which aisle/department gets the most reorders?

![orders2](https://github.com/ranjeetha-virdi/cutomer-segmentation/assets/81987445/56445e43-d648-47d0-8653-06f8a943bd7a)

![items](https://github.com/ranjeetha-virdi/cutomer-segmentation/assets/81987445/01395756-ec01-4095-8177-f45b70c2a664)
### Feature Processing and Engineering
Segmentation is done on multiple datasets to ensure different behaviours, preferences and attitudes of customers are getting captured. To reduce the complexity of the later steps it is best to create a master dataset, merging all the relevant data and rolling it up to the customer level.

Along with merging datasets, Data Wrangling also includes converting all data into appropriate data types and standardising data to ensure consistency. Below is an illustration of how we can use simple pandas functions like concatenate and merge to create a master dataset for easy access for downstream uses.

#### Steps for feature Engineering:
    1. Numeric data needs to be binned for categorical models; categorical data needs to be one-hot encoded for numeric models.        Similarly, the other data types should be appropriately converted to suit the model. To ensure we are inputting good               distribution of data into the model, it is also necessary to transform data (log, polynomial, etc.) based on the need of the       hour.
    2. Compressing the dimensionality of features to reduce the number of features, which can be overwhelming and might lead to        overfitting of the model. A very good method to reduce dimensionality and retain max information of the features by using PCA.
###  Modeling, test the data using K-Means Algorithm:
Clustering aims to group data points together based on their similarities. k-means is one of the simplest clustering algorithms. It initializes k number of centroids and assigns each data point to a centroid based on the smallest distance to each. This makes k number of clusters of data points. Once the cluster is identified, the centroids are readjusted to be at the centre of the cluster and the data points are reallocated based on these new centroids. This process keeps repeating until the algorithm converges i.e. it the centroid stops changing upon iterations or when the maximum limit for iterations is reached.

Before we tune the model, let’s look at a simple k-means code below and understand the use of each hyperparameter.
````
kmeans_args = {
"init": "random",
"n_init": 10,
"max_iter": 300,
"random_state": 42,
}
kmeans = KMeans(n_clusters = 5, **kmeans_args)
kmeans.fit(X)
````
    
    
    
**init**: It is used to define the method of initialization of centroids. When random, it chooses random rows from data for initialization whereas k-means++ allows the algorithm to place initial centres smartly

**n_init**: Allows the algorithm to initialize clusters the defined number of times and choose the most converging value as the best fit

**max_iter**: It is the maximum number of iterations of the algorithm in a single run to converge, the default value is 300

**random_state**: It guarantees the reproducibility of the model results

**n_clusters**:It refers to the number of clusters we want from the model, the algorithm will initialize those many centroids. To decide the ideal number of clusters, it is best to do statistical analysis as well as talk to domain experts to understand how many clusters they expect based on their expertise.
#### Techniques to find the appropriate number of clusters:

**Elbow Method**: In this method, we plot the explained variation of the data across different number of clusters. As k increases, the squared distance between the centroid and data point decreases, and the trick is to pick n_clusters around the range where we start getting diminishing results on increasing k — this is called the Elbow of the curve.
````
cluster_range = range(2,16)
sse = []
for k in cluster_range:
 kmeans = KMeans(n_clusters=k, **kmeans_args)
 kmeans.fit(X)
 sse.append(kmeans.inertia_)
````
![elbow](https://github.com/ranjeetha-virdi/cutomer-segmentation/assets/81987445/763a87d3-351e-4294-871b-4ece3bc2df92)


**Silhouette Method**: It measures how much a data point is similar to its own cluster compared to another cluster and we can generate a plot summarizing how well each data point has been classified. 1 means clusters are clearly distinguished and 0 means they are not significantly different.

````
silhouette_coefficients = []
cluster_range = range(3,10)
for k in cluster_range:
 kmeans = KMeans(n_clusters=k, **kmeans_args)
 kmeans.fit(X)
 score = silhouette_score(X, kmeans.labels_)
 silhouette_coefficients.append(score)    
````



### Hyperparameter tuning
After tuning the hyperparameters and determining the value of ‘k’, it is recommended to run iterations with k, k+1, k-1 clusters to study the variation in the stories and usefulness of the output segments
### Final output: The clusters observed in the dataset.
