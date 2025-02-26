---
title: Auto attendant and Call queue dialing and voice recognition reference
author: mkbond007
ms.author: mabond
manager: pamgreen
ms.reviewer: colongma
ms.date: 11/22/2024
ms.topic: article
ms.tgt.pltfrm: cloud
ms.service: msteams
search.appverid: MET150
ms.collection: 
  - M365-voice
  - m365initiative-voice
  - tier1
audience: Admin
appliesto:
  - Microsoft Teams
  - Skype for Business
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
  - ms.teamsadmincenter.autoattendants.overview
  - Phone System
  - seo-marvel-apr2020
  - has-azure-ad-ps-ref
  - azure-ad-ref-level-one-done
description: Learn about the Auto attendant and Call queue dialing and voice recognition options in Teams.
---
# Auto attendant and Call queue dialing and voice recognition reference

Dial by Name or Extension is an Auto attendant feature that enables callers to reach Teams users in your organization. Callers can use their voice or phone keypad to say or enter the full or partial name or extension of the person they would like to reach. The Auto attendant searches the company directory, locates the person, and then transfers the caller to them. As an admin, Dial by Name or Dial by Extension are options you set up when you [configure the call flow settings in an Auto attendant](create-a-phone-system-auto-attendant.md?tabs=call-flow).

## Searching for users

Teams users who can be reached by using Dial by Name **aren't required to have a phone number or have Calling Plans assigned to them, but they must be Enterprise Voice enabled for Skype for Business Server users**. For multi-national organizations, Dial by Name finds and transfers callers to Microsoft Teams users who are in different countries or regions.

Teams users who can be reached by using Dial by Extension **aren't required to have a phone number or have Calling Plans assigned to them, but they must be Enterprise Voice enabled for Skype for Business Server users**. You also need to have an appropriately configured dial plan for your users. For multi-national organizations, Dial by Extension finds and transfers callers to Microsoft Teams users who are in different countries or regions. Teams Assigned Phone number, LineURI, isn't supported for Auto attendant Dial by Extension.

Given the prerequisites involved, Dial by Name or Extension must be explicitly enabled when configuring an Auto attendant.

### Maximum directory size

There's no limit on the number of Active Directory users that search can support when a caller searches for a specific person. A caller can enter partial or full names (FirstName + LastName or LastName + FirstName), but they must enter a full extension number.
  
|Input type|Search format|Maximum number of users in an organization|
|:-----|:-----|:-----|
|DTMF (keypad entry) |Partial  <br/> FirstName + LastName  <br/> LastName + FirstName |No limit  |
|Speech (voice input) |FirstName  <br/> LastName  <br/> FirstName + LastName  <br/> LastName + FirstName  | No limit  |

### Search Considerations

Auto attendant search is a part of the main Address Book search of Microsoft. Exchange Address Book settings affect searches performed via the Auto attendant service. For example, if some users in your Address Book settings have the property `-HiddenFromAddressListsEnabled = $true`, then Auto attendant search won't return these users. This is similar to the Address Book search experience in Exchange, Teams, and other products. For more information about hiding users from the Address Book, see [Manage address lists in Exchange Online](/exchange/address-books/address-lists/manage-address-lists#hide-recipients-from-address-lists).

Once the main address book settings are verified, the search then proceeds to apply any configured [Dial Scope](create-a-phone-system-auto-attendant.md?tabs=dial-scope) Include or Exclude lists.

> [!NOTE]
> You can use the [Dial Scope](create-a-phone-system-auto-attendant.md?tabs=dial-scope) feature to narrow down the names that are reachable by changing the scope for a particular Auto attendant.
>
> If more than 5 names remain after any Dial Scope Include or Exclude lists are applied, the search fails and the caller is told that too many names were found.
> 
> It might take up to 24 hours for Active Directory Address Book updates to be reflected in the Auto attendant search results. This timeframe also applies to the addition of new users or the removal of existing ones.

## Dial by Name - Keypad (DTMF) entry

People calling in can use Dial by Name to reach users by specifying either the full or partial name of the person they're trying to reach. There are various formats that can be used when the name is entered.

When people search your organization's directory, they can use the '0' (zero) key to indicate a space between the first name and last name or last name and first name. When they enter a name, they're asked to terminate their keypad entry with the # key. For example, "After you enter the name of the person you're trying to reach, press #." If there are multiple names that are found, the person calling is given a list of names to select from.

People can search for names in your organization using the following search formats on their phone keypad:
  
|Name format|Search type|Example|Search result|
|:-----|:-----|:-----|:-----|
|FirstName + LastName |Full  |Amos0Marble# |Amos Marble |
|LastName + FirstName |Full |Marble0Amos#  |Amos Marble |
|FirstName  |Full   |Amos#   |Press 1 for Amos Marble  <br/> Press 2 for Amos Marcus |
|LastName |Full |Marble#  |Press 1 for Amos Marble  <br/> Press 2 for Mary Marble |
|FirstName or LastName |Partial |Mar# |Press 1 for Mary Marble  <br/> Press 2 for Mary Jones  <br/> Press 3 for Amos Marcus |
|FirsName + LastName |Partial |Amos0Mar# |Press 1 for Amos Marble  <br/> Press 2 for Amos Marcus |
|LastName + FirstName |Partial |Mar0Am# |Press 1 for Amos Marble  <br/> Press 2 for Amos Marcus |

There are several special characters that are used when searching for people using a phone keypad. For example, the person is asked to use the pound key (#), while the zero (0) key is used for a space between names. Pressing the star key (*) repeats the list of matching names to the person.
  
|Special phone keypad character|What it means|
|:-----|:-----|
|#   |End character when entering a name. |
|0   |Space between names. |
|*    |Repeat the list of matching names. |

### Dial by Name - Name recognition with speech

People can search for others in their organization with their voice (speech recognition). They can also reach anyone in Active Directory by saying the full or partial name of the person they're trying to locate. Using voice inputs can recognize names in various formats, including FirstName, LastName, FirstName + LastName, or LastName + FirstName.
  
You can enable speech recognition for an Auto attendant, but phone keypad entry (DTMF) isn't disabled. Phone keypad entry can be used at any time even if speech recognition is enabled on the Auto attendant.
  
As with phone keypad entry, if multiple names are found, the person calling hears a list of names to select from.

Callers can say names in the following formats:
  
|Name with speech|Search type|Example|Search result|
|:-----|:-----|:-----|:-----|
|FirstName + LastName |Full |Amos Marble |Amos Marble |
|LastName + FirstName |Full  |Marble Amos |Amos Marble |
|FirstName |Full |Amos |Press or say 1 for Amos Marble  <br/> Press or say 2 for Amos Jones |
|LastName |Full |Marble |Press or say 1 for Amos Marble  <br/> Press or say 2 for Ben Marble |
|FirstName or LastName |Partial |Mar |Press or say 1 for Mary Marble  <br/> Press or say 2 for Mary Jones  <br/> Press or say 3 for Amos Marcus |
|FirsName + LastName |Partial |Amos Mar |Press or say 1 for Amos Marble  <br/> Press or say 2 for Amos Marcus |

### Dial by Name - Multiple users with the same name

If there are multiple users with the same name, it's possible that a Dial by Name search returns these users. In this case, the default behavior is to say each name followed by the option to select. For example, if the caller searches for `John Smith` and there are three people with that name in the organization, the caller hears:

- For John Smith, press 1.
- For John Smith, press 2.
- For John Smith, press 3.

In these situations, you can extend the information the caller is presented with by configuring the [-UserNameExtension](/powershell/module/teams/new-csautoattendant#-usernameextension) parameter.

The `-UserNameExtension` parameter specifies how to extend the information returned in a Dial by Name search with additional information. Possible values are:

- **None**: The username is pronounced as is. This is the default value.
- **Office**: Adds office information from the user profile.
- **Department**: Adds department information from the user profile.

If `-UserNameExtension` is configured with `Department`, and if the caller searches for `John Smith` when there are three people with that name in the organization, the caller hears:

- For John Smith in accounting, press 1.
- For John Smith in sales, press 2.
- For John Smith in support, press 3.

### Dial by Extension

Users you want to make available for **Dial By Extension** need to have an extension specified as part of one of the following phone attributes defined in Active Directory (and synchronized via Microsoft Entra Connect) or Microsoft Entra ID. For more information, see [Add users individually or in bulk](/microsoft-365/admin/add-users/add-users).

- TelephoneNumber (AD) or BusinessPhone (Microsoft Entra ID)
- Mobile (AD and Microsoft Entra ID)
- HomePhone (AD) - legacy field 
- OtherTelephone (AD) - legacy field 

It's recommended to avoid using the *HomePhone* and *OtherTelephone* fields due to their legacy status. While both fields are currently supported, there might be long-term implications.

The required format to enter the extension in the user phone number field can be one of the following formats:

- *+\<phone number>;ext=\<extension>*
- *+\<phone number>x\<extension>*
- *x\<extension>*

Example 1:

```PowerShell
Update-MgUser -UserId 'usern@domain.com' -MobilePhone '15555555678;ext=5678'
```
Example 2:

```PowerShell
Update-MgUser -UserId 'usern@domain.com' -MobilePhone '+15555555678x5678'
```

Example 3:
```PowerShell
Update-MgUser -UserId 'usern@domain.com' -MobilePhone 'x5678'
```
You can set the extension in the [Microsoft 365 admin center](https://admin.microsoft.com/) or the [Microsoft Entra admin center](https://aad.portal.azure.com). For more information on the Update-MgUser cmdlet, see [Update-MgUser](/powershell/module/microsoft.graph.users/update-mguser).

> [!NOTE]
> If using the TelephoneNumber field to define the extension, Microsoft recommends that you use the format *+\<phone number>;ext=\<extension>*. If the user is also assigned a Teams Phone Number, you should define both numbers the same way.

## Language support

Language support for text-to-speech and speech recognition is available in these [supported languages](create-a-phone-system-auto-attendant-languages.md).

The following voice commands are available for speech recognition:
  
|Voice command| Corresponds to |
|:-----|:-----|
|Yes | Press 1 for Yes. |
|No | Press 2 for No. |
|Repeat |Repeats the list of options. Press * on the keypad to repeat the list of options. |
|Operator | Press 0 for "Operator" |
|Main Menu  |Brings the caller to the main menu of the Auto attendant. |
|Zero | Press 0 (by default, same as "Operator").|
|One | Press 1. |
|Two | Press 2. |
|Three| Press 3.|
|Four | Press 4. |
|Five | Press 5. |
|Six  | Press 6. |
|Seven | Press 7.|
|Eight |Press 8.|
|Nine  |Press 9.|

## Related articles

[Plan for Teams Auto attendants and Call queues](plan-auto-attendant-call-queue.md)

[Getting service phone numbers for Skype for Business and Microsoft Teams](./getting-service-phone-numbers.md)

[Country and region availability for Audio Conferencing and Calling Plans](country-and-region-availability-for-audio-conferencing-and-calling-plans/country-and-region-availability-for-audio-conferencing-and-calling-plans.md)
