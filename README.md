## Mental Health and Social Media Balance Analysis Using Apache Hive
# Project Overview
This project focuses on performing data analysis and extracting meaningful insights from a Mental Health and Social Media Balance dataset using Apache Hive.
The primary objective is to utilize Hive’s SQL-like capabilities to explore the relationship between screen time, social media usage, and mental well-being.
The analysis demonstrates how structured mental health and digital behavior data can be managed efficiently on a Big Data platform (Hadoop/Cloudera) and queried using HiveQL for analytical reporting and decision-making support.

# Dataset Description
The dataset, Mental_Health_and_Social_Media_Balance_Dataset.csv, contains detailed information about users’ social media habits and mental health indicators.
Attributes include:
•	User_ID — unique identifier for each participant.
•	Age — age of the participant.
•	Gender — demographic category (Male/Female/Other).
•	Platform — primary social media platform used.
•	Screen_Time — average time (in hours) spent on social media per day.
•	Mental_Health_Score — self-reported mental health rating on a standardized scale.

## Objectives
# The key objectives of this project are:
•	To import and store CSV data into Hive tables efficiently.
•	To perform analytical queries on mental health and social media usage patterns.
•	To extract data-driven insights such as:
o	Average screen time by gender or platform.
o	Correlation between screen time and mental health.
o	Platform-wise mental health score comparisons.
o	Age group–based differences in social media habits.
o	Identifying trends in digital wellness behavior.

## Technologies Used
•	Apache Hive
•	Hadoop Distributed File System (HDFS)
•	Cloudera QuickStart Environment
•	HiveQL (SQL-like query language)
•	CSV file ingestion via HDFS

# Steps Performed
1.	Database and Table Creation
Created a new database social_media_analysis in Hive.
Defined an external table schema corresponding to the CSV structure:
CREATE EXTERNAL TABLE IF NOT EXISTS mental_health_balance (
  User_ID STRING,
  Age INT,
  Gender STRING,
  Platform STRING,
  Screen_Time DOUBLE,
  Mental_Health_Score DOUBLE
)
ROW FORMAT SERDE 'org.apache.hadoop.hive.serde2.OpenCSVSerde'
WITH SERDEPROPERTIES (
  "separatorChar" = ",",
  "quoteChar" = "\""
)
STORED AS TEXTFILE
LOCATION '/user/hive/warehouse/mental_health_data/';
2.	Data Loading
Uploaded the CSV file from local storage (/home/cloudera/Desktop/mental.csv) to HDFS.
hdfs dfs -put /home/cloudera/Desktop/mental.csv /user/hive/warehouse/mental_health_data/
3.	Data Analysis Using HiveQL
Executed multiple analytical queries to explore mental health and social media balance:
SELECT COUNT(*) → total number of records.
GROUP BY → gender and platform analysis.
AVG() → average screen time and mental health scores.
ORDER BY + LIMIT → identify top platforms or high-risk groups.
4.	Insight Extraction and Reporting
o	Generated summarized analytical results for mental wellness trends.

## Key Insights
1.	Average Screen Time — The mean daily screen time among users indicates moderate-to-high engagement across social media platforms.
2.	Gender-wise Screen Time — Males and females show comparable screen usage, with slight variations in platform preference.
3.	Platform Popularity — Instagram and YouTube emerged as the most-used platforms.
4.	Mental Health Patterns — Users with higher screen time often recorded lower mental health scores.
5.	Age Group Analysis — Teenagers and young adults (13–30 years) had the highest screen times.
6.	Platform Impact — Professional platforms (e.g., LinkedIn) users reported better mental health averages.
7.	Correlation Trend — A negative correlation was observed between Screen_Time and Mental_Health_Score.
8.	High-risk Segment — Users exceeding 5+ hours of daily screen time tend to have below-average well-being.
9.	Gender-based Mental Health — Average mental health scores were slightly higher for females in the dataset.
10.	Overall Digital Well-being — Data indicates that balanced screen habits are associated with improved mental health ratings.

## Conclusion
This project demonstrates how Apache Hive can be leveraged for large-scale analysis of behavioral and mental health data.
By combining Big Data storage (HDFS) and HiveQL querying, the study reveals actionable insights into how digital habits affect psychological well-being.
The approach showcases Hive’s effectiveness in:
•	Managing structured datasets.
•	Performing SQL-like analytics on large-scale data.
•	Supporting data-driven decisions in mental health awareness and digital wellness research.

