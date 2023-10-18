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
to match the various customer segments they’ve created.But for that to happen, a business needs a robust set of customer segments to form a customer segmentation model. 

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
      
      6.	Test Train Split
     
      7.	Modeling, test the data using K-Means Algorithm
      
      8.	Hyperparameter tuning
      
      9.	Model Evaluation and find the best model 

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
