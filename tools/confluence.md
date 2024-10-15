# Confluence Tool

The Confluence tool is a Python module that provides integration with Atlassian Confluence, a team collaboration and knowledge management platform. It allows users to search for articles and retrieve specific content from Confluence through the Confluence REST API.

## Capabilities

The following capabilities are provided:

1. **Search for articles in Confluence**
   - Allows users to search for articles using a query string.
   - Returns a list of matching articles with their titles, IDs, types, and URLs.

2. **Retrieve a specific article from Confluence**
   - Allows users to fetch the content of a specific article using its ID.
   - Returns the article's title, ID, URL, and full content.

## Configuration

### Generating Confluence API Token

1. Log in to your Atlassian account.
2. Go to https://id.atlassian.com/manage-profile/security/api-tokens
3. Click "Create API token"
4. Give your token a name (e.g., "Alexandria Integration")
5. Copy the generated token (you won't be able to see it again)

### Configuring Confluence Tool

Steps:

1. Login to Alexandria as an administrator
2. Navigate to the tools menu
3. Click on Confluence
4. Fill out the following fields:
   - CONFLUENCE_USER = Your Confluence username (usually your email)
   - CONFLUENCE_API_TOKEN = The API token you generated
   - CONFLUENCE_URL = Your Confluence instance URL (e.g., https://your-domain.atlassian.net/wiki)

## Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Confluence tool to help answer questions. For example, if a person asks you to:

Question: Can you search Confluence for information about "project management"?

You should use the confluence_search function with the query "project management".

If a person asks:

Question: Can you retrieve the Confluence article with ID 123456?

You should use the confluence_get_article function with the article_id "123456".
```

This small piece of guidance should be sufficient to activate most of the Confluence functionality.

## Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones:

### Searching for articles

```
Can you search Confluence for articles about "agile methodologies"?
```

When you ask this, the AI will interpret it as a Confluence request that should use the tool. It will use the `confluence_search` function with the query "agile methodologies" to search for relevant articles in Confluence.

### Retrieving a specific article

```
Can you retrieve the Confluence article with ID 123456?
```

When you ask this, the AI will use the `confluence_get_article` function to fetch the content of the article with ID 123456 from Confluence.

