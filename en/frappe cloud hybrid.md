## Frappe Cloud Hybrid

This article describes the Hybrid Model of hosting your ERPNext Sites with Frappe Cloud.

FC Hybrid leverages your server, your data ideology by setting up the basic requirements to run an ERPNext Site controlled from FC Dashboard.

We use Ansible Playbooks to setup the server and our In House developed orchestrator called Agent to do site related activities like updates, backups, restores and migrations. Agent is extensively used to control all the 6000+ sites and 50+ Servers currently on Frappe Cloud.

### Difference from FC Servers

The difference of Self Hosted Servers from FC servers is that, one single server which you will be providing will be used as both App and Database Server. Wherein in FC Servers, one s erver handles App and the other is used as the Database Server.

These self hosted servers won’t be in Frappe’s control and it’s maintenace will be completely on the owner of the server.

### Benefits and Features

1.  Control and Security: Frappe Cloud BYOD allows customers to maintain complete control over their infrastructure and data, which is especially important for customers who have strict security requirements or are subject to regulatory compliance.
    
2.  Flexibility: Frappe Cloud BYOD allows customers to scale their infrastructure up or down as needed, without having to worry about capacity constraints or other limitations.
    
3.  All features of Frappe Cloud including
    

*   Offsite Backups
*   Server Monitoring
*   Frappe Cloud Hosting Support
*   Multiple Sites on Same Server
*   Auto Updates on Site

### Server Assumptions

While creating a server from the UI, the system assumes the following

*   The OS is Ubuntu 20
*   `root/sudo` access is given the access to FC
*   There are no other users other than `root` user
*   The default SSH User and SSH Port is `root` and `22` respectively
*   The server is accessible from the Internet
*   A DNS Record with your own domain is pointed to the server

### Architecture

This is a simple architecture diagram of a Self Hosted Server Setup with FC

![](https://frappecloud.com/files/BYOD%20Arch.drawio.png)

> This image assumes there are 3 benches in the server, thus 3 docker containers.

### Request Flows

*   **Agent Requests**(Purple) are directly sent to the server. They are http requests and they execute a site operation and once that is finished, sends out a JSON Response directly back to Frappe Cloud
*   **Site Requests**: Are channeled to the server via Proxy Server. This Proxy server is currently in Mumbai Region and the Traffic is routed to the end server via an Nginx Proxy. These site requests are handled by the Nginx present in the Self Hosted Server and sent to the Docker container with the site.
*   **Exporters**: Collect the monitoring data from the server and notifies the Frappe Cloud team if anything anomalous is happening
*   **Database Requests**: These are direct database calls from the sites.

### Folders and Structure

*   All the Agent related configs will be in an `agent` folder in the frappe user
*   The Benches will be in a `benches` directory under the frappe user. These doesn’t have the complete capabilty of a frappe bench.
*   All the archived benches will be in the `archived` folder
*   The `frappe` user’s UID and GID should be 1000:1000
*   There will be docker containers which are actually the benches and will have complete access to bench commands

![](https://frappecloud.com/files/Screenshot%202023-05-29%20at%202.23.57%20PM.png)

Here is the folder structure inside the `benches` directory

![](https://frappecloud.com/files/Screenshot%202023-05-29%20at%202.25.28%20PM.png)

Accessing Bench commands can only be done from within the container

![](https://frappecloud.com/files/Screenshot%202023-05-29%20at%202.27.16%20PM.png)