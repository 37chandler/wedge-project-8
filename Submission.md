# Applied Data Analytics


## Wedge Project
The Wedge Project offers a deep dive into data engineering using transactional data from the Wedge Co-Op, the largest co-operative grocery store in the US. This project contained POS records from 2010 to 2017, capturing detailed transaction information primarily from member-owners. The data required significant transformation to clean and prepare it for analysis. This project highlights the importance of data pipelines, data cleaning, and the conversion of raw transactional data into structured formats that support business insights.

### Task 1 : Building a Transaction Database in Google BigQuery
 The first task involves uploading all transaction records from the Wedge Co-Op dataset to Google BigQuery. This requires ensuring correct column data types and properly handling null values. The following file processes the large zipped files into correctly formatted csv files ready for upload to GBQ:
* [task_1_process_files.ipynb](/task_1_process_files.ipynb)  

The second part of task 1 using the following file to upload all processed csv files to GBQ:

* [task_1_upload_GBQ.ipynb](/task_1_upload_GBQ.ipynb)


### Task 2
The second task extracts a sample of owner records (excluding non-owners). The following script connects to the Google BigQuery instance, retrieves a list of owners, selects a sample (recommended size: ~250 MB), and saves these records in a local text file. This sample serves as a manageable subset for further local analysis.

* [task_2.ipynb](/task_2.ipynb)

### Task 3
Task 3 focuses on creating summary tables to answer business questions such as sales trends, popular items, and owner spending patterns. The following script file processes the owner records from Google BigQuery, builds three summary tables and stores them in a relational database. The summary tables provide a streamlined view for quick insights. 

* [task_3_ipynb](task_3.ipynb)

## Query Comparison Results
Fill in the following table with the results from the
queries contained in `gbq_assessment_query.sql`. You only
need to fill in relative difference on the rows where it applies.
When calculating relative difference, use the formula
` (your_results - john_results)/john_results)`.
| Query | Your Results | John's Results | Difference | Rel. Diff |
|---|---|---|---|---|
| Total Rows | 85760139| 85760139 | 0 | 0 |
| January 2012 Rows | 1070907 | 1070907  | 0 | 0 |
| October 2012 Rows | 1042287 | 1042287  | 0  | 0 |
| Month with Fewest | Feb | Feb | No | NA |
| Num Rows in Month with Fewest | 6556770 | 6556770 | 0 | 0 |
| Month with Most | Jan | Jan | No | NA |
| Num Rows in Month with Most | 7993503 | 7993503 | 0 | 0 |
| Null_TS | 72189676* | 7123792 | 65065884 | 9.13 |
| Null_DT | 0 | 0 | 0 | 0 |
| Null_Local | 234843 | 234843 | 0 | 0 |
| Null_CN | 0 | 0 | 0 | 0 |
| Num 5 on High Volume Cards | 14987 | 14987 | Yes | NA |
| Num Rows for Number 5 | 460625 | 460630 | -5 | -0.00001 |
| Num Rows for 18736 | 12153 | 12153 | 0 | 0 |
| Product with Most Rows | banana organic | banana organic | No | NA |
| Num Rows for that Product | 908639 | 908639 | 0 | 0 |
| Product with Fourth-Most Rows | avocado hass organic | avocado hass organic | No | NA |
| Num Rows for that Product | 456771 | 456771 | 0 | 0 |
| Num Single Record Products | 2741 | 2769 | -28 | -0.010 |
| Year with Highest Portion of Owner Rows | 2012 | 2012 | No | NA |
| Fraction of Rows from Owners in that Year | 0.74 | 0.74 | 0 | 0 |
| Year with Lowest Portion of Owner Rows | 2017 | 2017 | No | NA |
| Fraction of Rows from Owners in that Year | 0.75 | 0.75 | 0 | 0 |

\*  Null_TS: The null values for this column are strings 'NULL" vs actual *null* values. I realized my initial code is incorrect, setting everything to 'NULL" vs np.nan. This still may not account for the major discrepancy between UMT_MSBA data and wedge-project-np data though. I am going to continue some exploration of what may cause this deviation.  

## Reflections
Working with large dataframes within VS Code proved challenging. I'm accustomed to the intuitive, visual nature of Excel, where I can easily explore datasets. With VS Code, working with datasets—especially for large zip files—required me to adjust my approach. For example, identifying patterns in missing values was difficult without the same level of visual context I'm used to. This project made me realize that I need much more practice working with large datasets, particularly in efficiently navigating and exploring them using tools like df.shape and other methods for summarizing and inspecting data.  

Setting up the schema and handling null values in Google BigQuery was another obstacle. I spent considerable time configuring the datetime format, and while I eventually managed to achieve the correct TIMESTAMP format, I’m still unsure exactly how it worked. This experience highlighted that seemingly simple tasks can be deceptively complex. I also struggled immensely with handling null values. Identifying how missing values were originally denoted in the data and then converting them into a format compatible with Google BigQuery was particularly challenging.

Throughout the project, I also realized how easy it is to get caught up in a "rabbit hole." I went through multiple iterations of my code and, at several points, scrapped everything to start over. For instance, I had a script that worked well with small CSV files, but it crashed with larger files, and I couldn't determine the issue. My takeaway is that sometimes even a small mistake can disrupt the entire process and identifying the root cause can be extremely challenging. Currently, my go-to strategy is to start over from scratch, but I hope to develop more efficient debugging techniques in the future.
