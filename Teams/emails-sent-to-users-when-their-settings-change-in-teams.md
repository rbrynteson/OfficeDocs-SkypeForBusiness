---
title: "Emails sent to users when their settings change"
ms.author: wlibebe
author: wlibebe
manager: pamgreen
ms.reviewer: oscarr
ms.date: 02/21/2024
ms.topic: article
ms.assetid: 1b46da6d-f93a-4cc0-9ae8-af765935b007
ms.tgt.pltfrm: cloud
ms.service: msteams
ms.subservice: teams-audio-conferencing
search.appverid: MET150
ms.collection: 
  - M365-collaboration
  - m365initiative-meetings
audience: Admin
appliesto: 
  - Microsoft Teams
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom: 
  - Audio Conferencing
  - seo-marvel-mar2020
description: "Learn about what information is sent automatically to users by email when their dial-in conferencing settings change in Microsoft Teams. "
---

# Emails sent to users when their settings change in Microsoft Teams

Emails are automatically sent to users who are [enabled for Audio Conferencing](set-up-audio-conferencing-in-teams.md) using Microsoft as the audio conferencing provider.

By default, there are four types of email that are sent to your users who are enabled for Audio Conferencing. However, if you want to limit the number of emails sent to users, you can turn it off. Audio Conferencing in Microsoft 365 or Office 365 sends emails to your users when:

- **An Audio Conferencing license is assigned to them or when you are changing the audio conferencing provider to Microsoft.**

     This email includes the conference ID, the default conference phone number for the meetings, the audio conferencing PIN for the user, and the instructions and link to use the Teams Meeting Update Tool. The Teams Meeting Update Tool is used to update existing meetings for the user. See [Assign Microsoft Teams add-on licenses](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

    > [!NOTE]
    > If your organization has been enabled for dynamic conference IDs, all of a user's meetings that they schedule will have unique conference IDs. Check out the [View and reset a conference ID assigned to a user in Microsoft Teams](see-change-and-reset-a-conference-id-assigned-to-a-user-in-teams.md) article for more information.

    Here's an example of this email:

     ![Teams Verify License.](media/teams-emails-sent-to-users-when-settings-change-image1.png)

    To find out more about licensing, see [Microsoft Teams add-on licensing](./teams-add-on-licensing/microsoft-teams-add-on-licensing.md).

- **The conference ID or default conference phone number of a user changes.**

    This email contains the conference ID, default conference phone number, and the instructions and link to use the Teams Meeting Update Tool. The Teams Meeting Update tool is used to update existing meetings for the user. This email doesn't include the user's audio conferencing PIN. See [Reset a conference ID for a user](reset-a-conference-id-for-a-user-in-teams.md).

    Here's an example of this email:

     ![Dial-in conferencing info has changed.](media/teams-emails-sent-to-users-when-settings-change-image2.png)

- **The audio conferencing PIN of a user is reset.**

    This email contains the organizer's audio conferencing PIN, the existing conference ID, and default conference phone number for the user. See [Reset the Audio Conferencing PIN](reset-the-audio-conferencing-pin-in-teams.md).

     Here's an example of this email:

     ![Dial-in conferencing PIN changed.](media/teams-emails-sent-to-users-when-settings-change-image3.png)
  
- **A user's license is removed or when audio conferencing provider changes from Microsoft to other provider or None.**

    This happens when the **Audio Conferencing** license is removed from a user or when setting the audio conferencing provider to **None**.

    See [Assign or remove licenses for Microsoft 365 for business](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

    Here's an example of this email:

     ![Dial-in conferencing is turned off.](media/teams-emails-sent-to-users-when-settings-change-image4.png)

> [!NOTE]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

## Make changes to the email messages that are sent to them

You can make changes to the email that is automatically sent to users. By default, the sender of the emails is from Microsoft 365 or Office 365, but you can change the display name using Windows PowerShell. For more information, see [Microsoft Teams PowerShell reference](/powershell/module/teams) .

## What if you don't want email to be sent to them?

When you disable sending emails to users, emails aren't sent even when a user gets assigned a license. In this case, the conference ID, default conferencing phone number, and, more importantly, their audio conferencing PIN isn't sent to the user. When this happens, you must tell the user by sending them a separate email or by calling them.

By default, emails are sent to your users, but if you want to prevent them from receiving email for audio conferencing, you can use Microsoft Teams or Windows PowerShell.

### Using the Microsoft Teams admin center

1. In the left navigation, go to **Meetings** > **Conference Bridges**.

2. At the top of the **Conference Bridges** page, select **Bridge settings**.

3. In the **Bridge settings** pane, enable or disable **Automatically send emails to users if their dial-in settings change**.

4. Select **Save**.

> [!Note]
> [!INCLUDE [updating-admin-interfaces](includes/updating-admin-interfaces.md)]

### Using Windows PowerShell

You can also use the Microsoft Teams PowerShell module and run:

```PowerShell
Set-CsOnlineDialInConferencingTenantSettings -AutomaticallySendEmailsToUsers $true|$false
```

You can use the [Set-CsOnlineDialInConferencingTenantSettings](/powershell/module/teams/set-csonlinedialinconferencingtenantsettings) to manage other settings for your organization, including email.

For more information, see [Microsoft Teams PowerShell reference](/powershell/module/teams/).

## Want to know more about Windows PowerShell?

By default, the sender of the emails is from Microsoft 365 or Office 365, but you can change the email address and display name using Windows PowerShell.

Windows PowerShell is all about managing users and what users are allowed or not allowed to do. With Windows PowerShell, you can manage Microsoft 365 or Office 365 using a single point of administration that can simplify your daily work when you have multiple tasks to do. To get started with Windows PowerShell, see these topics:

- [Why you need to use Office 365 PowerShell](/microsoft-365/enterprise/why-you-need-to-use-microsoft-365-powershell)

- [Best ways to manage Office 365 with Windows PowerShell](/previous-versions//dn568025(v=technet.10))

For more information about Windows PowerShell, see the [Microsoft Teams PowerShell reference](/powershell/module/teams).

## Related topics

- [Enable or disable sending emails when Audio Conferencing settings change](enable-or-disable-sending-emails-when-their-settings-change-in-teams.md)

= [Send an email to a user with their Audio Conferencing information](send-an-email-to-a-user-with-their-dial-in-information-in-teams.md)
