---
description: na
keywords: na
pagetitle: Terminology for Azure Rights Management
search: na
ms.date: 2015-11-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 742877bf-26f5-40e3-b1f7-8475e7c3ce11
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# Terminology for Azure Rights Management
Confused by a word, phrase, or acronym that’s related to Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS)? Find the definition here for terms and abbreviations that are either specific to Azure RMS or have a specific meaning when used in the context of [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)].

|Term <br /> <br />|Definition <br /> <br />|
|--------|--------------|
|AADRM <br /> <br />|The name of the Windows PowerShell module for Azure Rights Management, which was derived from the unofficial abbreviation for [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] when it was previously named (Windows) Azure Active Directory Rights Management. <br /> <br />|
|activate <br /> <br />|To enable the [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] service so that an organization can add information protection to their documents and email. This action also enables Rights Management features in Exchange Online and SharePoint Online. <br /> <br />|
|Active Directory Rights Management Services <br /> <br />|Frequently abbreviated to *AD RMS*. <br /> <br />A Windows Server role that that provides information protection by using encryption and policy to help secure documents, files, and email. <br /> <br />|
|AD RMS <br /> <br />|See *Active Directory Rights Management Services*. <br /> <br />|
|Azure Rights Management <br /> <br />|Frequently abbreviated to *Azure RMS*. <br /> <br />An Azure service that provides information protection by using encryption and policy to help secure documents, files, and email.  Also known as *Azure Rights Management service*. Previous names have included: <br /> <br /><ul><li>*Windows Azure Active Directory Rights Management*: Frequently abbreviated to Windows Azure AD Rights Management Service. </li><li>*RMS Online*: The original, proposed name, which you might sometimes see in error messages and log file entries. </li> </ul>|
|Azure RMS <br /> <br />|See *Azure Rights Management*. <br /> <br />|
|BYOK <br /> <br />|See *bring your own key*. <br /> <br />|
|bring your own key <br /> <br />|Frequently abbreviated to *BYOK*. <br /> <br />A configuration option chosen by an organization that wants to generate and manage their own tenant key for [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. <br /> <br />|
|content key <br /> <br />|A unique key that is created by RMS-enlightened applications for each document or email that is protected by using [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] and that helps to limit the risk of information disclosure. <br /> <br />|
|consume <br /> <br />|To unlock a file to read or use it when that file has been protected by [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. <br /> <br />|
|deactivate <br /> <br />|To disable the Rights Management service so that the organization can no longer use [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. <br /> <br />|
|departmental template <br /> <br />|A rights policy template that you create (a custom template) and is configured to be visible for selected users rather than all users in your organization. <br /> <br />|
|enlightened applications <br /> <br />|Applications that natively support Rights Management, which includes Office applications, such as Word and Excel. Independent software vendors (ISVs) and developers can also write applications that natively support [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. <br /> <br />|
|enterprise rights management <br /> <br />|An industry-standard, generic term that is often used to describe products and solutions that help organizations protect sensitive or valuable information by using a combination of encryption and policy authorization tools. Microsoft Rights Management is an example of an enterprise rights management (ERM) solution. <br /> <br />|
|ERM <br /> <br />|See *enterprise rights management*. <br /> <br />|
|generic protection <br /> <br />|A level of protection that encrypts any file type and prevents unauthorized people from opening the file. After the file is opened, the file is now unencrypted and usable in an application that doesn’t natively support [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. <br /> <br />|
|information protection <br /> <br />|Sometimes abbreviated to *IP*. <br /> <br />An industry-standard, generic term that refers to protecting data and files from unauthorized access, even after the data and files leave the organizational boundaries by using email or document sharing. Microsoft Rights Management is an example of an information protection (IP) solution. <br /> <br />|
|Information Rights Management <br /> <br />|Frequently abbreviated to *IRM*. <br /> <br />A term used in conjunction with Office services, such as Exchange Server, Word, and SharePoint Online, to describe the ability to support Rights Management. <br /> <br />|
|IRM <br /> <br />|See *Information Rights Management*. <br /> <br />|
|MSDRM <br /> <br />|Sometimes seen as references for the RMS client 1.0, which is replaced with the newer RMS client, MSIPC. This older client supports applications that are developed with the RMS SDK 1.0 and supports Office 2010 and Office 2007, Exchange 2010 and Exchange 2013, and SharePoint 2010 and SharePoint 2007. <br /> <br />|
|MSIPC <br /> <br />|Sometimes seen as references for the RMS client 2.0, which replaced the older RMS client, MSDRM. This later client supports applications that are developed with the RMS SDK 2.0 and supports Office 2016 and Office 2013, SharePoint 2013, and the RMS sharing application. <br /> <br />|
|native protection <br /> <br />|A level of protection available in all enlightened applications that prevents unauthorized people from opening a file and that can also enforce more stringent policies, such as read-only, and do not print. In addition, this protection stays with the file, even when the file is forwarded to other people or saved in a public location that others can access. <br /> <br />|
|.pfile <br /> <br />|The file name extension that is appended to all files that Rights Management generically protects. <br /> <br />|
|.ppdf <br /> <br />|The file name extension that Rights Management creates when it automatically creates a PDF copy of a file (Word, Excel, PowerPoint, or PDF) that you share by email, so that the file can be read (but not edited) on all devices. <br /> <br />|
|permissions level <br /> <br />|A logical grouping of usage rights that make it easier for end-users and administrators to choose configuration options that are role-based. For example, Reviewer and Co-Author. <br /> <br />|
|protect <br /> <br />|Apply Rights Management controls to files or email messages by using encryption, identity, and access control policies to help secure your data. <br /> <br />|
|publish <br /> <br />|To protect a file in order to safeguard it from unauthorized access and use. <br /> <br />|
|Rights Management connector <br /> <br />|An outbound proxy relay that you can deploy for on-premises services such as Exchange Server and SharePoint, to protect data by using Azure Rights Management. <br /> <br />|
|Rights Management services <br /> <br />|The generic term that applies to both the cloud version of [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] ([!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]) and the on-premises version of [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] (AD RMS). <br /> <br />|
|Rights Management sharing application <br /> <br />|An optional downloadable application for Windows and most popular mobile devices, which supports safely sharing files in-place and by email. <br /> <br />|
|RMS <br /> <br />|See *Rights Management services*. <br /> <br />|
|RMS connector <br /> <br />|See *Rights Management connector*. <br /> <br />|
|RMS for individuals <br /> <br />|A free subscription for a user to use [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] when their organization does not have a subscription to Office 365 or Azure Active Directory. <br /> <br />|
|RMS sharing app <br /> <br />|See *Rights Management sharing application*. <br /> <br />|
|super user <br /> <br />|A group of highly trusted administrators who can decrypt and access files that the organization has protected by using Rights Management. Typically, this level of access is required for legal eDiscovery and by auditing teams. <br /> <br />|
|tenant key <br /> <br />|Also known as the server licensor certificate (SLC) key. <br /> <br />The key that is unique to an organization and ultimately secures all [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] cryptographic functions that chain to this tenant key. <br /> <br />|
|unprotect <br /> <br />|Remove Rights Management controls from files or email messages, which used encryption, identity, and access control policies to help secure your data. <br /> <br />|
|use license <br /> <br />|A per-document certificate that is granted to a user who opens a file or email message that has been protected by [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. This certificate contains that user’s rights for the file or email message and the encryption key that was used to encrypt the content, as well as additional access restrictions defined in the document’s policy. <br /> <br />|

## See Also
[Getting Started with Azure Rights Management](../Topic/Getting_Started_with_Azure_Rights_Management.md)

