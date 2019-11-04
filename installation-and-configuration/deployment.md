---
description: >-
  Describes the deployment process.
---
Instructions
============

Before SysKit Sense can be deployed to an Azure environment a couple of prerequisites are required.  
Once the required prerequisites are gather, the expected deployment time to Azure is around **30 minutes**.  

1\. Tools
---------

This deployment guide uses [Azure CLI](https://docs.microsoft.com/en-us/cli/azure) and [Azure PowerShell](https://docs.microsoft.com/en-us/powershell/azure/overview). Please install and use the latest versions.  
The Azure CLI and Azure PowerShell are used for creating the required service principals that are to be used by the deployment, and also to configure the application once it has been deployed.  
The commands from this deployment guide are meant to be used from a regular PowerShell window and not in PowerShell ISE.

1.  [Install](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli?view=azure-cli-latest) Azure CLI
2.  [Install](https://docs.microsoft.com/en-us/powershell/azure/install-az-ps) Azure PowerShell  
    The installation is very simple and comes down to running the following command in an elevated PowerShell session (Run as Administrator).
    
    > Install-Module -Name Az -AllowClobber
    
    If you don't have access to administrator privileges, you can install for the current user by adding the -Scope argument.
    
    > Install-Module -Name Az -AllowClobber -Scope CurrentUser
    

Before running any commands in the Azure PowerShell or Azure CLI you will need to be logged in for both Azure PowerShell and Azure CLI.  
  
Please **restart any open command line or PowerShell windows** for az commands to be available after the installation.  
  
For Azure CLI:

> az login

For Azure PowerShell:

> Connect-AzAccount

In case of **errors** such as: _Connect-AzAccount : The 'Connect-AzAccount' command was found in the module 'Az.Accounts', but the module could not be loaded. For more information, run 'Import-Module Az.Accounts'._ you will need to set the execution policy to unrestricted as is described [here](https://support.microsoft.com/en-ph/help/2411920/you-can-t-run-scripts-in-azure-active-directory-module-for-windows-pow).  
  
  
If you are working with multiple subscriptions please set the **correct subscription** before running any commands for both Azure PowerShell and Azure CLI.  
For Azure CLI:

> az account set --subscription {SubscriptionId}

For Azure PowerShell:

> Select-AzSubscription -Subscription {SubscriptionId}

You can retrieve the ID of the desired subscription by running the following command

> az account list

You can also view the SubscriptionId in the Azure Portal → Subscriptions page.  
  

2\. Prerequisites
-----------------

1.  An **access token** provided by SysKit.  
    This token is a form of authentication that gives access to the SysKit Sense deployment artifacts.
2.  **Docker credentials** for the SysKit Sense images provided by SysKit.
3.  The **deployment scripts**.

3\. Deployment
--------------

Before continuing and running any commands please check once again that you have selected the **correct subscription** in both Azure CLI and Azure PowerShell.  
This deployment will deploy resources to your Azure Subscription.  

When you deploy this template, Microsoft is able to identify the installation of SysKit Ltd. software with the Azure resources that are deployed. Microsoft is able to correlate the Azure resources that are used to support the software. Microsoft collects this information to provide the best experiences with their products and to operate their business. The data is collected and governed by Microsoft's privacy policies, which can be found at [https://www.microsoft.com/trustcenter](https://www.microsoft.com/trustcenter).

  
  
To deploy SysKit Sense follow these steps:

1.  Unzip the **deployment scripts** to a directory of your choosing. All files will be required for the deployment.
2.  Open a PowerShell session in the directory where the files are extracted.
3.  Run the first time deployment or the upgrade command listed below, depending on the state of your deployment.  
      
    Parameters:
    
    *   Replace **{DockerRegistryUsername}**, **{DockerRegistryPassword}** and **{AccessToken}** with the values provided by Syskit.  
        the AccessToken parameter must be enclosed in quotation marks as in the command below.
    *   Replace **{syskit-sense-yourcompany}** with a valid value for the dns name label. This parameter should uniquely identify your deployment.  
        Will form the default URL where SysKit Sense will be accessible. i.e. **https://{UniqueDnsNameLabel}.{SelectedLocation}.cloudapp.azure.com**  
        Please use lowercase letters with no special characters except -.  
        
    
      
    *   For **first time deployment** run:
        
        >./Deploy-SysKitSense.ps1 -SubscriptionId {SubscriptionId} \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-ResourceGroupName syskit-sense \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-Location {SelectedLocation} \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-UniqueDnsNameLabel {syskit-sense-yourcompany} \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-DockerRegistryUsername {DockerRegistryUsername} \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-DockerRegistryPwd {DockerRegistryPassword} \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-AccessToken "{AccessToken}"
        >                     
        
        The resource group will be automatically created. You can supply an existing resource group if you wish.
    *   For an **upgrade** please run the following command:
        
        >./Deploy-SysKitSense.ps1 -Upgrade \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-OutputsDirectory {DirectoryWithOutputsFromPreviousDeployment}  \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-SubscriptionId {SubscriptionId} \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-DockerRegistryUsername {DockerRegistryUsername} \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-DockerRegistryPwd {DockerRegistryPassword} \`  
        >&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
        >-AccessToken "{AccessToken}"
        >                         
        
4.  Check the generated output files in the directory (the **OutputsDirectory** script parameter). If the **OutputsDirectory** parameter has not been set, the files can be found in the 'outputs' subdirectory of the working directory.  
    Please keep these files as they will be required for future upgrades. The files contain secrets for this deployment. The secrets are encrypted and tied to the current user account.

4\. Additional Configuration
----------------------------

After the deployment succeeds there are some additional steps that need to be taken.

1.  Set the correct SysKit Sense App Registration Redirect URI type.
    *   Go to Azure Portal → Azure Active Directory → App Registrations → SysKit Sense → Authentication.
    *   Use the dropdown in the top section of the page (Redirect URIs) and change the urn://syskit-sense-agent-config/ Redirect URI to be of type Public Client by using the dropdown in the Type column.
2.  To deploy SysKit Sense Agents please add people to the **Agent Operators** application role for the SysKit Sense application.  
    These users will be able to configure agents once installed.
    *   The aplication roles can be assigned in the Azure Portal → Enterprise Applications → SysKit Sense → Users and Groups. Be sure to choose **All Applications** from the Application Type filter when searching for SysKit Sense.
3.  Once everything is configured the application will be accessible from **https://{UniqueDnsNameLabel}.{SelectedLocation}.cloudapp.azure.com**.  
    The actual URL will also be displayed in the output of the **Deploy-SysKitSense.ps1** script.
4.  You can download the agent installation from this [link](../agent/SysKitSenseAgentInstallation.exe). Agent should be installed on server in your On-Premise network.

5\. Deployment Problems
-----------------------

### 5.1. Error AADSTS7000218 while configuring an Agent

Please make sure that you resolved all the potential warnings when executing **Deploy-SysKitSense.ps1**.  
The AADSTS7000218 error occurs when the _urn://syskit-sense-agent-config/_ SysKit Sense redirect URI has not been set to Public client.  
SysKit Sense Agent is a native application and as such the redirect URI must be of the public client type.  
  
To resolve this error please follow the instructions under step 4.5 _Set the correct SysKit Sense App Registration Redirect URI type_.
