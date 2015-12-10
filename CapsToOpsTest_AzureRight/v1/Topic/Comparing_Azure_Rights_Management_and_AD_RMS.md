---
description: na
search: na
title: Comparing Azure Rights Management and AD RMS
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 2015-10-01
ms.author: e8f708ba3bce4153b61467184c747c7f
capscontentguid: 8123bd62-1814-4d79-b306-e20c1a00e264
---
# Comparing Azure Rights Management and AD RMS
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>If you know or have previously deployed Active Directory Rights Management Services (AD RMS), you might be wondering how <token>aad_rightsmanagement_1</token> (Azure RMS) compares in terms of functionality and requirements. Use the following table for a side-by-side comparison of the features and benefits of Azure RMS and AD RMS. If you have security-specific comparison questions, see the <link xlink:href="8123bd62-1814-4d79-b306-e20c1a00e264#BKMK_CryptographicControls">Cryptographic controls for signing and encryption</link> section in this topic.</para>
    <alert class="note">
      <para>To make this comparison easier, some information here is repeated from <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link>. Use that topic for more specific support and version information for <token>aad_rightsmanagement_1</token>.</para>
    </alert>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>
              <token>aad_rightsmanagement_1</token>
            (Azure RMS)</para>
          </TD>
          <TD>
            <para>Active Directory Rights Management Services (AD RMS)</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>Supports information rights management (IRM) capabilities in Microsoft Online services such as Exchange Online and SharePoint Online, as well as Office 365. </para>
            <para>Also supports on-premises Microsoft server products, such as Exchange Server, SharePoint Server, and file servers that run Windows Server and File Classification Infrastructure (FCI).</para>
          </TD>
          <TD>
            <para>Supports on-premises Microsoft server products such as Exchange Server, SharePoint Server, and file servers that run Windows Server and File Classification Infrastructure (FCI).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Enables implicit trust between organizations and users in any organization. This means that protected content can be shared between users within the same organization or across organizations when users have <token>o365_1</token>, or <token>aad_rightsmanagement_1</token>, or users sign up for RMS for individuals.</para>
          </TD>
          <TD>
            <para>Trusts must be explicitly defined in a direct point-to-point relationship between two organizations by using either trusted user domains (TUDs) or federated trusts that you create by using Active Directory Federation Services (AD FS).</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Provides two default rights policy templates that restrict access of the content to your own organization; one that provides read-only viewing of protected content and another template that provides write or modify permissions for the protected content.</para>
            <para>You can also create your own custom templates, which includes departmental templates that are visible to only a subset of users. For more information, see <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c">Configuring Custom Templates for Azure Rights Management</link>.</para>
            <para>In addition, users can define their own set of permissions if the templates are not sufficient.</para>
          </TD>
          <TD>
            <para>There are no default rights policy templates; you must create and then distribute these. For more information, see <externalLink><linkText>AD RMS Policy Template Considerations</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=154765</linkUri></externalLink>.</para>
            <para>In addition, users can define their own set of permissions if the templates are not sufficient.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Minimum supported version of Microsoft Office is Office 2010, which requires the <externalLink><linkText>RMS sharing application</linkText><linkUri>http://technet.microsoft.com/library/dn339006.aspx</linkUri></externalLink>.</para>
            <para>Microsoft Office for Mac:</para>
            <list class="bullet">
              
              <listItem><para>Microsoft Office for Mac 2016: Supported </para></listItem><listItem>
                <para>Microsoft Office for Mac 2011: Not supported</para>
              </listItem>
            </list>
          </TD>
          <TD>
            <para>Minimum supported version of Microsoft Office is Office 2007.</para>
            <para>Microsoft Office for Mac:</para>
            <list class="bullet">
              
              <listItem><para>Microsoft Office for Mac 2016: Supported </para></listItem><listItem>
                <para>Microsoft Office for Mac 2011: Supported</para>
              </listItem>
            </list>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Supports the <externalLink><linkText>RMS sharing application</linkText><linkUri>https://technet.microsoft.com/library/dn919648(v=ws.10).aspx</linkUri></externalLink> for Windows, Mac computers, and mobile devices.</para>
            <para>In addition, the RMS sharing application supports the following:</para>
            <list class="bullet">
              <listItem>
                <para>Sharing with people in another organization.</para>
              </listItem><listItem>
                <para>Email notification, which lets the sender know when somebody tries to open a protected attachment.</para>
              </listItem>
              <listItem>
                <para>A document tracking site for users, which includes the ability to revoke a document.</para>
              </listItem>
            </list>
          </TD>
          <TD>
            <para>Supports the <externalLink><linkText>RMS sharing application</linkText><linkUri>https://technet.microsoft.com/library/dn919648(v=ws.10).aspx</linkUri></externalLink> for Windows, Mac computers, and mobile devices. However, sharing does not support sharing with people in another organization, email notification, or the document tracking site and the ability for users to revoke documents. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>All file types can be protected with <externalLink><linkText>native or generic protection when you use the RMS sharing application</linkText><linkUri>https://technet.microsoft.com/library/dn339003(v=ws.10).aspx</linkUri></externalLink>.</para>
            <para>For other applications, check the <externalLink><linkText>client capabilities table</linkText><linkUri>https://technet.microsoft.com/library/dn655136.aspx#BKMK_ClientCapabilities</linkUri></externalLink>. </para>
          </TD>
          <TD>
            <para>All file types can be protected with <externalLink><linkText>native or generic protection when you use the RMS sharing application</linkText><linkUri>https://technet.microsoft.com/library/dn339003(v=ws.10).aspx</linkUri></externalLink>.</para>
            <para>For other applications, check the <externalLink><linkText>client capabilities table</linkText><linkUri>https://technet.microsoft.com/library/dn655136.aspx#BKMK_ClientCapabilities</linkUri></externalLink>. </para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Minimum supported version of the Windows client is Windows 7.</para>
          </TD>
          <TD>
            <para>Minimum supported version of the Windows client is Windows Vista Service Pack 2.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Mobile device support includes Windows Phone, Android, iOS, and Windows RT. </para>
            <para>Email support by using Exchange ActiveSync IRM is also supported on all mobile device platforms that support this protocol.</para>
          </TD>
          <TD>
            <para>Mobile device support includes Windows Phone, Android, iOS, and Windows RT, and requires the <externalLink><linkText>Active Directory Rights Management Services Mobile Device Extension</linkText><linkUri>http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341</linkUri></externalLink>.</para>
            <para>Email support by using Exchange ActiveSync IRM is supported on all mobile device platforms that support this protocol.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Supports multi-factor authentication (MFA) for computers and mobile devices. </para>
            
          <para>For more information, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_MFA">Multi-factor authentication (MFA) and Azure RMS</link> section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic.</para></TD>
          <TD>
            <para>Supports smart card authentication if IIS is configured to request certificates.</para>
            
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Supports Cryptographic Mode 2 without additional configuration, which provides stronger security for key lengths and encryption algorithms. </para>
            <para>For more information, see the <link xlink:href="8123bd62-1814-4d79-b306-e20c1a00e264#BKMK_CryptographicControls">Cryptographic controls for signing and encryption</link> section in this topic, and <externalLink><linkText>AD RMS Cryptographic Modes</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=266659</linkUri></externalLink>.</para>
          </TD>
          <TD>
            <para>Supports Cryptographic Mode 1 by default and requires additional configuration to support Cryptographic Mode 2 for stronger security. </para>
            <para>For more information, see the <link xlink:href="8123bd62-1814-4d79-b306-e20c1a00e264#BKMK_CryptographicControls">Cryptographic controls for signing and encryption</link> section in this topic, and <externalLink><linkText>AD RMS Cryptographic Modes</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=266659</linkUri></externalLink>.</para>
          </TD>
        </tr><tr>
          <TD>
            <para>Supports migration from AD RMS and if required, to AD RMS: </para>
            
          <list class="bullet"><listItem><para><link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172">Migrating from AD RMS to Azure Rights Management</link></para></listItem><listItem><para><link xlink:href="0b1c2064-0d01-45ae-a541-cebd7fd762ad">Decommissioning and Deactivating Azure Rights Management</link></para></listItem></list></TD>
          <TD>
            <para>Supports migration from Azure RMS and to Azure RMS: </para><list class="bullet"><listItem><para><link xlink:href="0b1c2064-0d01-45ae-a541-cebd7fd762ad">Decommissioning and Deactivating Azure Rights Management</link></para></listItem><listItem><para><link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172">Migrating from AD RMS to Azure Rights Management</link></para></listItem></list>
          </TD>
        </tr><tr><TD><para>Requires an RMS license to protect content. No RMS license is required to consume content that has been protected by Azure RMS (includes users from another organization). </para><para>For more information, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedSubscriptions">Cloud subscriptions that support Azure RMS</link> section from    <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link>.</para></TD><TD><para>Requires an RMS license to protect content, and to consume  content that has been protected by AD RMS.</para><para>For more information about licensing for AD RMS, see <externalLink><linkText>Client Access Licenses and Management Licenses</linkText><linkUri>https://www.microsoft.com/en-us/Licensing/product-licensing/client-access-license.aspx</linkUri></externalLink> for general information, but contact your Microsoft partner or Microsoft representative for specific information.</para></TD></tr>
      </tbody>
    </table>
  </introduction>
  <section address="BKMK_CryptographicControls">
    <title>Cryptographic controls for signing and encryption</title>
    <content>
      <para>
        <token>aad_rightsmanagement_1</token> always uses RSA 2048 for all public key cryptography and SHA 256 for signing operations. In comparison, AD RMS supports RSA 1024 and RSA 2048, and SHA 1 or SHA 256 for signing operations. </para>
      <para>Both <token>aad_rightsmanagement_1</token> and AD RMS use AES 128 for symmetric encryption.</para>
      <para>
        <token>aad_rightsmanagement_1</token> <?Comment CB: 251978 2014-08-02T16:13:00Z  Id='87?>is compliant with FIPS 140-2 when your tenant key is created and managed by Microsoft (the default), or if you manage your own tenant key (known as BYOK).<?CommentEnd Id='87'
    ?> For more information about managing your tenant key, see <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and Implementing Your Azure Rights Management Tenant Key</link>.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting started with Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
