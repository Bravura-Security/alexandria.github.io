# Jira Tool

The Jira tool is a Python module that provides integration with Atlassian's Jira issue tracking and project management platform. It allows users to interact with Jira through its REST API, primarily focusing on searching for issues.

# Capabilities

The following capabilities are provided:

* Performs a Jira search using JQL (Jira Query Language) and returns the results.

# Configuration

## Generating Jira API Token

To use the Jira tool, you'll need to generate an API token. Follow these steps:

1. Log in to your Atlassian account at https://id.atlassian.com/manage/api-tokens
1. Click "Create API token"
1. Give your token a name (e.g., "Alexandria Jira Integration")
1. Click "Create"
1. Copy the generated token (you won't be able to see it again)

## Configuring Jira Tool

Steps:

1. Login to Alexandria as an administrator
1. Navigate to the tools menu
1. Click on Jira
1. Fill out the following fields:

    * JIRA_USER =
    * JIRA_API_TOKEN =
    * JIRA_SERVER_URL = (e.g., https://your-domain.atlassian.net)


# Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Jira tool to help answer questions. For example, if a person asks you to:

Question: Can you find all open issues for the BSCS project?

You should use the Jira search tool with an appropriate JQL query, such as:
jira_search(query="project = BSCS AND status = Open")
```

This small piece of guidance should be sufficient to activate the Jira functionality.

# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones.

## Performing a Jira search

To search for Jira issues, you can use the jira_search function. Here's an example:

```
Can you find all high-priority issues in the BSCS project?
```

When you ask this, the AI will interpret it as a Jira request that should use the tool. It will construct an appropriate JQL query and submit a request to retrieve the content after authenticating.