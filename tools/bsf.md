---
title: Bravura Security Fabric
parent: Tools
---

# Bravura Security Fabric Tool

The Bravura Security Fabric (BSF) tool is a Python module that provides integration with the Bravura Security Fabric Identity API. It allows users to interact with various BSF Identity resources such as user accounts, roles, workflow requests, and more through the BSF Identity API.


# Capabilities

The following capabilities are provided:

* Get user accounts for a specific user
* Get user details, attributes, accounts, groups, and roles by ID
* Unlock user accounts
* Disable user profiles or associated accounts
* Clear multi-factor authentication factors for a user
* Enable user profiles or associated accounts
* Get roles that a user is a member of
* Resecure user accounts
* Synchronize passwords for a user's accounts
* Request roles for a user
* Request just-in-time access for a user
* Find workflow requests based on specified criteria
* Retrieve workflow request details
* Execute SQL queries against an ODBC data source
* Retrieve resource information
* List supported resource types


# Configuration

## Generating BSF Identity API Token

To generate an API token for the Bravura Security Fabric Identity API, follow these steps:

* Log in to your BSF Identity tenant as an administrator
* Navigate to the API configuration section
* Generate a new API key with the necessary permissions

## Configuring BSF Identity Tool

Steps:

* Login to Alexandria as an administrator
* Navigate to the tools menu
* Click on Bravura Security Fabric
* Fill out the following fields:
    * BSF_INSTANCE_URL =
    * BSF_USERNAME =
    * BSF_PASSWORD =


# Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Bravura Security Fabric tool to help answer questions. For example, if a person asks you to:

Question: Can you get the account information for user BILLIG?

You should use the bsf_idapi_user_accounts_get function to retrieve the account information.
```

This small piece of guidance should be sufficient to activate most of the BSF Identity functionality.

# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones:

## Asking questions about user accounts

```
Can you get the account information for user BILLIG?
```

When you ask this, the AI will interpret it as a BSF Identity request that should use the tool. It will use the bsf_idapi_user_accounts_get function to retrieve the account information for the specified user.

## Retrieving user details

```
Can you provide me with detailed information about user BILLIG, including their attributes, accounts, groups, and roles?
```

The AI will use the bsf_idapi_user_get_by_id function to retrieve comprehensive information about the specified user.

## Managing user accounts

```
Can you unlock all accounts for user BILLIG?
```

The AI will use the bsf_idapi_user_accounts_unlock function to unlock the specified user's accounts.

## Working with workflow requests

```
Can you find all pending workflow requests created in the last 24 hours?
```

The AI will use the bsf_idapi_find_workflow_requests function with appropriate criteria to search for recent pending workflow requests.