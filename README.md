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

### Principal Component Analysis

### Logistic Regression

### Linear Regression

### Market-Basket Analysis
