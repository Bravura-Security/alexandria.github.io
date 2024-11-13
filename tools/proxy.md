---
title: Proxy
parent: Tools
---

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

# Configuring the Proxy

Request access to the proxy from support@bravurasecurity.com and the .tar.gz file that contains the proxy elements will be provided as well as credentials needed for the proxy to authenticate to the alexandria server. 

To install the proxy you need 

1. Copy the provided .tar.gz package to the linux vm or server.
1. Unzip the package.

```
tar -xvzf alexandria_proxy-0.1.0.tar.gz
```

1. Navigate to the unzipped directory.
1. Run the following command:

```
pip install .
```

1. Create .env file with the following values

```
PROXY_UUID=<provided by support@bravurasecurity.com>
PROXY_TOKEN=<provided by support@bravurasecurity.com>
ALEXANDRIA_API_BASE_URL=https://alexandria-app.bc.test.bravurasecurityfabric.com/
VERIFY_SSL=True
LOG_LEVEL=INFO
PROXY_RECIPIENT=proxy
```

1. Run the proxy


