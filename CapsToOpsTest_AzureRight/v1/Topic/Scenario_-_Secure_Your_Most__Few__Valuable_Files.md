---
description: na
search: na
title: Scenario - Secure Your Most (Few) Valuable Files
ms.service: na
ms.tgt_pltfrm: na
ms.topic: article
ms.date: na
ms.author: e8f708ba3bce4153b61467184c747c7f
capscontentguid: 95f1844a-612c-4e67-bbe6-4b6b92295221
---
# Scenario - Secure Your Most (Few) Valuable Files
This scenario and supporting user documentation uses Azure Rights Management to manually and custom-protect a handful of files that you have identified as being your most valuable, which warrant the highest level of protection from unauthorized access. These are usually files that only a few people should be able to access. For example, recipe instructions for your company's signature food product, or takeover plans that must not be public before a specified date.

The instructions are suitable for the following set of circumstances:

- You have identified the small set of files to protect .

- The files are in one of the Office file formats that support Rights Management. If the files are in other file formats (for example, CAD files) ensure that these formats support Azure RMS and that you deploy applications that natively support Azure RMS. For more information, see [How Applications Support Azure Rights Management](https://technet.microsoft.com/library/jj585004.aspx).

- The files contain highly confidential, sensitive information that should be accessible to only a few people.

- Requiring an Internet connection to authorize each individual access to a file is an acceptable tradeoff for these people, because it provides higher security.

- These people  do not have a requirement to further share this information with others, but they can modify the information and save their changes.

- The administrator must be able to track who is accessing the files and when, and revoke access if necessary.

## Deployment Instructions
![](../Image/AzRMS_AdminBanner.png)

Make sure that the following requirements are in place, and then follow the instructions for the supporting procedures before going on to the user documentation.

## Requirements for this Scenario
For this scenario, the following must be in place:

|Check <br /> <br />|Requirement <br /> <br />|If you need more information <br /> <br />|
|---------|---------------|--------------------------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|You have prepared accounts and groups for Office 365 or Azure Active Directory: <br /> <br /><ul><li>A mail-enabled group named **Privileged access**, which contains the few people who should have access to these highly confidential  documents </li><li>A mail-enabled group named **IT Compliance managers**, which contains people whose job includes eDiscovery, monitoring and auditing </li><li>A mail-enabled group named **RMS administrators**, and all administrators that will configure Azure RMS are members of this group </li> </ul>|[Preparing for Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|Azure Rights Management is activated <br /> <br />|[Activating Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|You have configured a custom template as described next <br /> <br />|[Configuring Custom Templates for Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|The Rights Management sharing application is deployed to your Windows computer, so that you can protect these files in-place, as described in the next section <br /> <br />|[Download and install the Rights Management sharing application](https://technet.microsoft.com/library/dn574734%28v=ws.10%29.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|Authorized users have a minimum version of Office 2013 <br /> <br />|If users have Office 2010, they must also install the Rights Management sharing application. <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|Your Azure RMS subscription includes document tracking <br /> <br />|If your subscription for Azure RMS does not include document tracking and revocation, you  will not be able to use the document tracking site to see who is accessing these document and revoke access if necessary. In this case, either purchase a subscription that does support document tracking, or accept this limitation. You might also consider the [usage logging](https://technet.microsoft.com/library/dn529121.aspx) capabilities of Azure RMS, which can provide  information such as who accessed each file and when, to help you detect potential suspicious behavior. <br /> <br />To check your subscription support: [Comparison of Rights Management Services (RMS) Offerings](https://technet.microsoft.com/dn858608) <br /> <br />|

#### To configure the custom template

1. In the Azure  portal: Create a new custom template for Azure Rights Management, which contains these values and settings:

   - Name: **Privileged access**

   - Rights:  Grant the **Privileged access** mail-enabled group **Co-author** rights

   - Scope:  Select the **Privileged access** mail-enabled group,  the **IT Compliance managers** mail-enabled group, and the **RMS administrators** mail-enabled group.

   - Offline access: **Content is available only with an Internet connection**

2. Publish the new template.

#### To protect the files in-place

1. In File Explorer, navigate to the first folder that contains the files to protect:

   - If you will protect all the files in the folder, select the folder.

   - If you will protect only some files in the folder, multi-select the files to protect.

2. Right-click, select **Protect with RMS**, and then select **Protect in-place**.

3. Select **Privileged access**.

4. You might be prompted for credentials. Wait for the files to be protected and then click **Close** when you see **the files have been protected** page.

5. If you have more files to protect in other folders, repeat steps 1 through 4 for each folder.

For more information about protecting files in-place, see [Protect a file on a device (protect in-place) by using the Rights Management sharing application](https://technet.microsoft.com/library/dn574733%28v=ws.10%29.aspx)

> [!TIP]
> If the number of files to protect are too many for this manual process, consider using the [RMS Protection tool](https://www.microsoft.com/en-us/download/details.aspx?id=47256) to bulk-protect the files with the template.

#### To monitor and if necessary, revoke access to the files

1. In File Explorer, right-click the protected file, select  **Protect with RMS**, and then select **Track Usage**.

2. If prompted, sign in to access the document tracking site.

3. Check who has accessed the file and the other files that you protected, paying particular attention to failed attempts in case they indicate suspicious behavior. If deemed appropriate, you can revoke access to each file.

## User Documentation Instructions
There are no specific instructions to give to users for this scenario because these files require no special action from users. The files have been protected by you and will be monitored by you. However, you might need to inform these users and your support channels  which files are protected and how this can restrict use of the documents. For example, if an authorized user doesn't have an Internet connection, she will not be able to open the file.

Using the following template, copy and paste the announcement into a communication for your end users, and make these modifications:

1. Supply either the actual names of the files or use a clear reference that the authorized users will understand.

2. Replace *&lt;contact details&gt;* with instructions for how these users can contact the help desk or IT department  with an escalated support channel that matches the importance of these documents.  For example, provide a 24-hour telephone number for high severity support calls.

3. Make any additional modifications that you want to the announcement, and then send it to these users.

The example documentation shows how this announcement might look for users, after your customizations.

![](../Image/AzRMS_UsersBanner.png)

### IT Announcement: Protecting &lt;organization name&gt;'s top secret documents
The following files now have a very high level of protection applied to them, so that only &lt;restricted users&gt; can access and change these files. To help safeguard them from unauthorized access, your application will automatically request authorization each time you open these files so you must now have an Internet connection to  them and you might be prompted for your credentials:

- &lt;top secret document, type or location 1&gt;

- &lt;top secret document, type or location 2&gt;

- &lt;top secret document, type or location  3&gt;

**Need help?**

- If you cannot access these files or if you notice suspicious changes in the files &lt;action and contact details&gt;.

#### Example Customized User Documentation
![](../Image/AzRMS_ExampleBanner.png)

##### IT Announcement: Protecting VanArsdel's top secret documents
The following files now have a very high level of protection applied to them, so that only the people on the To line  of this email message can access and change these files. To help safeguard them from unauthorized access, your applications will automatically request authorization each time you open these files so you must now have an Internet connection to   open them and you might be prompted for your credentials:

- Design specifications for code name "Mercury"

- Design specifications for code name "Jupiter"

- Design specifications for code name "Saturn"

- Design specifications for code name "Neptune"

**Need help?**

- If you cannot access these files or if you notice suspicious changes in the files, call the 24-hour support escalation line that has been sent to you in a protected email message from the IT Department.

