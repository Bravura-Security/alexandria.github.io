---
title: Tools
nav_order: 6
---

# Tools 

Below is a list of tools that alexandria ships with. Experimental tools are still undergoing testing and validation with customers. 

| Tool | Description | Status |
|------|-------------|--------|
| [Aha!](aha) | Product management via Aha! | Supported |
| [Azure Dev Ops](azure-devops) | Provides git commit, pr, file access, and code search | Experimental |
| [Bing Internet Search](bing) | Provides general internet search capabilities | Supported |
| [Books](books) | Allows searching of books held within alexandria | Supported |
| [Bitbucket](bitbucket) | Provides git commit, pr, file access, and code search | Supported |
| [Bravura Security Fabric](bsf) | Provides identity and access management capabilities | Supported |
| [Confluence](confluence) | Provides access to confluence articles and search | Experimental |
| [DuckDB](duckdb) | Provides advanced excel document interactions | Experimental |
| [Github Cloud](github) | Provides git commit, pr, file access, and code search | Supported | 
| [Grafana](grafana) | Provides access to grafana logs and queries | Experimental |
| [Hasura](hasura) | Provides the ability to run graphql queries against hasura data stores | Supported |
| [Hubspot](hubspot) | Provides the ability to search and interact with content in hubspot | Supported |
| [Jira](jira) | Provides the ability to interact with Jira tickets | Supported |
| [Zendesk](zendesk) | Provides the ability to interact with zendesk tickets and kb articles | Supported |
| [Salesforce](salesforce) | Provides the ability to search and interact with content in salesforce | Supported |
| [ServiceNow](servicenow) | Provides the abiliity to interact with ServiceNow tickets | Experimental |

# Proxy

Some applications we need to interface with are only available on private networks. Our network proxy creates a bridge that allows alexandria to communicate with these on-premesis systems. 

The network proxy is a light weight service that is deployed on a linux virtual machine in your network. It communicates with alexandria over https. Its execution sequence is as follows:

1. The network proxy is installed and started. Its configuration values are stored in environment variables. 
1. The network proxy polls alexandria looking for work to do. 
1. When a user asks a question that needs gitlab files to be returned, an alexandria tool will ask for the proxy to run a command. 
1. When the network proxy polls home looking for work, it will realize alexandria is waiting for a tool to be ran.
1. The network proxy will then run the command and collect output.
1. The network proxy will then return the results to the alexandria server
1. The alexandria server will then consume those results and progress in factoring that information into next steps. 

For steps to deploy the network proxy please see [Proxy](proxy)

| Tool | Description | Status |
|------|-------------|--------|
| [Gitlab](gitlab-on-premesis) | Gitlab version control system | Experimental |

