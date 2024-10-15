# What's new in October 20, 2024

Below is a summary of what's new.

## New Capabilities

* Online documentation at https://bravura-security.github.io/alexandria.github.io/
* Zendesk support tickets via support@bravurasecurity.com
* Aha! idea bank at https://alexandria-bravura-security.ideas.aha.io/
* [Azure Devops Tool](/alexandria.github.io/tools/azure-devops)
* Quick links in the header too
  * Submit support ticket
  * Submit idea to the idea bank
  * Access the online documentation

## Enhanced Capabilities

* Expanded salesforce support for all content that can be stored in salesforce
* Expanded search functionality for hubspot
* Attach 250 MB word documents and chat with them
* Attach 250 MB pdf documents and chat with them
* Create books from 250 MB word documents
* Create books from 250 MB pdf documents
* New alexandria assistant that can consult and consume the online documentation
* Improves advanced UI by removing obsolete elements from the UI
* Enhances guards to protect against large payloads by truncating content before sending to the AI model. 
* Explain to people in the UI when content is being truncated and how much.
* Enhances robustnes for when the AI model doesn't return properly formatted json

## Bug fixes

* Disables menu links for items people do not yet have access too
* Fixes formatting display problem with the hasura tool when making graphql queries
* Fixes issues that blocked people from being able to resume a past session from the history
* Fixes the history restoration issue where past chat responses were not being rendered
* Fixes but where attached files couldn't be removed from the UI without starting a new session
