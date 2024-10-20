---
title: Azure Devops
parent: Tools
---

# Azure Devops Tool

The Azure DevOps tool is a Python module that provides integration with Azure DevOps, allowing users to interact with various Azure DevOps resources such as repositories, pull requests, commits, and files through the Azure DevOps API.

# Capabilities

The following capabilities are provided:

* Retrieve the content of a specific file from an Azure DevOps repository.
* Retrieve details of a specific pull request from an Azure DevOps repository. 
* Retrieve commits from an Azure DevOps repository with optional filters.
* Retrieve details of a specific commit from an Azure DevOps repository.
* Retrieve pull requests from an Azure DevOps repository with optional filters.
* Search for code in a specified Azure DevOps project.

# Configuration

## Generating Azure DevOps Personal Access Token (PAT)

To use the Azure DevOps tool, you need to generate a Personal Access Token (PAT):

* Log in to your Azure DevOps account.
* Go to User Settings (top right corner) > Personal access tokens.
* Click on "New Token".
* Give your token a name and select the appropriate scopes (at minimum, you'll need "Read" access to Code).
* Click "Create" and copy the generated token.

# Configuring Azure DevOps Tool

Steps:

* Login to Alexandria as an administrator
* Navigate to the tools menu
* Click on or create "Azure DevOps"
* Fill out the following fields:
    * AZURE_DEVOPS_API_URL =
    * AZURE_DEVOPS_PAT =


# Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Azure DevOps tool to help answer questions. For example, if a person asks you to:

Question: Can you retrieve the contents of the file 'README.md' from the 'MyProject/MyRepo' repository?
```

You should use the azure_devops_get_file_contents function to retrieve the file contents.
This small piece of guidance should be sufficient to activate most of the Azure DevOps functionality.

# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones. Here are some examples:

## Retrieving file contents
```
Can you show me the contents of the file 'src/main.py' in the 'MyProject/MyRepo' repository?
```

When you ask this, the AI will interpret it as an Azure DevOps request that should use the tool. It will extract the repository and file path from the question and then submit a request to retrieve the content after authenticating.

## Getting pull request details
```
Can you give me details about pull request #123 in the 'MyProject/MyRepo' repository?
```

The AI will use the azure_devops_get_pull_request function to retrieve the details of the specified pull request.

## Searching for code
```
Can you search for all occurrences of 'TODO' comments in the 'MyProject' project?
```

The AI will use the azure_devops_search_code function to search for the specified query in the project's codebase.

