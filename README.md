
# Applied Data Analytics
## Wedge Project Overview
This project explores data engineering concepts using a rich dataset provided by the Wedge Co-Op, the largest co-operative grocery store in the US, located in Minneapolis, MN. The dataset contains transaction-level data from the point-of-sale (POS) system, spanning from January 1, 2010, to January 2017. The data reflects every item logged in receipts, offering insights into customer behavior, particularly among the 75% of transactions made by member-owners.

The primary challenge involves transforming raw POS records, which include non-item transactions (e.g., payments, taxes, and discounts), into clean, consumable datasets. The project requires understanding various file formats and structures, including different delimiters and formats for missing values.

By working with this dataset, the goal is to develop skills in defining and preparing data sets suitable for further analysis, a critical component of data engineering.


## Wedge Project Tasks
To achieve the project goals, three key tasks are conducted:

#### Building a Transaction Database in Google BigQuery
The first task involves uploading all transaction records from the Wedge Co-Op dataset to Google BigQuery. This requires ensuring correct column data types and properly handling null values. The aim is to structure the data programmatically for better analysis and to upload seemlessly to Google BigQuery.

#### Creating a Sample of Owners
In this task, a Python script is used to extract a sample of owner records (excluding non-owners). The script connects to the Google BigQuery instance, retrieves a list of owners, selects a sample (recommended size: ~250 MB), and saves these records in a local text file. This sample serves as a manageable subset for further local analysis.

#### Building Summary Tables
The final task focuses on creating summary tables to answer business questions such as sales trends, popular items, and owner spending patterns. Using Python and SQLite, the script processes the owner records from Google BigQuery, builds tables (e.g., sales by date, sales by owner, and sales by product description), and stores them in a relational database (.db file). The summary tables provide a streamlined view for quick insights.