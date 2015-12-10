---
description: na
search: na
title: Scenario - Executives Securely Exchange Privileged Information
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 2015-09-01
ms.author: e8f708ba3bce4153b61467184c747c7f
capscontentguid: e18cf5df-859e-4028-8d19-39b0842df33d
---
# Scenario - Executives Securely Exchange Privileged Information
This scenario and supporting user documentation uses Azure Rights Management so that executives can safely exchange emails and attachments by email with one another and  policies automatically restrict access to the executives without requiring special action from them. The emails and any attachments will be automatically protected by Azure Rights Management.

If required, you can add an exception to the rule, such as the abbreviation of DNP (for "Do Not Protect") in the email message subject, so that executives can specify this if they need to send an unprotected email to other executives-for example, to review before forwarding to others.

The instructions are suitable for the following set of circumstances:

- Executives share confidential information with one another that should not be shared with others.

- Executives do not need to do anything different when they send these emails other than send them to a work email address rather than a personal email address.

- Executives have a way to override the rule themselves if they ever need to send an unprotected email message to other executives.

## Deployment Instructions
![](../Image/AzRMS_AdminBanner.png)

Make sure that the following requirements are in place, and then follow the instructions for the supporting procedures before going on to the user documentation.

## Requirements for this Scenario
For the  instructions for this scenario to work, the following must be in place:

|Check <br /> <br />|Requirement <br /> <br />|If you need more information <br /> <br />|
|---------|---------------|--------------------------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|You have prepared accounts and groups for Office 365 or Azure Active Directory: <br /> <br /><ul><li>A mail-enabled group named **Executives**, and all executives are members of this group </li><li>A mail-enabled group named **RMS administrators**, and all administrators that will configure Azure RMS are members of this group </li> </ul>|[Preparing for Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|Your Azure Rights Management tenant key is managed by Microsoft; you are not using BYOK <br /> <br />|[Planning and Implementing Your Azure Rights Management Tenant Key](https://technet.microsoft.com/library/dn440580.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|Azure Rights Management is activated <br /> <br />|[Activating Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|Either: <br /> <br /><ul><li>Exchange Online is enabled for Azure Rights Management </li><li>The RMS connector is installed and configured for Exchange on-premises </li> </ul>|<ul><li>For Exchange Online: Expand the [Exchange Online: IRM Configuration](https://technet.microsoft.com/library/jj585031.aspx#BKMK_ExchangeOnline) section in [Configuring Applications for Azure Rights Management](https://technet.microsoft.com/library/jj585031.aspx). </li><li>For Exchange on-premises: [Deploying the Azure Rights Management Connector](https://technet.microsoft.com/library/dn375964.aspx) </li> </ul>|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|You have configured a custom template as described next <br /> <br />|[Configuring Custom Templates for Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|You have configured a transport protection rule for IRM,  as described later in this article <br /> <br />|<ul><li>For Exchange Online: [Create a Transport Protection Rule](https://technet.microsoft.com/library/dd302432.aspx) </li><li>For Exchange 2013: [Create a Transport Protection Rule](https://technet.microsoft.com/en-us/library/dd302432%28v=exchg.150%29.asp) </li><li>For Exchange 2010: [Create a Transport Protection Rule](https://technet.microsoft.com/en-us/library/dd302432%28v=exchg.141%29.aspx) </li> </ul>|

#### To configure the custom template for executives

1. In the Azure  portal: Create a new custom template for Azure Rights Management, which contains these values and settings:

   - Name: **Executives**

   - Rights:  Grant the **Executives** mail-enabled group **Co-Owner** rights

   - Scope:  Select the **Executives** mail-enabled group, and the **RMS administrators** mail-enabled group.

2. Publish the new template.

3. For Exchange Online only: Refresh the templates by using the Windows PowerShell for Exchange Online command:

   ```
   Import-RMSTrustedPublishingDomain -Name "RMS Online -1 " -RefreshTemplates -RMSOnline
   ```

#### To configure the transport rule for IRM

- Use the Exchange documentation referenced in the table for procedural information to create the transport rule with the following settings:

   - Name:     **Apply the Executives templates to executive emails**

   - Specify the **Executives** group as the sender and recipient of the rule and additional condition.

   - For the action, select **Apply rights protection to the message with** and then select the **Executives** template that you configured.

   - Add the exception of **DNP** (as an abbreviation for "Do Not Protect"), or your choice of words to identify this exception, to be included in the subject.

   - Make sure the rule is configured for **Enforce**.

## User Documentation Instructions
Unless you want to provide instructions of how to specify **DNP** or your choice of exception words or phrases in the email subject,  there are no procedural  instructions to give to users for this scenario because protecting emails from and to executives requires no special action from them. Email messages and any attachments are automatically protected so that only the members of the Executives group can access them.

However, you might need to inform the executives and your help desk  that these emails will be automatically protected and how this can restrict their use of these emails. For example, they cannot successfully be read by other people if the emails or attachments are later forwarded  to others. If you configured the DNP (or equivalent) exception, make sure that the help desk is aware of this configuration so that executives can override the rule themselves, without requiring action from an Exchange administrator.

Using the following template, copy and paste the announcement into a communication for your end users, and make these modifications to reflect your environment:

1. Replace the instances of *&lt;organization name&gt;* with the name of your organization.

2. If you chose a different string from DNP for the exemption, replace that value and the explanation accordingly.

3. Replace *&lt;emaildomain&gt;* with your organization's email domain name.

4. Replace *&lt;contact details&gt;* with instructions for how your users can contact the help desk, such as a website link, email address, or telephone number.

5. Make any additional modifications that you want to the announcement, and then send it to these users.

The example documentation shows how this announcement might look for users, after your customizations.

![](../Image/AzRMS_UsersBanner.png)

### IT Announcement: &lt;Organization name&gt; executive emails are now automatically protected
From now on, whenever you send emails to another &lt;organization name&gt; executive in the company, the contents of the emails and any attachments will be automatically protected such that only another executive in the company can access them to read the information, print it, copy from it, and so on. This restriction applies even if you forward the email message to others, or save the attachments. This protection helps  to prevent data loss of confidential and sensitive information.

Note that if you want others who are not a &lt;organization name&gt; executive to be able to read and edit the information that you send in these emails, you must email it to them separately. Or, to override the automatic protection, type the letters **DNP** (as an abbreviation for Do Not Protect) anywhere in the email message subject.

When sending company-confidential information to another &lt;organization name&gt; executive, please remember to send it to their work email address (*name*@&lt;emaildomain&gt;) and not to a personal email address.

**Need help?**

- Contact the help desk: &lt;contact details&gt;

#### Example User Documentation
![](../Image/AzRMS_ExampleBanner.png)

##### IT Announcement: VanArsdel executive emails are now automatically protected
From now on, whenever you send emails to another VanArsdel executive in the company, the contents of the emails and any attachments will be automatically protected such that only another executive in the company can access them to read the information, print it, copy from it, and so on. This restriction applies even if you forward the email message to others, or save the attachments. This protection helps  to prevent data loss of confidential and sensitive information.

Note that if you want others who are not a VanArsdel executive to be able to read and edit the information that you send in these emails, you must email it to them separately. Or, to override the automatic protection, type the letters **DNP** (as an abbreviation for Do Not Protect) anywhere in the email message subject.

When sending company-confidential information to another VanArsdel executive, please remember to send it to their work email address  (*name*@vanarsdelltd.com) and not to a personal email address.

**Need help?**

- Contact the help desk: helpdesk@vanarsdelltd.com

