# HubSpot Tool

The HubSpot tool is a Python module that provides integration with the HubSpot CRM platform. It allows users to interact with various HubSpot resources such as contacts, companies, deals, campaigns, and more through the HubSpot API.

# Capabilities

The following capabilities are provided:

* Search and retrieve HubSpot objects of any supported type (e.g., deals, contacts, companies, tickets, products, tasks, notes, etc.).
* Retrieve details of a specific HubSpot object.
* Retrieve details of a specific contact.
* Retrieve details of a specific company.
* Retrieve performance metrics for a specific campaign.
* Retrieve details of a specific deal pipeline.
* List HubSpot users and their access levels.
* Retrieve user access logs.

# Configuration

## Generating HubSpot API Token

Follow these steps to generate a HubSpot API Key:

* Log in to your HubSpot account.
* Navigate to Settings > Integrations > API Key.
* Click "Create API Key" if you don't have one already.
* Copy the generated API Key.
* Configuring HubSpot Tool

## Steps:

* Login to Alexandria as an administrator
* Navigate to the tools menu
* Click on HubSpot
* Fill out the following field:
    * HUBSPOT_API_KEY =


# Informing assistants to use the tool

While the tool is generically available to all assistants, sometimes an assistant will feel like it shouldn't use the tool. If you want to ensure the assistant reliably invokes the tool, you should add the following to the "Tools" tab of the assistant:

```
You are encouraged to use the HubSpot tool to help answer questions. For example, if a person asks you to:

Question: Can you summarize who our most engaged contacts are at XYZ?

You should use search the hubspot api for contacts from customer XYZ and express who appears the most engaged.
```

This small piece of guidance should be sufficient to activate most of the HubSpot functionality.


# Usage
To use this tool, you can start with very simple scenarios and then grow into more complex ones.

## Searching for HubSpot objects

```
Can you search for contacts in HubSpot with the last name "Smith"?
```
When you ask this, the AI will interpret it as a HubSpot request that should use the tool. It will use the hubspot_search function with the appropriate parameters to search for contacts with the last name "Smith".

## Retrieving specific object details

```
Can you get the details customer XYZ in HubSpot?
```

The AI will use the hubspot_get_company_details function to retrieve the details of the specified company.

## Listing HubSpot users

```
Can you list the HubSpot users and their access levels?
```

The AI will use the hubspot_list_users function to retrieve a list of HubSpot users and their access levels.