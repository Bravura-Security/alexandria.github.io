---
title: Microsoft Excel Assistant
parent: General
nav_order: 1
---

# Microsoft Excel Assistant

The excel assistant allows people to talk to their excel documents. 

# How to chat with an excel document

1. Login to alexandria
1. Create the excel assistant that is defined below
1. Click "ATTACH FILE" from the UI
1. Wait for the file to process (for larger files this may take 10+ seconds)
1. Ask a question such as "can you count how many requirements are defined in the document?"

Limitations include:

| Limitation | Summary |
|------------|---------|
| 25 MB File Size | to protect against denial of service attacks, we block uploading of documents greater than 25 MB in size |
| 5 row headers | If your spreadsheet tabs have headers larger than 5 rows they need special consideration described below |
| 500 columns | We have tested spreadsheets with up to 500 coumns in a single tab | 
| 25 tabs | We have tested with spreadsheets that have up to 25 tabs |


# Configuration

We recomend you create the following Assistant


**Title**

```
Excel Spreadsheet assistant
```

**AI Model**

```
Advanced: We need to create queries on the underlying spreadsheet data. This can be complex and so its perferred to use the slower but higher quality models for this task. 
```

**Description**

```
You are an expert at working with excel files.

You can answer questions such as

* Doing calculations on a spreadsheet
* Retrieving data from a spreadsheet
* Interpreting contents of a spreadsheet.
```

**Tools**

```
You will use duckdb functions to access spreadsheets.

You will be provided the first 10 lines of each tab of the spreadsheet so you can

* Identify if the spreadsheet has headers
* Identify the columns in the spreadsheet
* Identify the types of data in the spreadsheet.

Guidelines you should follow:

* You are strongly encouraged to reference these summaries to help you plan out what queries and how to interpret the data.
* Its critically important you don't answer with just the summary data provided. Query the spreadsheet for the full context.

# Examples

## Example 1

Calculate the average one from a spreadsheet named "Deals" and that has an "Opportunities" tab and a "Won" Column.

SELECT avg(Won) FROM Opportunities

## Example 2

what vbus are mentioned in the attached spreadsheet?

SELECT avg(VBU) FROM Opportunities

## Example 3

The attached spreadsheet is Questionaire_Product_Final.xslx. It has a tab called "Technical Questions".

When someone asks you the below question

can you summarize rows 100 through 120 of the "Technical Questions" tab in the attached spreadsheet

You should assume the following:

* The spreadsheet is loaded. And each tab in the spreadsheet is given a name. In this case, the tab is slightly different than what the user stated. "5. Technical Questions". This will then ultimately be named will be named "5._Technical_Questions" for queries.

You should then run the below query

SELECT * FROM '5._Technical_Questions' LIMIT 21 OFFSET 99
```

**Content**

```
You are an expert at doing data analysis on spreadsheets. You should be descriptive and detailed in your responses. Ensuring you are as factually correct as possible. Always show your work when you are summarizing content for people. 
```

# Best Practices

The tool can handle very large spreadsheets. We currently support 25MB spreadsheets with tabs that have as many as 500 rows. But it cannot handle all spreadsheets. Spreadsheets with the following characteristics will need additional guidance to be given to process them.

* If the spreadsheet has no headers at all, then it is best to put in the content tab how the columns of each sheet should be interpreted. You make want to create purpose specific assistants for each different type of spreadsheet that falls into this category. 

* If the header area of a tab is more than 3 rows in hight this can really impact the ability for alexandria to "see" the spreadsheet and strategize how to query it. Its best if your header is only 1-3 rows in hight. If its larger than this you may need to create purpose specific assistants to explain the contents of the tabs. When their data begins. When their data ends.



# How it works under the covers

The excel assistant works by taking excel files that are attached to a chat and converting them to a database that can then be queried using [DuckDB](https://duckdb.org/). Each tab of the spreadsheet is turned into a table. And each row in the sheet becomes a row in the database table. 

Additionally, the first 5 lines of each spreadsheet are converted into a markdown table that can be read by the AI. This is critical because the AI needs to be able to "see" the spreadsheet just like do to understand what columns in the table exist and examples of the data in each column. We have chosen 5 rows to "see" as a balance between seeing enough in most normal spreadsheets to be able to determine how to query them while also supporting very large and complex spreadsheets where reading 20+ rows of content might overwhelm the AI. 

So when people ask a question of a spreadsheet, the steps that are taken are:

1. Aleandria will "look at" the first 5 rows of each sheet and strategize one or more queries that can be used to query the data and determine next steps.
1. Alexandria will send these queries to the duckdb tool to run the queries on the temporary database. 
1. Alexandria will then interpret the resulting data to best answer the users question. 