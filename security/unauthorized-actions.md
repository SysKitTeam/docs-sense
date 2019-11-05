---
description: >-
  Describes the process needed to fix the Unauthorized Actions message users come across 
---

# Unauthorized Actions 

When the user tries to perform the actions that require **Administrator** application role, SysKit Sense will show a dialog warning the user that they do not have appropriate permissions. Learn more about Application Roles in SysKit Sense [here](./application-roles.md).

## Steps to fix the Unauthorized Actions dialog
Users have to use the Azure Portal to assign the Application Roles. The steps to assign the Application Roles are:
1. Navigate to [Azure Portal](https://portal.azure.com)
2. Navigate to **Azure Active Directory**
3. Navigate to **Enterprise Applications** (located in the left navigation menu)
4. In the **Application Type** dropdown, select **All Applications** option. In the search bar, search for *SysKit Sense*. Select the *SysKit Sense* application.
5. Navigate to **Users and Groups** (located in the left navigation menu)
6. Click on **Add User** button and follow the wizard to assign **Administrator** role to required to users.
>**Note** User assigning roles have to be **Configuration Owner** of the SysKit Sense Active Directory Application.

>**NOTE** If you add additional Application Roles to user, user have to log out and once more log in into application for the new Roles to be applied.