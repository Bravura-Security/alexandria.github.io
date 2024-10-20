---
title: Bitbucket
parent: Tools
---

# Bitbucket Tool

The Bitbucket tool is a Python module that provides integration with the Bitbucket platform. It allows users to interact with various Bitbucket resources such as repositories, commits, pull requests, and files through the Bitbucket API.

# Capabilities

The following capabilities are provided:

* Retrieve the content of a specific file from a Bitbucket repository.
* Get detailed information about a specific Bitbucket repository.
* List all branches in a specific Bitbucket repository.
* Retrieve the metadata of a specific file from a Bitbucket repository.
* Retrieve commits from a Bitbucket repository with optional filters.
* Retrieve details of a specific commit from a Bitbucket repository.
* Retrieve pull requests from a Bitbucket repository with optional filters.
* Search for code in a specified Bitbucket workspace.

# Configuration

## Generating Bitbucket API Token

To use the Bitbucket tool, you need to generate an API token:

* Log in to your Bitbucket account.
* Go to your account settings.
* Navigate to "App passwords" under "Access Management".
* Click "Create app password".
* Give your app password a name and select the necessary permissions.
* Copy the generated password (you won't be able to see it again).

## Configuring Bitbucket Tool

Steps:

* Login to Alexandria as an administrator
* Navigate to the tools menu
* Click on Bitbucket
* Fill out the following fields:
    * BITBUCKET_API_URL = https://api.bitbucket.org
    * BITBUCKET_API_USER =
    * BITBUCKET_API_PASSWORD =
    * BITBUCKET_WORKSPACE_ID =


# Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Bitbucket tool to help answer questions. For example, if a person asks you to:

Question: Can you retrieve the contents of the file "README.md" from the "example/repo" repository?

You should use the bitbucket_get_file_contents function to retrieve the file contents.
```

This small piece of guidance should be sufficient to activate most of the Bitbucket functionality.


# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones:

## Retrieving file contents

```
Can you get the contents of the file "README.md" from the "example/repo" repository?
```

When you ask this, the AI will interpret it as a Bitbucket request that should use the tool. It will extract the repository and file path from the question and then submit a request to retrieve the content after authenticating.

## Listing repository branches
```
List all branches in the "example/repo" repository.
```

The AI will use the bitbucket_list_branches function to retrieve all branches in the specified repository.

## Searching for code

```
Search for the term "TODO" in the "example" workspace.
```

The AI will use the bitbucket_search_code function to search for the specified term in the given workspace.

## Retrieving commit information

```
Get the details of the commit with hash "abc123" in the "example/repo" repository.
```

The AI will use the bitbucket_get_commit function to retrieve the details of the specified commit.

## Getting pull requests
```
Retrieve the open pull requests for the "example/repo" repository.
```

The AI will use the bitbucket_get_pull_requests function to fetch the open pull requests for the specified repository.