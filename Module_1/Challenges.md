# Question 1

Utilizing the CSV file in `./data/csv_data/product_reviews.csv`, write a chatbot that can answer the following questions:

## Question 1a
Provide a summary of the data in this CSV file.  In particular, be sure to provide quick statistics on the data present in the table, to include things like an analysis of each column, the distribution of values in that column, etc.

## Question 1b
Given this CSV, generate a thorough data validation report that identifies potential issues with the data.  This report should include things like missing values, inconsistent data types, outliers, and any other potential data quality issues you can identify.  Also prioritize any fixes that you would propose to make to improve the data quality.


# Question 2

You will be analyzing a complicated email thread between multiple participants.  The email thread is provided in the file `./data/docs/email.txt`.  

## Question 2a
You should create a tool that can get this file from GitHub.  Once this email chain is obtained, you will need to analyze it to create a tracker of all of the tasks to provide a high-level summary to management.  

In particular, you will create and agent that will parse the email thread to create a spreadsheet in Google Sheets that contains the following columns:

- task name
- responsible person(s)
- deadline
- status

Copy the results of the file as text into the scorer when you are completed.

## Question 2b
Identify the key milestones, final release date, whether it is on schedule or delayed, and if delayed provide reasoning for the delay.
