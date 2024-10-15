# Salesforce Tool

The Salesforce tool is a Python module that provides integration with the Salesforce CRM platform. It allows users to interact with various Salesforce objects through the Salesforce API using SOQL (Salesforce Object Query Language) queries.

## Capabilities

The following capabilities are provided:

* Execute generic SOQL queries across all Salesforce objects.
* Retrieve data from Salesforce in a structured format.
* Convert query results to CSV files for easy data analysis.

## Configuration

### Generating Salesforce API Credentials

To use the Salesforce tool, you need to have the following credentials:

1. Salesforce Username
2. Salesforce Password
3. Salesforce Security Token
4. Salesforce Domain

To obtain these credentials, follow these steps:

1. Log in to your Salesforce account.
2. Go to Setup (gear icon in the top right corner).
3. In the Quick Find box, search for "My Personal Information" and select "Reset My Security Token".
4. Click on "Reset Security Token" button. Salesforce will email you a new security token.
5. Note down your username, password, and the domain of your Salesforce instance (e.g., login.salesforce.com for production or test.salesforce.com for sandboxes).

### Configuring Salesforce Tool

Steps:

1. Login to Alexandria as an administrator 
2. Navigate to the tools menu
3. Click on Salesforce
4. Fill out the following fields:
   * SF_USERNAME = <Your Salesforce Username>
   * SF_PASSWORD = <Your Salesforce Password>
   * SF_SECURITY_TOKEN = <Your Salesforce Security Token>
   * SF_DOMAIN = <Your Salesforce Domain>

## Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant may not use the tool automatically. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Salesforce tool to help answer questions. For example, if a person asks you to:

Question: Can you retrieve the top 5 Accounts from Salesforce?

You should use the Salesforce tool to execute a SOQL query like:
SELECT Id, Name FROM Account ORDER BY CreatedDate DESC LIMIT 5
```

This small piece of guidance should be sufficient to activate the Salesforce functionality.

## Usage

To use this tool, you can start with very simple scenarios and then grow into more complex queries.

### Executing a SOQL Query

```
Can you retrieve the top 5 Accounts from Salesforce?
```

When you ask this, the AI will interpret it as a Salesforce request that should use the tool. It will construct and execute a SOQL query similar to:

```sql
SELECT Id, Name FROM Account ORDER BY CreatedDate DESC LIMIT 5
```

The tool will then:

* Execute the query against the Salesforce API.
* Generate a CSV file with the results.
* Provide a summary of the results and a URL to download the CSV file.

### Listing Customer Support Tickets

When Salesforce is used as a customer ticketing system, you can retrieve customer support tickets using a SOQL query. Here's an example of how to list recent customer support tickets:

```
Can you retrieve the 10 most recent customer support tickets from Salesforce?
```

```sql
SELECT Id, CaseNumber, Subject, Status, Priority, CreatedDate, ContactId, AccountId 
FROM Case 
ORDER BY CreatedDate DESC 
LIMIT 10
```


### Advanced Usage
You can execute more complex SOQL queries to retrieve data from various Salesforce objects. For example:

```
Can you find all Opportunities with a value greater than $100,000 that were created in the last 30 days?
```
The AI would construct a query like:

```
SELECT Id, Name, Amount, CloseDate FROM Opportunity 
WHERE Amount > 100000 AND CreatedDate = LAST_N_DAYS:30
```

Remember that the complexity of the queries you can execute depends on your Salesforce data model and the permissions associated with the Salesforce user credentials you've configured.
