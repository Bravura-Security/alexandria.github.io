# DuckDB Tool

The DuckDB tool is a Python module that provides integration with DuckDB, allowing users to execute SQL queries on CSV or Excel data. It enables data analysis and manipulation directly within the Alexandria platform.

# Capabilities

The following capabilities are provided:

* Execute SQL queries on CSV or Excel data
* Support for both local files (within the session) and remote files (via URL)
* Flexible input formats: CSV and Excel (including multi-sheet Excel files)
* Configurable output formats: JSON and CSV
* Automatic registration of data as tables in DuckDB
* Error handling and logging for robust operation

# Configuration

## Configuring DuckDB Tool

The DuckDB tool is designed to work within the Alexandria platform and doesn't require separate configuration. It utilizes the session management system of Alexandria for handling file operations.

When you attach a spreadsheet to a chat session, we do the folllowing actions on it

* Convert the spreadsheet into an duckdb sqlite database to run queries on.
* Convert the top 5 lines of each spreadsheet into a markdown summary to give context about what is contained in each sheet and some of the sample data contained in it. 

# Usage

To use this tool, you can start with simple queries and then move on to more complex scenarios. Its recommended you add the below to the "Tools" area of the assistants you will use for working with spreadsheets

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

Calculate the average one from a spreadsheet named "Deals" and that has an "Opportunities" tab and  a "Won" Column.

SELECT avg(Won) FROM Opportunities

## Example 2

The attached spreadsheet is Questionaire_Product_Final.xslx. It has a tab called "Technical Questions". 

When someone asks you the below question 

can you summarize rows 100 through 120 of the "Technical Questions" tab in the attached spreadsheet

You should assume the following:
* The spreadsheet is loaded. And each tab in the spreadsheet is given a name. In this case, the tab is slightly different than what the user stated. "5. Technical Questions". This will then ultimately be named will be named "5._Technical_Questions" for queries.

You should then run the below query

SELECT * FROM '5._Technical_Questions' LIMIT 21 OFFSET 99

```

While a little technical, these examples give the assistant the knowledge to rationalize how to navigate quite complex spreadsheets. They show how the data is transformed into a duckdb database and gives examples of queries that allow for effective processing of the data. 

## Basic Query Execution

To use the tool, you should 


1. Attach a spreadsheet to a chat 
1. As a question such as "can you total up the revenue from the opportunities tab?"

This will trigger alexandrdia to create a query that will sum the content in a column named similar to revenue in a tab named similar to opportunities.

