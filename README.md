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

# Aim

## To achieve this, we will do the following:

   I. Design a Segmentation pipeline to carry out including Exploratory Data Analysis, Data Wrangling, Feature Engineering and Modeling.
   
   
   II. Reducing the features with the help of PCA for customer segmentation.
   
   
   The basic requirements to meet this aim we need to do the following steps: 
      
      1.	Data Collection
      
      2.	Data Cleaning
      
      3.	Exploratory Data Analysis
     
      4.	Feature Preprocessing
      
      5.	Feature Engineering to create new features like affordability and Economic Regions of US
      
      6.	Test Train Split
     
      7.	Modeling, test the data on different machine learning models 
      
      8.	Hyperparameter tuning
      
      9.	Model Evaluation and find the best model 

### Data Collection

For customer segmentation of retail market, we use the dataset available at the dataset shared on Kaggle for Instacart Market Basket Analysis.
This dataset was open-sourced by Instacart a few years ago.




The dataset has data points for apartment, homes and retail properties available for rent across all the states in US. The dataset 
has 1,00,000 rows and 22 columns with each row representing each property available for rent with numerical features like bedrooms, 
bathrooms, square feet and rent and categorical features like category of the property whether home or apartment, amenities, pets 
allowed or not and has a fee or not.

### Data Cleaning 

To get an overview of the dataset at hand, like examining the spread of the numerical data like price, square feet, bedrooms and bathrooms
and examine the presence of null values, I have a helper function to summarize all these aspects of the data set we can easily have a 
summarized overview of the distribution of our data set. Also we can see that there are many columns like amenities, pets allowed and 
address with missing values. 
The cleaning process include dropping columns like address, latitude and longitude. 
Convert the price feature for some properties were specified in terms of weekly basis to monthly basis. Formatting amenities columns to properly 
encode ordinal values based on their importance. Example if an apartment is with acess to golf club and swimming pool then it will be evaluated to
have a higher rent as compared to an apartment only with a refrigerator and ac. Bring columns like category which specifies the type of property ie 
an apartment or a home is available at rent. Then create seperate dataframes for each state with maximum data points in our case it was Texas, California, 
Varginia, North Carolina, Colorado, Florida, Massachusetts and Maryland.

### Exploratory Data Analysis

To understand the distribution of the properties at various levels starting at Economic Region Level. The US is divided into eight economic regions by 
The Bureau of Economic Analysis for comparison of economic data and they are as below.

