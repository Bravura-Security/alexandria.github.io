---
title: Aha!
parent: Tools
---

# Aha! Tool

The Aha tool is a Python module that provides integration with the Aha! product management platform. It allows users to interact with various Aha! resources such as products, ideas, epics, features, initiatives, goals, and more through the Aha! API.

# Capabilities

The following capabilities are provided

* Lists ideas for a specific product with various optional filters.
* Lists competitors for a specific product with an optional search term.
* Lists all strategic models
* Lists initiatives with optional filters.
* Lists all goals.
* Lists all strategic visions.
* Lists products with an optional updated_since filter.
* Lists epics with optional filters.
* Lists personas for a specific product.
* Lists pages (or notes/documents) for a specific product with an optional search term.
* Retrieves a specific page and its parent pages recursively.
* Retrieves details of a specific competitor.
* Retrieves details of a specific strategic model.
* Retrieves details of a specific goal.
* Retrieves details of a specific strategic vision.
* Retrieves details of a specific product.
* Retrieves details of a specific epic.
* Retrieves details of a specific feature.
* Retrieves details of a specific idea.
* Retrieves details of a specific persona.
* Retrieves details of a specific initiative.

# Configuration

## Generating Aha! API Token

Follow the steps in [OAuth2 Authentication for API Access](https://www.aha.io/api/oauth2) and generate an API Key

You can access the appropriate area in the aha tenant as per the attached screenshot

## Configuring Aha! Tool

Steps

1. Login to Alexandria as an administrator 
1. Navigate to the tools menu
1. Click on Aha!
1. Fill out the following fields
  * AHA_API_KEY = <API Key>
  * AHA_API_URL = <url to aha tenant>

## Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool you should add the following to the "Tools" tab of the assistant

```
You are encouraged to use the Aha! to help answer questions. For example, if a person asks you too

Question: can you summarize https://bravura-security.aha.io/pages/COMPANY-N-586

You should retrieve the note with the id of COMPANY-N-586
```

This small piece of guidance should be sufficient to activate most of the Aha functionality.


# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex

## Asking questions by url

```
Can you summarize https://bravura-security.aha.io/pages/COMPANY-N-586
```

When you ask this, the AI will interpret it as an aha request that should use the tool. It will extract the id from the url and then submit a request to retrieve the content after authenticating. 