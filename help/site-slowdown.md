---
description: >-
  Describes the Site Slowdown incident and what can be done to fix it.
---

# Site Slowdown

**Site slowdown** is an incident that is raised when a specific site is loading poorly on any of the configured locations.  
The load time of the site is measured without any cache in the chrome browser from the server where the SysKit Sense agent is installed.

There are various reasons why a SharePoint Site can be slow, and the resolution of the problem is outside the scope of SysKit Sense.  

If the issue is persistent and not related to networking or Microsoft servers (indicated by other SysKit Sense incidents or Office 365 [service health](https://admin.microsoft.com/AdminPortal/Home#/servicehealth)) then the fault must lie within the SharePoint Site itself. The content on the site, deployed webparts or images, etc. 
Once this is established to be true, we recommend starting with the following Microsoft documentation page:  
https://docs.microsoft.com/en-us/office365/enterprise/tune-sharepoint-online-performance


If you find that the performance of the page is adequate for your needs, you can set the threshold value for raising this incident in **Settings -> Thresholds -> Site Load Time**.

