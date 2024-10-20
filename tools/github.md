---
title: Github
parent: Tools
---

# GitHub Tool

The GitHub tool is a Python module that provides integration with the GitHub platform. It allows users to interact with various GitHub resources such as repositories, commits, pull requests, and file contents through the GitHub API.

# Capabilities

The following capabilities are provided:

* Retrieves commits from a GitHub repository with optional filters.
* Retrieves details of a specific commit from a GitHub repository.
* Retrieves the content of a specific file from a GitHub repository.
* Retrieves pull requests from a GitHub repository with optional filters.
* Searches for code in GitHub repositories.
* Lists branches for a repository.
* Gets information about a GitHub repository.

# Configuration

## Generating GitHub API Token

1. Go to your GitHub account settings.
1. Navigate to "Developer settings" > "Personal access tokens".
1. Click on "Generate new token".
1. Give your token a descriptive name and select the necessary scopes (at least repo for most operations).
1. Click "Generate token" and copy the generated token.

## Configuring GitHub Tool

Steps:

1. Login to Alexandria as an administrator
1. Navigate to the tools menu
1. Click on GitHub
1. Fill out the following fields:
    * GITHUB_TOKEN =

# Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the GitHub tool to help answer questions. For example, if a person asks you to:

Question: Can you retrieve the contents of the README.md file from the main branch of the repository 'owner/repo'?

You should use the github_get_file_contents function to retrieve the file contents.
```

This small piece of guidance should be sufficient to activate most of the GitHub functionality.

# Usage
To use this tool, you can start with very simple scenarios and then grow into more complex ones:

## Retrieving file contents

```
Can you show me the contents of the README.md file in the main branch of the repository 'owner/repo'?
```

When you ask this, the AI will interpret it as a GitHub request that should use the tool. It will extract the repository, file path, and branch information from the question and then submit a request to retrieve the content after authenticating.

## Listing commits
```
Can you list the last 5 commits for the repository 'owner/repo' on the 'develop' branch?
```

The AI will use the github_get_commits function to retrieve the specified number of commits for the given repository and branch.

## Searching code
```
Can you search for occurrences of 'TODO' in the code of the repository 'owner/repo'?
```
The AI will use the github_search_code function to search for the specified query in the repository's code.

## Getting pull request information
```
Can you show me the open pull requests for the repository 'owner/repo'?
```
The AI will use the github_get_pull_requests function to retrieve the open pull requests for the specified repository.

Remember that the AI assistant can combine these functions and provide more detailed analysis based on the retrieved information. Feel free to ask more complex questions that might require using multiple GitHub tool functions in combination.