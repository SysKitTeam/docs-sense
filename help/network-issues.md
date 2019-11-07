---
description: >-
  Describes the Network incident in details and possibles causes. Also describes some common best practices
  in setting up network for accessing Office 365.
---

**Network issues** is an incident that is raised for a location when SysKit Sense determines that the network is behaving poorly loading sites from that location.
It does so based on the **Time Spent In Network** metric collected by the installed agent. 

SharePoint Online includes its own headers in the HTTP response, some of which provide great insight about the page processing and the network travel of our page request.  
The **Time Spent in Network** metric is based on the values of the **SpIisLatency** and **SpRequestDuration** header values.

- **SPIisLatency** - the time in milliseconds taken by the front-end web server after the request has been received by that server, but before the web application begins to process the request. This value should be around 0 or 1, or very close to those figures.
- **SPRequestDuration** - the time in milliseconds that it took to process the request on the server. Fundamentally, this is the end-to-end processing time for the SharePoint page. Healthy pages have a value of around 200 ms, and a range of 100–500 ms, so if it’s greater than that, you may experience some issues. If this value is high, the next metric will be high as well.

The Time Spent in Network Metric is defined as:
> ServerResponseTime = [Response time for the first request on page]  
> NetworkTime = ServerResponseTime - (SpIisLatency + SpRequestDuration)

If this value is above a certain threshold an incident is raised. You can alter the threshold value for raising this incident in **Settings -> Thresholds -> Time Spent in Network**.  

There are various reasons for network issues in an environment, and the resolution of the problem is outside the scope of SysKit Sense since it can be impacted by the monitored environment itself, your ISP or the Microsoft network.  
Depending on the fact whether the issue is persistent and that there are no active incidents related to networking reported by Microsoft there is a higher probability that the issues are with the ISP or inside your network than within the Microsoft network. 

The following Microsoft article is a good starting point if you are not already familiar with the basic concepts when dealing with Office 365 networking:  
>[https://docs.microsoft.com/en-us/office365/enterprise/office-365-networking-overview](https://docs.microsoft.com/en-us/office365/enterprise/office-365-networking-overview)

As stated in the article:
>The ultimate goal of Office 365 networking is to optimize the end user experience by enabling the least restrictive access between clients and the closest Office 365 endpoints.  

This means that for optimal performance you must shorten the network path to Office 365 entry points, bypass any firewalls and provide local direct egress to Office 365.

>[https://docs.microsoft.com/en-us/office365/enterprise/office-365-network-connectivity-principles](https://docs.microsoft.com/en-us/office365/enterprise/office-365-network-connectivity-principles)