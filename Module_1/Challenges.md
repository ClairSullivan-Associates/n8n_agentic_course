# Question 1

Utilizing the CSV file in `./data/csv_data/product_reviews.csv`, write a chatbot that can answer the following questions:

### Question 1a
Provide a summary of the data in this CSV file.  In particular, be sure to provide quick statistics on the data present in the table, to include things like an analysis of each column, the distribution of values in that column, etc.

### Question 1b
Given this CSV, generate a thorough data validation report that identifies potential issues with the data.  This report should include things like missing values, inconsistent data types, outliers, and any other potential data quality issues you can identify.  Also prioritize any fixes that you would propose to make to improve the data quality.


# Question 2

You will be analyzing a complicated email thread between multiple participants.  The email thread is provided in the file `./data/docs/email.txt`.  

### Question 2a
You should create a tool that can get this file from GitHub.  Once this email chain is obtained, you will need to analyze it to create a tracker of all of the tasks to provide a high-level summary to management.  

In particular, you will create and agent that will parse the email thread to create a spreadsheet in Google Sheets that contains the following columns:

- task name
- responsible person(s)
- deadline
- status

Copy the results of the file as text into the scorer when you are completed.

### Question 2b
Identify the key milestones, final release date, whether it is on schedule or delayed, and if delayed provide reasoning for the delay.


# Question 3

You have access to a series of completely fictitious resumes in markdown format in the folder `./data/resumes`.  You will need to create a workflow that gets these resumes off to the GitHub repository and prepares them for analysis.  Note that you should NOT assume all files in this folder are in markdown format, so you will need to validate the files first.  Create a workflow that scores these resumes based on the job ads below.  You will need the analysis saved to a Google Sheet with the following columns:

- name
- email
- phone number
- score
- justification of the score

Once you have written your results to a Google Sheet, you will copy and paste the results into the scorer.

### Question 3a
**Principal AI Engineer - Enterprise Agent Platform**
We are seeking a Principal AI Engineer to architect and lead the development of our next-generation enterprise AI agent platform serving millions of users. The ideal candidate has 10+ years of experience building production AI systems at scale, with deep expertise in multi-agent architectures, LLM orchestration, and distributed systems. You will lead a team of engineers, define technical strategy, and establish best practices for responsible AI development while driving innovation in agentic workflows. This role requires a proven track record of deploying 15+ production AI agents, experience with enterprise-scale infrastructure (AWS/GCP/Azure), and the ability to translate complex business requirements into scalable technical solutions. Published research, patents, or significant open-source contributions in AI/ML are strongly preferred.

### Question 3b
**Senior AI Engineer - AI Agent Development**
We are seeking a Senior AI Engineer to design and deploy production AI agents that automate business processes and enhance customer experiences. The ideal candidate has 5-7 years of experience building ML systems, with at least 2 years focused on LLM applications, RAG systems, and agent architectures. You will mentor junior engineers, collaborate with product teams to define AI capabilities, and own the end-to-end development of intelligent automation solutions. This role requires hands-on expertise with modern AI frameworks (LangChain, OpenAI API, vector databases), cloud infrastructure (AWS/Azure/GCP), and a proven track record of deploying at least 3-5 AI agents to production. Experience with agent orchestration tools like n8n and a track record of measurable business impact through AI solutions are essential.

# Question 4

Within the course repository are 10 issues that need to be analyzed and routed.  Your task is to create a workflow that will get issues 71 through 80 from the GitHub repository.  Based on the content of the issue, you will need to determine which team each issue should be routed to from the following list:

- PM (Product Management)
- Frontend Engineering
- Backend Engineering
- Finance

You also need to determine based on the content of the issue how much of a priority the issue is.  The priority levels are from 1 (low, we will get it it at some point) to 5 (critical, really important things are failing or needing this).  Once you have determined the team and priority for each issue, you will need to create a Google Sheet with the following columns:

- issue number
- issue title
- assigned team
- prioritization

Once you have written your results to a Google Sheet, you will copy and paste the results into the scorer.