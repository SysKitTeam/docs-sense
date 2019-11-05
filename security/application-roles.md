---
description: >-
  Describes the application roles used by SysKit Sense, what they mean and how to set them up.
---
# Application roles in SysKit Sense

SysKit Sense have integrated Role-Based access control (RBAC). It leverages the Application Roles feature of Azure Active Directory Applications. SysKit Sense ships with the following Application Roles:
- **Viewer** - Reserved for future usage
- **Administrator** - Users with this Application Role assigned can activate license, add sites to monitor and configure settings
- **Agent Operator** - Users with this Application Role assigned can register agents with SysKit Sense


# Assigning Application Roles

Users have to use the Azure Portal to assign the Application Roles. The steps to assign the Application Roles are:
1. Navigate to [Azure Portal](https://portal.azure.com)
2. Navigate to **Azure Active Directory**
3. Navigate to **Enterprise Applications** (located in the left navigation menu)
4. In the **Application Type** dropdown, select **All Applications** option. In the search bar, search for *SysKit Sense*. Select the *SysKit Sense* application.
5. Navigate to **Users and Groups** (located in the left navigation menu)
6. Click on **Add User** button and follow the wizard to assign roles to users.
>**Note** User assigning roles have to be **Configuration Owner** of the SysKit Sense Active Directory Application.

>**NOTE** If you add additional Application Roles to user, user have to log out and once more log in into application for the new Roles to be applied.