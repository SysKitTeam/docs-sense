---
description: >-
  Describes the Office 365 Slowdown incident and how SysKit Sense detects it.
  Describes some steps users can take to fix the situation.
---

# Office 365 Slowdown

Office 365 Slowdown is an icident that is raised for a location when SysKit Sense determines that there is an issue with the Microsoft servers. 
It does so based on the SharePoint Request Duration (**SPRequestDuration**) and SharePoint Health Score (**X-SharePointHealthScore**) metrics collected by the installed agent.
These metrics are actually headers sent back from SharePoint Online in the HTTP response.


**SPRequestDuration** - the time in milliseconds that it took to process the request on the server. Fundamentally, this is the end-to-end processing time of the SharePoint page in the Microsoft environment. Note that page customizations like navigation and expensive web parts can impact this time.
**X-SharePointHealthScore** - an indication of how heavily loaded SharePoint Online was at the time the page was being served. The values range from 0 to 10. A score of zero represents a low load and a high ability to process requests, whereas a score of ten suggests a problem with the tenant and that the server is throttling requests. Naturally, we hope this value is as close to zero as possible.

If both of the metric values are above a certain threshold an incident is raised. You can alter the threshold value for raising this incident in **Settings -> Thresholds**.  

As mentioned before, a high **SPRequestDuration** can be the result of things like navigation and expensive web parts. A consistent high SPRequestDuration is more indicative with problems on the page than problems in SharePoint Online. As such, you should set the threshold so that it fits the need of your environmnent. You can [tune](https://docs.microsoft.com/en-us/office365/enterprise/tune-sharepoint-online-performance) the page performance to bring the baseline values down.
Once a baseline has been determined and an appropriate threshold set we can conclude that there is something going on in Office 365 if the values go above the thresholds.

The resolution of the problem is outside the scope of SysKit Sense. If a SysKit Sense incident was raised and you find that the performance is indeed degraded you will need to open a case with Office 365 Support. 
Before you open a case with Office 365 Support, make sure that the performance degradation is not because of possible page customizations in the near past that would cause **SPRequestDuration** to go up. 


