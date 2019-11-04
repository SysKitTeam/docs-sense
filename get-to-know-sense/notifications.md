---
description: >-
    Describes the notifications in SysKit Sense, when are they sent and how can users configure them.
---

# Notifications in SysKit Sense

SysKit Sense comes with the support for notifications sent by e-mail. To setup the notifications users have to navigate to settings page, accessible by clicking **Settings** option on left navigation pane. The notifications are disabled by default, so users have to enable them maunally. The notifications are **sent every time an incident occurs or ends**. To learn more about incidents go to [Incidents article.](./incidents.md)  

On the settings page users can define the email addresses to which they would like to receive notifications. Multiple email addresses can be entered, divided by **;**

Users have two options for choosing the mail server for sending the email notifications:
1. **Exchange Online** - Using this options SysKit Sense will use Exchange Online mail server to send the email notifications. Before the application can use mail server, current user have to give consent to SysKit Sense application to send email on the behalf the currently logged in user.
> Using the Exchange Online options, the received emails will have the sender mail of the user that gave consent.
2.  **SMTP** - Using this options users can use their own mail server for SysKit Sense to use. This option requires more information to setup but users have complete control on setting Sent from and Reply-to email addresses.