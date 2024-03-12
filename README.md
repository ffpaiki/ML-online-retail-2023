# Machine Learning in Online Retail

In the business world, increasing revenue is achieved through various means. This can be done through marketing strategies, establishing a digital presence, or implementing appropriate business intelligence. As the growth of transactional data in the marketplace, Market Basket Analysis (MBA) enables data scientists to apply statistical and mathematical techniques to gain revenue. Basically, the concept of MBA works to generate patterns from the ransactional data, which will provide insights for increasing profits. Not only that, but this research also can be used as system recommendations for a customer in their shopping way. This project, we attempt to implement the MBA concept using a dataset obtained from UCI Machine Learning.

## The Processes

1. Data Extraction
2. Data Cleaning & Transformation
3. Exploratory Data Analysis
4. K-Means Clustering
5. Principal Component Analysis
6. Linear Regression
7. Logistic Regression

### Data Extraction

The data set contains all the transaction information for a UK-based non-store online retail occurring between 01/12/2010 and 09/12/2011 for 406,829 customers in 38 countries. The data is available at https://archive.ics.uci.edu/dataset/352/online+retail. As an initial introduction of the dataset, the data consists of 3 numerical features (Quantity, UnitPrice, and InvoiceDate) and 5 categorical features (InvoiceNo, StockCode, Description, CustomerID, and Country). InvoiceNo represents the invoice number assigned to each transaction (this code starts with ‘c’) it indicates cancelation, StockCode represents the product code, Description represents the product name, and UnitPrice represents the product price (in sterling).

### Data Cleaning & Transformation

The purpose of this is to remove unnecessary data, such as data with null values or data that doesn't conform to certaion format/requirement. During the data transformation, I also generate several data and split data into parts, which could be use later in categorize the information from the data. Data pre-processing is an essential step in the data analysis pipeline. It entails cleaning and transforming raw data into a format suitable for analysis.

This is an example of the data we possess; the total amount of data we have before the preprocessing step is approximately 550 thousand records, encompassing various features, as can be seen here. As you can see here, this dataset has more than 3500 types of items and more than 4000 customers. The data pre-processing, we perform includes removing canceled invoices, eliminating rows lacking CustomerID or item names, and standardizing the time format appropriately. In the end, the number of data rows after this pre-processing step is approximately 390 thousand.

### Exploratory Data Analysis (EDA)

In this phase, I'm trying to understand any kinds of information that can be generated from this data, such that has meaningful impact for the business. Since this is a transaction record of a business, the most important part in a business is sales, it's about how much profit can be generated and how can we use this information to increase sales in the future. Therefore, I use this to get as much information as possible regarding the sales information, such as countries that has more sales, time of day that has more sales, type of customer to target, which product that has the greater sales at a certain time, etc.

Due to the uneven distribution of the country data, which includes around 39 cities, we attempted to group them based on areas. Eventually, we discovered that more than 90% of our customers are in the UK, with the remainder distributed across Europe and several other regions. From this simple descriptive statistic, businesses can infer that they could enhance their marketing efforts in the UK. This is also one of the benefits of implementing Exploratory Data Analysis (EDA) before data processing. We examined the monthly total sales from our retail data. The sales display fluctuations throughout the year. In the first three months, the sales were relatively low, hovering around 600k. And in the fourth month, there was a slight increase in sales, reaching just above 600k. But, in the fifth and sixth months, the sales dip back down to 500k. Then, from the seventh month until the last month of the year, the sales slightly increase until reaching about 1 million at the of the year. Moreover, the average sales for the year were about 700k, and this figure was achieved starting from the middle of August until December.

### K-Means Clustering

In this part, we offer a clustering using K-means model. It is an unsupervised learning algorithm that aims to partition a dataset into K clusters. However, before proceeding, we need to implement elbow method to determine the optimal number of clusters. The basic idea of this method is to run K-means algorithms for a range value of K, in here we run it 12 times. 

From this line graph, we can see that the higher the number of clusters, the lower inertia is. Inertia itself is the sum of squared distances between data points and their assigned clusters centroid. So, based on the line graph, we can see the “elbow”, where it points to a suitable cluster, which is between 6 or 7. 

As we attempt to find the number of suitable clusters among customers based on purchase frequency and total spending, we run the K-means method and identify 7 clusters over more than 4300 customers. The visualization of the results is presented above. It’s important to note that during the execution of the K-means algorithm, we standardize the data point to prevent model bias. 

To represent the result of customer clustering using K-means, we utilize a scatter plot. In here, the x red dot displays a centroid for each cluster. Notably, when observing the two data points positioned above the plot, our intuition suggests that these points may be outliers. We make this assessment based on our gut feeling, as these points lack sufficient data support for their assigned cluster. 

### Logistic Regression

By using logistic regression, our goal is to identify relationships between cancellation items and the quantity or time of purchase. Logistic regression attempts to predict binary outcomes [0,1], where in this case, it predicts whether an item is canceled or not. We use library ‘ScikitLearn’ package in Python. Data manipulation includes one-hot encoding for StockCode, Month, and Time, resulting in 54 columns and 1121 rows. 

Next, we split our training and test dataset into 75% and 25%, respectively, and build the model. To predict whether a customer will cancel an invoice or not, the best way is to evaluate our model’s accuracy. We utilize a confusion matrix, which provides four essential classification metrics. True Positive, True Negative, False Positive, and False Negative. For our purpose, it is more critical for the model to correctly predict a customer’s cancellation than to mistakenly predict no cancellation when, in reality, when customer cancels. This means that our focus should be on false negative. And the result of FN is encouraging with 7 out 281 observations as FN. 

To ensure the reliability of our results, we evaluate our model’s performance using AUC and the ROC curve between our training and test sets. This graph illustrates the true positive rate against the false positive rate. A desirable ROC curve is one where the red line, representing the ROC curve, closely hugs the upper-left corner of the graph. This positioning indicates that our model correctly identifies positives much more often than it incorrectly predicts them. 

Additionally, we provide AUC values for both the training and test sets, which are almost 100% and 97% respectively. These high AUC values suggest that our model exhibits strong discriminatory power. However, if the ROC curve appears less smooth, it may indicate that the model requires more data for optimal implementation.


### Linear Regression

To find out the customer purchase behavior, we used Apriori algorithm to find the relationship between purchased items. In this case, we use support, confidence, and lift as parts of the metrics with a minimum support of 0.02. In most cases, 0.05 is usually being used as the minimum support. We chose 0.02 due to the difference between the number of transactions in each country. In this case, most of the transactions came from UK followed by Germany, France, EIRE, and Spain. This different number of transactions per country resulted in a low value of support per itemset and thus we need to lower the value of minimum support. Further analysis can be done to understand purchase behavior in each country separately.

The minimum threshold of 0.7 is chosen for both confidence and lift. Based on the data in the dataset, the algorithm produces 76 association rules whose confidence and lift are bigger than 0.7. From the data, we found that there are 24 association rules (31.58%) that have values of lift more than 10.0. This can also be seen in the graph toward the upper right corner of the chart. These are the product associations that are mostly purchased together by customers in a transaction. We have also tried several combinations for the number of selected features and the number of recursions. From those combinations, we found that 2 numbers of features with 2 recursions provide a slightly better result than the other combinations, which is why we chose to use 2 features with 2 recursions.

During the model fitting using linear regression, the dataset has been split into a training set and a test set. The training set contains 70% of the dataset and the remaining 30% goes into the test set. We found from the result that the R-squared and Adjusted R-squared are 0.836 which means around 83.6% of the predicted data can be explained by the measured features.



### Market-Basket Analysis

To find out the customer purchase behavior, we used Apriori algorithm to find the relationship between purchased items. In this case, we use support, confidence, and lift as parts of the metrics with a minimum support of 0.02. In most cases, 0.05 is usually being used as the minimum support. We chose 0.02 due to the difference between the number of transactions in each country. In this case, most of the transactions came from UK followed by Germany, France, EIRE, and Spain. This different number of transactions per country resulted in a low value of support per itemset and thus we need to lower the value of minimum support. Further analysis can be done to understand purchase behavior in each country separately.

The minimum threshold of 0.7 is chosen for both confidence and lift. Based on the data in the dataset, the algorithm produces 76 association rules whose confidence and lift are bigger than 0.7. From the data, we found that there are 24 association rules (31.58%) that have values of lift more than 10.0. This can also be seen in the graph toward the upper right corner of the chart. These are the product associations that are mostly purchased together by customers in a transaction.

