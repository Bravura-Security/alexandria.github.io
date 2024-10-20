---
title: Grafana
parent: Tools
---

# Grafana Tool

The Grafana tool is a Python module that provides integration with the Grafana monitoring and visualization platform. It allows users to interact with Grafana datasources and execute queries through the Grafana API.

# Capabilities

The following capabilities are provided:

* Search for datasources registered in Grafana.
* Query a specific datasource in Grafana.


# Configuration

## Generating Grafana API Token

To use the Grafana tool, you need to generate an API key in your Grafana instance:

1. Log in to your Grafana instance as an administrator.
1. Go to Configuration > API Keys.
1. Click "Add API key".
1. Give your key a name, select the role (e.g., "Admin" for full access), and set an expiration if desired.
1. Click "Add" to generate the key.
1. Copy the generated API key immediately, as you won't be able to see it again.

## Configuring Grafana Tool

Steps:

1. Login to Alexandria as an administrator
1. Navigate to the tools menu
1. Click on Grafana
1. Fill out the following fields:
    * GRAFANA_API_KEY =
    * GRAFANA_API_URL = <URL to your Grafana instance, e.g., https://your-grafana-instance.com>


# Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the Grafana tool to help answer questions. For example, if a person asks you to:

Question: Can you list all the datasources in our Grafana instance?

You should use the grafana_search_datasources function to retrieve the list of datasources.

Question: Can you query the Prometheus datasource with ID 1 for CPU usage?

You should use the grafana_query_datasource function with the appropriate datasource ID and query.
```

This small piece of guidance should be sufficient to activate most of the Grafana functionality.

# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones:

## Searching for Grafana datasources

```
Can you list all the datasources registered in our Grafana instance?
```

When you ask this, the AI will interpret it as a Grafana request that should use the tool. It will call the grafana_search_datasources function to retrieve the list of datasources.

## Querying a specific Grafana datasource

```
Can you query the Prometheus datasource with ID 1 for CPU usage over the last hour?
```

When you ask this, the AI will use the grafana_query_datasource function, providing the datasource ID (1) and an appropriate query for CPU usage.