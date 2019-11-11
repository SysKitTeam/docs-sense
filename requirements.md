# Requirements

SysKit Sense is a cloud native solution that leverages several of Azure resources. Most notably Azure Kubernetes Services, Azure Storage, Azure CosmosDb. The resources are provisioned automatically during the [deployment](https://github.com/SysKitTeam/docs-sense/tree/c1996a12ec0e63b0a079f6c3da1790205a180774/installation-and-configuration/deployment.md) process and there is no need to manually prepare the resources.

In order to prepare for the SysKit Sense [deployment](https://github.com/SysKitTeam/docs-sense/tree/c1996a12ec0e63b0a079f6c3da1790205a180774/installation-and-configuration/deployment.md), the following requirements need to be met:

## Have the required resource providers registered in the Azure subscription

The deployment script will try to register the required resource providers automatically, but if the user deploying SysKit Sense is not a subscription Owner/Contributor this step will fail and manual registration is required. More information about registering the resource providers is available [here](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-manager-supported-services).

Required resource providers:

* Microsoft.Resources 
* Microsoft.Authorization 
* Microsoft.ManagedIdentity 
* Microsoft.ContainerService 
* Microsoft.ServiceBus 
* Microsoft.DocumentDB 
* Microsoft.Network 
* Microsoft.Compute 
* Microsoft.Insights 
* Microsoft.KeyVault 
* Microsoft.Storage 

## Ownership of a resource group in the Azure Subscription

By default, the resources required by SysKit Sense will be deployed to a resource group named **syskit-sense**. If the resource group does not exist, it will be created during the deployment process. A different resource group can be chosen by modifying the deployment parameters. We recommend an empty resource group for SysKit Sense deployments only. The user account performing the deployment must be an owner of the resource group for the deployment to succeed. More info about RBAC in Azure can be found [here](https://docs.microsoft.com/en-us/azure/role-based-access-control/role-assignments-portal).

## Permissions to register an application with the Azure AD tenant

The user account performing the deployment must have sufficient permissions to register an application with the Azure AD tenant and assign the application to a role in your Azure subscription.

How to Check these Azure AD permissions?

* go to [Azure Portal](https://portal.azure.com/)
* Select Azure Active Directory.  
* Note your role  

If you have the User role, you must make sure that non-administrators can register applications.

* Select User settings  

Check the App registrations setting. This value can only be set by an administrator. If set to Yes, any user in the Azure AD tenant can register an app.  
If the app registrations setting is set to No, only users with an administrator role may register these types of applications. See available roles and role permissions to learn about available administrator roles and the specific permissions in Azure AD that are given to each role. If your account is assigned to the User role, but the app registration setting is limited to admin users, ask your administrator to either assign you to one of the administrator roles that can create and manage all aspects of app registrations, or to enable users to register apps.

\*\*Source: \([https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal\#required-permissions](https://docs.microsoft.com/en-us/azure/active-directory/develop/howto-create-service-principal-portal#required-permissions)\)

