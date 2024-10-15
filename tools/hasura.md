# Hasura Tool

The Hasura tool is a Python module that provides integration with the Hasura GraphQL API. It allows users to execute GraphQL queries on the Hasura API and retrieve results.

# Capabilities

The following capabilities are provided:

* Execute GraphQL queries on the Hasura API
* Handle optional variables for GraphQL queries
* Manage authentication and headers for Hasura API requests

# Configuration

## Configuring Hasura Tool

Steps:

1. Login to Alexandria as an administrator 
2. Navigate to the tools menu
3. Click on Hasura GraphQL
4. Fill out the following fields:
   * HASURA_ENDPOINT = <URL to your Hasura GraphQL endpoint>
   * HASURA_SECRET = <Your Hasura admin secret>
   * HASURA_X_USER_ID = <Optional: Hasura user ID>
   * HASURA_X_TOKEN = <Optional: Hasura token>
   * HASURA_ROLE = <Optional: Hasura role>

## Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Hasura tool to help answer questions. For example, if a person asks you to:

Question: Can you execute a GraphQL query to get all users?

You should use the Hasura tool to execute the appropriate GraphQL query.
```

Hasura databases can have dynamic and flexible schemas. Providing sample queries and schema documentation allows the AI to craft the queries. So your strongly encouraged to provide both of this information in the tools section and this will greatly improve your success rate with the tool.

# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones.

## Executing a GraphQL query

```
Can you execute a GraphQL query to get all users?
```

When you ask this, the AI will interpret it as a Hasura request that should use the tool. It will construct an appropriate GraphQL query and submit a request to the Hasura API after authenticating.
