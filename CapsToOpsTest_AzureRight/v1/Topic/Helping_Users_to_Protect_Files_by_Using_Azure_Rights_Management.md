---
description: na
keywords: na
pagetitle: Helping Users to Protect Files by Using Azure Rights Management
search: na
ms.date: 2015-09-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 58f9a6ff-4121-4c8c-9865-1bb290604ad2
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# Helping Users to Protect Files by Using Azure Rights Management
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>After you have deployed and configured Azure Rights Management (Azure RMS) for your organization, provide help and guidance for users, administrators, and your help desk:</para>
    <list class="bullet">
      <listItem>
        <para>
          <legacyBold>End-user information:</legacyBold>
        </para>
        <para>Let users know how and when to protect documents and emails that contain sensitive information. Whenever possible, provide this information for  their existing work flows so that they can incorporate the additional steps to an already-familiar process rather than introducing completely new processes . Be sure to let them know the benefits (and the risks) that are specific to your business, as well as providing guidance for when they should protect files and emails. If you have configured <externalLink><linkText>custom templates</linkText><linkUri>http://technet.microsoft.com/library/dn642472.aspx</linkUri></externalLink>, provide instructions about which one to select if the template name and description is not sufficient for them to choose the correct one.</para>
        <alert class="tip">
          <para>Example videos for end users: </para>
          <list class="bullet"><listItem><para> <externalLink><linkText>Azure RMS user experience</linkText><linkUri>http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-user-experience</linkUri></externalLink></para></listItem><listItem><para> <externalLink><linkText>Azure RMS Document Tracking and Revocation</linkText><linkUri>http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation</linkUri></externalLink></para></listItem></list>
          
        </alert>
      </listItem>
      <listItem>
        <para>
          <legacyBold>Administrator information:</legacyBold>
        </para>
        <para>Some applications automatically apply information protection, by using policies and settings that administrators configure. For these applications, you might need to provide instructions for other administrators who manage these applications and services. For more information, see <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link> and <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36">Configuring Applications for Azure Rights Management</link>.</para>
      </listItem>
      <listItem><para><legacyBold>Help desk information:</legacyBold></para><para>One of the most useful tools for the help desk is the <externalLink><linkText>RMS Analyzer</linkText><linkUri>https://www.microsoft.com/en-us/download/details.aspx?id=46437</linkUri></externalLink>.   Help desk operators can run it with the Azure RMS administrator option, and they can ask users to run it with the Azure RMS user option. This tool can not only help identify problems, but also fix problems that it finds, and if still not fixed, record trace logs.</para><para>If there are legitimate requests to have full rights access to protected documents, for example a request by the legal department or a manager after an employee has left the organization, make sure the help desk has processes to request this by using the Azure RMS <externalLink><linkText>super user feature</linkText><linkUri>https://technet.microsoft.com/en-us/library/mt147272.aspx</linkUri></externalLink>.</para><para>In  addition, these are some of the typical problems that users might report: </para><list class="bullet"><listItem><para><legacyBold>Sign in help:</legacyBold></para><para>Users might be prompted for credentials when Azure RMS needs to authenticate a user and cannot use cached credentials. This will be the user’s work or school account and password that is associated with your Office 365 tenant or Azure Active Directory tenant. It will not be a Microsoft account (formerly Microsoft Live ID) or their personal email account, because these are not currently supported by Azure RMS. Provide users and your help desk with instructions about which account to use when users are prompted for credentials when they use these applications with Azure RMS.</para></listItem><listItem><para><legacyBold>Problems protecting or consuming content:</legacyBold></para><para>Make sure that users have the appropriate instructions for the applications that they use, and are using applications and devices that are supported by Azure RMS. For more information about supported applications and devices, see <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link>.</para><para>If users see an error when trying to protect or consume content, ask them to run the <externalLink><linkText>RMS Analyzer</linkText><linkUri>https://www.microsoft.com/en-us/download/details.aspx?id=46437</linkUri></externalLink> as an Azure RMS user.</para><para>If users report that they can open protected content but don't have the rights that they need, ask them to run the <externalLink><linkText>RMS Analyzer</linkText><linkUri>https://www.microsoft.com/en-us/download/details.aspx?id=46437</linkUri></externalLink> as an Azure RMS user and download and view the templates. This will confirm that they have successfully downloaded the templates and what rights the templates provide. The problem might be that the user is not in the correct group that's configured for the template, or that the template needs reconfiguring for the user.</para></listItem></list></listItem>
      
    </list><para>Use the following sections for application-specific information to help users protect sensitive documents and emails.</para>
  </introduction>
  <section>
    <title>Using information protection with the Rights Management sharing application</title>
    <content>
      <para>The Rights Management (RMS) sharing application is required for users to protect and consume protected content if they use Office 2010, but also recommended for all computers and mobile devices that support Azure RMS.</para>
      <para>In addition to making it easier for users to protect important documents, the RMS sharing application lets users track the documents that they have protected, and if necessary, revoke access to them. </para>
      <para>For instructions to use this application for Windows computers, see the <externalLink><linkText>Rights Management sharing application user guide</linkText><linkUri>http://technet.microsoft.com/library/dn339006.aspx</linkUri></externalLink>.</para>
      <para>For mobile devices, see the <externalLink><linkText>FAQ for Microsoft Rights Management Sharing Application for Mobile Platforms</linkText><linkUri>http://technet.microsoft.com/dn451248</linkUri></externalLink>. </para>
      <alert class="tip">
        <para>For a high-level example scenario with screenshots, see the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Example_SharingApp">Users safely share attachments with mobile users</link> section in the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link> topic.</para>
      </alert>
    </content>
  </section>
  <section>
    <title>Using information protection with Office 365, Office 2016, or Office 2013</title>
    <content>
      <para>If you are using Azure RMS and have not installed the Rights Management sharing application, users will not see the <ui>Share Protected</ui> button on the ribbon or <ui>Protect in-place</ui> from File Explorer that makes it easier for them to protect files. For these users, they must follow instructions similar to these.</para>
      <alert class="tip">
        <para>To find application-specific help and instructions for using information protection with these applications, search for <userInput>IRM</userInput> and the application name and version.</para>
      </alert>
      <procedure>
        <title>To protect a document in Word 2013</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Within Microsoft Word, create a new document.</para>
            </content>
          </step>
          <step>
            <content>
              <para>From the <ui>File</ui> menu, click <ui>Info</ui>, click <ui>Protect Document</ui>, click <ui>Restrict Access</ui>, and then choose a template to quickly apply the appropriate usage rights, or select <ui>Restrict Access</ui> and select the usage rights yourself.</para>
              <alert class="note">
                <para>If this is the first time that you have used Rights Management, you will contact the <token>aad_rightsmanagement_1</token> service and will be prompted for credentials to configure the Office IRM client.</para>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>Save the document.</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>When others open the document, they are first authenticated. If they are not authorized to open the document, the document does not open. If they are authorized to open the document, it opens with the restricted usage rights that were specified for that user. For example, a usage right of View-only does not allow the user to edit or save the document, even if it is first copied to another location. The usage rights are displayed at the top of the document by using a restriction banner. The banner might display the permissions that are applied to the document, or it might provide a link to display them.</para>
          </content>
        </conclusion>
      </procedure>
      <procedure>
        <title>To protect an email message using Outlook 2013 and Exchange Online</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Within Outlook, create a new mail message addressed to a recipient within your organization.</para>
            </content>
          </step>
          <step>
            <content>
              <para>From the <ui>OPTIONS</ui> tab,  click <ui>Permission</ui>, and then select an option. For example: <ui>Do Not Forward</ui>, <ui>&lt;Company Name&gt; - Confidential</ui> or <ui>&lt;Company Name&gt; - Confidential View Only</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Send the message.</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>Similarly to viewing a protected document, when the recipients receive the email message, they are first authenticated. If they are authorized to see the email message, it opens with the restricted usage rights that were specified for that user. For example, if you selected <ui>Do Not Forward</ui>, the Forward button on the ribbon is not available.</para>
          </content>
        </conclusion>
      </procedure>
      <procedure>
        <title>To protect an email message using the Outlook Web App</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Within the Outlook Web App, create a new mail message addressed to a recipient within your organization.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click  <ui>…</ui>,  click <ui>set permission</ui>, and then select an option. For example: <ui>Do Not Forward</ui>, <ui>Do Not Reply All</ui>, <ui>&lt;Company Name&gt; - Confidential</ui> or <ui>&lt;Company Name&gt; - Confidential View Only</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Send the message.</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>Similarly to viewing a protected document, when the recipients receive the email message, they are first authenticated. If they are authorized to see the email message, it opens with the restricted usage rights that were specified for that user. For example, if you selected <ui>Do Not Reply All</ui>, the <ui>REPLY ALL</ui> option in the message window is not available.</para>
          </content>
        </conclusion>
      </procedure>
    </content>
    <sections/>
  </section>
  <relatedTopics>
    <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
