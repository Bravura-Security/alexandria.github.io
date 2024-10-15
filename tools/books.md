# Books Tool

The Books tool is a Python module that provides integration with Alexandria's book management system. It allows users to interact with book pages and perform searches within books through the Alexandria API.

# Capabilities

The following capabilities are provided:

* Retrieves a text copy of a specific page in a book from Alexandria.
* Performs a natural language search on the contents of a book to find relevant pages.

# Configuration

## Configuring Books Tool

The Books tool is integrated into the Alexandria system and doesn't require separate configuration. It uses the existing Alexandria session for API calls.

## Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant might not know when to use it. To ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Books tool to help answer questions. 
```

This small piece of guidance should be sufficient to activate the Books functionality.

# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones.

## Retrieving a specific book page

```
How do you configure the salesforce integration?
```

When you ask this, and a book is attached to the assistant, then this tool will retrieve the id of the book and search within the book for details about configuring salesforce. 

