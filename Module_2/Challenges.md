# Instructions

There are two major sections to this module's challenges: access the Bill.com v3 API for workflows and extracting information from PDFs and webpages.

# Bill.com v3 API Instructions

You will be provided during class with the credentials to access a Bill Sandbox account that has data preloaded into it.  Using the v3 API and any n8n nodes you need, your task will be to create an agent that answers the following questions.  

There are practically limitless ways you can approach this problem.  For example, you could create one chatbot for each of the following.  Or you could create a single chatbot with different tools to handle and and all of the following.  Or you don't have to create a chatbot at all and just answer each question below through updating the user and system prompts.  It is completely up to you!  However, you are instructed to automate as much of the process as possible.  Your submitted solutions should be ones that were obtained with just a single chat or manual trigger and answer the entire question.

**Important Note**
You will use the following URL to access the API: `https://gateway.stage.bill.com/connect/v3/login` 

**Hint**
Be sure to consult the [Bill.com v3 API documentation](https://developer.bill.com/reference/api-reference-overview) for more information on how to access the API and its endpoints.  In particular, you are encouraged to explore pagination for this API.


## Question 1

Within the Sandbox you will find a vendor named "San Jose Music Supplies."  You will need to determine how much money they owe this organization as well as how late their required payments are.  Using this information, construct an email to them reminding them of their outstanding balance and requesting payment.  Use language that is appropriate to how late their payments are.  Copy and paste the text of the email into the scorer when you are completed.

## Question 2

Also within the Sandbox is the vendor named "Green Thumb Landscaping" that has some outstanding payments.  Construct an email to them reminding them of their outstanding balance and requesting payment. Use language that is appropriate to how late their payments are.  Copy and paste the text of the email into the scorer when you are completed.

## Question 3

You are the accountant for this simulated organization and have to provide a summary of the outstanding balances due to the organization.  Obtain this information and use it to craft an email to your boss with this information.  Copy and paste the text of the email into the scorer when you are completed.

## Question 4

Based on the data in the Sandbox, forecast potential cash flow issues based on increasing overdue trends and recommend actions such as changes to payment terms or prioritization of collections.  Copy and paste the text of this forecast into the scorer when you are completed.

## Question 5

Create a Google Sheet with complete details on all invoices in the system, including:

- Vendor Name
- Vendor ID
- Invoice number
- Invoice amount
- Number of days late (assume today's date is 2025-04-10 for this exercise) 

Copy and paste the results of the Google Sheet into the scorer when you are completed.


# Data Extraction Instructions

You will be working with the US Securities and Exchange Commission (SEC) API for this section of the module.  The SEC provides a public API that allows users to access filings made by publicly traded companies.  In order to access it, you will need to create a free account and obtain an API key.  You can find more information about the SEC API here: `https://sec-api.io/`.

When working with this API, we will be downloading PDFs from the site.  These follow a particular format.  For example, to access the PDF of the September 30, 2025 Form 10-Q (Quarterly Earnings Report) for Bill Holdings, you will using the following URL:

`https://www.sec.gov/Archives/edgar/data/1786352/000162828025050328/bill-20250930.htm`

Be sure to consult the SEC API documentation for more information on how to access filings and their formats, in particular [this website](https://sec-api.io/docs/sec-filings-render-api) on how to GET PDF files.

You will create a workflow that extracts specific information from these filings based on the questions below.

## Question 6

Create an agent that downloads the Bill Holdings From 10-Q for the quarter ending September 30, 2025.  From this file, extract the following information and write it to a Google Sheet with the following columns:

- Quarter
- Total assets
- Net income (loss)

# Question 7

From this same file, extract the data for the Company's available-for-sale debt securities, included within short-term investments and funds held for customers, by remaining contractual maturity as of September 30, 2025.

