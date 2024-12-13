# Portfolio

# DAP Design and Implementation
Descriptive Analysis

# <img width="721" alt="Screenshot 2024-12-13 at 7 25 37 PM" src="https://github.com/user-attachments/assets/337f04cf-4430-4552-8db0-531e28c0f6a7" />

Step 1: Data Ingestion 
<p>
For data ingestion, I selected the dataset "Council voting records" and applied filters for the year 2024 (October) and specific meeting types: We also have “City Finance & Services” and “Public Hearing”. Also, the data set contains a feature to define the voting year as 2024 and the voting month as October. This reduced the data set to 462 records, according to the records shown in the data set portal on 11/23/24. Next, I downloaded the filtered records in Excel format. After that, I had to go into my AWS console to create buckets in S3 for storage and analysis.
</p>

# <img width="815" alt="Screenshot 2024-12-13 at 7 28 21 PM" src="https://github.com/user-attachments/assets/2e22cf92-a55a-49a4-87a8-3d0b9740d44d" />

Step 2: Data Profiling
<p>
  Having uploaded votingdataset-tej into AWS Glue DataBrew, I conducted the data profile analysis on the said dataset. It turned out that there were 462 rows and 9 columns in the overall data evaluation. Metrics of internal data quality: All cells in the dataset were valid; therefore, 0% were missing cells. There were no duplicate rows in the dataset, meaning 100% unique rows. The data type of all of the columns was stated to be a string. In addition, a correlation matrix was computed, though this was not possible since the dataset has no numeric features.
</p>

# <img width="723" alt="Screenshot 2024-12-13 at 7 35 10 PM" src="https://github.com/user-attachments/assets/f212ed69-4dbe-41ea-863e-527e832dc7f9" />

Step 3: Data Cleaning

<p>
  Several transformations were performed on DataBrew by running a recipe to clean data. Key modifications included renaming columns for clarity and standardization: Variables consisting of more than one word were modified to contain underscores, where Meeting Type was changed to Meeting_Type, Vote Date to Vote_Date, and Vote Number to Vote_Number and Agenda Description to Agenda_Description, and so on. The applied imputing strategy was the last valid value method because it gave the best result in handling null values. Vote_Start_Date_Time, like other related fields, was formatted to a standard date format to make their comparison easier. The final compiled data set was checked against the City of Vancouver’s database and has proven to be more than ninety percent accurate.
</p>

# <img width="700" alt="Screenshot 2024-12-13 at 7 36 50 PM" src="https://github.com/user-attachments/assets/3f32b22a-657e-4f1e-9ff8-8253fd34505e" />

Step 4: Data Pipeline Design

<p>
  After that, the following workflow loaded the data set from an S3 bucket named ‘Extract Council voting Records’. Some additional columns have been omitted to keep only the necessary ones. An aggregation step was then applied to bring out the concluding summary of the data and the answer to the query, which is “How many Candidates have taken part in Council elections in the month of October”. The processed data was stored in two S3 buckets: A second was labeled ‘Load for Users,’ and the other one ‘Load for System.’ This meant that the supply was controlled so that the data chain was kept clean for efficient analysis.
</p>

# <img width="627" alt="Screenshot 2024-12-13 at 7 39 23 PM" src="https://github.com/user-attachments/assets/6444add9-cdfc-438a-8c73-6ffdeeb4d0d1" />



