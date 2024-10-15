# Bing Search Tool

The Bing Search tool is a Python module that provides integration with Microsoft's Bing search engine. It allows users to perform web searches and retrieve detailed information from search results using the Bing Search API.

## Capabilities

The following capabilities are provided:

* Performs a Bing search based on a user-provided query.
* Retrieves search results including titles, URLs, and snippets.
* Downloads and analyzes the content of search result web pages.
* Extracts text content from HTML pages for further analysis.

## Configuration

### Obtaining Bing Search API Subscription Key

To use the Bing Search tool, you need to obtain a Bing Search API v7 subscription key:

1. Go to the [Azure Portal](https://portal.azure.com/).
2. Create a new Bing Search v7 resource or use an existing one.
3. Navigate to the "Keys and Endpoint" section of your Bing Search resource.
4. Copy the subscription key and endpoint URL.

### Configuring Bing Search Tool

Steps:

1. Login to Alexandria as an administrator.
2. Navigate to the tools menu.
3. Click on "Bing Search".
4. Fill out the following fields:
   * BING_SEARCH_V7_SUBSCRIPTION_KEY = <Your Bing Search API Subscription Key>
   * BING_SEARCH_V7_ENDPOINT = <Your Bing Search API Endpoint URL>


## Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant may not use the tool by default. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Bing Search tool to help answer questions. For example, if a person asks you to:

Question: Can you search for information about artificial intelligence?

You should use the Bing Search tool to perform a web search and provide relevant information.
```

This small piece of guidance should be sufficient to activate the Bing Search functionality.

## Usage

To use this tool, you can start with simple scenarios and then grow into more complex ones:

### Basic Search
```
Can you search for the latest news about renewable energy?
```

When you ask this, the AI will interpret it as a Bing search request. It will use the tool to perform a web search, retrieve the results, and provide a summary of the findings.

### Detailed Analysis
```
Please search for information about climate change and analyze the top 5 results in detail.
```

For this request, the AI will not only perform the search but also download and analyze the content of the top search results, providing a more in-depth summary of the information found.
