# ServiceNow Tool

The ServiceNow tool is a Python module that provides integration with the ServiceNow platform. It allows users to interact with ServiceNow tickets through the ServiceNow API.

# Capabilities

The following capabilities are provided:

* Retrieve details of a specific ServiceNow ticket by its ID.

# Configuration

## Generating ServiceNow API Credentials

To use the ServiceNow tool, you'll need to obtain the following credentials from your ServiceNow instance:

1. ServiceNow Instance URL
2. ServiceNow Username
3. ServiceNow Password

Contact your ServiceNow administrator to obtain these credentials.

## Configuring ServiceNow Tool

Steps:

1. Login to Alexandria as an administrator 
2. Navigate to the tools menu
3. Click on ServiceNow
4. Fill out the following fields:
   * SERVICENOW_INSTANCE_URL = <Your ServiceNow Instance URL>
   * SERVICENOW_USERNAME = <Your ServiceNow Username>
   * SERVICENOW_PASSWORD = <Your ServiceNow Password>

## Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the ServiceNow tool to help answer questions related to IT service management. For example, if a person asks you to:

Question: Can you get the details of ServiceNow ticket INC829430?

You should use the servicenow_create_ticket function to create a new ticket with the appropriate details.
```

This small piece of guidance should be sufficient to activate the ServiceNow functionality.

# Usage

To use this tool, you can start with very simple scenarios and then grow into more complex ones.

## Retrieving ticket details
To retrieve details of an existing ServiceNow ticket, you can use the following function:

servicenow_get_ticket(session, ticket_id)
Example usage:

```
Can you get the details of ServiceNow ticket INC829430?
```

The AI will interpret this as a request to use the ServiceNow tool and retrieve the details of the specified ticket.