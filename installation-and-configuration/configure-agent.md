---
description: >-
  Describes how to setup and configure the Agent application. Describes how to fix credentials expired incident.
---

# Configuring On-Premise Agent

To use SysKit Sense to its full potential, users have to deploy the On-Premise Agents. These agents should be installed on servers inside the network for which users whish to monitor connection to Office 365. Agents are desktop application consisting of Windows Service and configuration interface application. SysKit Sense Agent will ping SharePoint Online sites every 5 minutes. This ensures that SysKit Sense is not overloading the Office 365 while maintaining real-time monitoring of Office 365 environment. 

Configuration of SysKit Sense Agent are done following these steps:
1. Install the SysKit Sense Agent on server located in network for which you whish to test connection to Office 365. 
2. After the SysKit Sense Agent is started, users must give URL of SysKit Sense application. This is the URL on which the SysKit Sense is hosted. 
3. Users have to login using their work account. **Note**: Users have to be assigned to **Agent Operators** role to be able to register agent. To learn how to set up application roles, please consult [this article](../security/application-roles.md).
4. User have to assign the name for the Agent. The default value is FQDN of the server the SysKit Sense is installed on, but we recommend changing it to something more relevant (SysKit Sense will stores on which server it is installed and will show this information).
5. User will be prompted to enter credentials of the account which will access the SharePoint Online sites. The account has to have **Read** permissions on the SharePoint Online sites which are monitored. We recommend to use a dedicated service account for monitoring.