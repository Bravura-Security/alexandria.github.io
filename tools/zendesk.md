# Zendesk Tool

The Zendesk tool is a Python module that provides integration with the Zendesk customer service and support ticketing system. It allows users to search for tickets and knowledge base articles through the Zendesk API.

# Capabilities

The following capabilities are provided:

* Search for tickets in Zendesk with various filters and criteria.
* Search the Zendesk Knowledge Base for articles.

# Configuration
## Generating Zendesk API Token

To use the Zendesk tool, you need to generate an API token. Follow these steps:

* Log in to your Zendesk account as an administrator.
* Go to Admin Center > Apps and Integrations > APIs > Zendesk API.
* Click on the "Add API token" button.
* Give your token a descriptive name and click "Create".
* Copy the generated API token and keep it secure.

## Configuring Zendesk Tool

Steps:

* Login to Alexandria as an administrator
* Navigate to the tools menu
* Click on Zendesk
* Fill out the following fields:
    * ZENDESK_URL = (e.g., https://yourcompany.zendesk.com)
    * ZENDESK_USER =
    * ZENDESK_API_TOKEN =

# Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Zendesk tool to help answer questions. For example, if a person asks you to:

Question: Can you search for tickets related to "password reset"?

You should use the zendesk_search_tickets function with the appropriate query.
```

This small piece of guidance should be sufficient to activate most of the Zendesk functionality.

# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones.

## Searching for tickets

```
Can you search for tickets with the status "open" created in the last 7 days?
```
When you ask this, the AI will interpret it as a Zendesk request that should use the tool. It will construct an appropriate query and use the zendesk_search_tickets function to retrieve the results.

## Searching the Knowledge Base
```
Can you find knowledge base articles about "two-factor authentication"?
```
The AI will use the zendesk_search_knowledge_base function to search for relevant articles in the Zendesk Knowledge Base.

## Advanced Usage

The Zendesk tool supports various search queries for tickets. Here are some examples:

* Search for a specific word: Greenbriar
* Search for an exact string: "Greenbriar Corporation"
* Search for a ticket by id: 3245227
* Search for a resource type: type:user "Jane Doe"
* Search by ticket status: type:ticket status:open
* Search by date: type:organization created<2099-05-01
* Search between dates: type:ticket created>2024-07-24 created<2024-07-30
* Search for tickets created yesterday: type:ticket created=2024-07-24

You can use these advanced search queries to create more specific and powerful searches in your Zendesk environment.