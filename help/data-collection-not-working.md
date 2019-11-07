---
description: >-
  Describes Data Collection not Working, Credentials Expired and the Location Unavailable incidents in detail. Show some common steps to fix these issues.
---

# Data Collection Problems

This category of incidents is related to the operation of SysKit Sense.


## Credentials Expired

The agent installed at a location needs credentials of a user to access SharePoint as that user.  
If the agent is operating normally this incident should never happen, but if i.e. the user's password was changed or the agent was offline for a longer period of time then the _Credentials Expired_ incident will signal that the credentials need to be refreshed.  
To refresh the credentials, you must go to the server where the agent is installed and start SysKit Sense from the Start Menu.

## Location Unavailable

This incident will appear when the agent installed at a location is no longer registered as online.  
The agent has not contacted SysKit Sense for more than the defined amount of time.  
Note that this is different from the _Data Collection not working_ incident since in this case we know for sure that the agent is offline or having connectivity issues. 

## Data Collection not working

This incident can appear when the agent installed at a location stops sending data to SysKit Sense.  
It indicates that the agent may not be working correctly.  

This incident will currently also appear when the agent comes online after a period of inactivity. The period of inactivity is signaled by the _Agent Unavailable_ incident but due to the current implementation the _Data Collection not working_ may appear for a brief period of time when the agent comes back online and the _Agent Unavailable_ incident ends.  
The reason for this is that the incident is active the whole time during the _Agent Unavailable_ incident but is hidden since _Agent Unavailable_ has higher priority. The same goes for the _Credentials Expired_ incident.   
Once the higher priority incident is resolved, the _Data collection not working_ incident will disappear after the agent starts sending data for all the pages monitored.  

This behaviour will possibly change in the future since it can lead to false conclusions.
