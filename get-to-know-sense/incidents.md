---
description: >-
  Describes the Incidents in SysKit Sense, how are they calculated and what can user do about them.
---

# Incidents Overview 

The incidents are central part of the SysKit Sense. SysKit Sense comes with an advanced incident engine which monitors SharePoint Online and the networks where the SysKit Sense Agents are installed. Incident represents issues that are causing users to experience degraded Office 365 and SharePoint performance. When SysKit Sense determines that the incident has started or finished, it will send an email notification.

## Incidents Categories

The incidents in SysKit Sense are divided in three major group: site related, Office 365 related and agent related.

### Site related incidents

1. **Site Slowdown** - SysKit Sense will periodically try to load the SharePoint site in the browser. If the predefined threshold is violated SysKit Sense will report the Site *Site Slowdown* incident. Learn more about this incident [here](../help/site-slowdown.md)
2. **Large Content** - SysKit Sense will analyze your SharePoint Online site and report on the large images, JavaScript files and fonts. Learn more about this incident [here.](../help/large-content-on-site.md)

### Office 365 incidents
1. **Office 365 Slowdown** - SysKit Sense collects the performance data coming from SharePoint Online sites. By analyzing this data SysKit Sense can determine Office 365 performance degradation even when the Microsoft is not acknowledging the issue. Learn more about this incident [here](../help/office-365-slowdown).

### Agent related incidents
1. **Network Issues** - SysKit Sense analyzes how much time is lost in the network during the accessing SharePoint Online. If too much time is spent SysKit Sense will raise an incident. Learn more about this incident [here.](../help/network-issues.md)
2. **Expired Credentials** - SysKit Sense will raise incident when the credentials on SysKit Sense Agent expire. Learn more about this incident [here.](../help/data-collection-not-working.md)
3. **Data Collection not Working** - SysKit Sense will monitor the health of the connected SysKit Sense Agents. If the agent stops sending data to SysKit Sense, an incident will be raised. Learn more about troubleshooting this issue [here.](../help/data-collection-not-working.md)
4. **Location Unavailable** - If the SysKit Sense Agent stops communicating with SysKit Sense, an incident will be raise. Lear more about troubleshooting this issue [here](../help/data-collection-not-working.md)