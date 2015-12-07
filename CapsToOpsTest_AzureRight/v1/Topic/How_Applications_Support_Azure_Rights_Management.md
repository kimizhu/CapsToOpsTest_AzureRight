<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the following information to help you understand how your end-user applications (such as the Office applications, Word, Excel, PowerPoint, and Outlook) and services (such as Exchange and SharePoint) can use Microsoft <token>aad_rightsmanagement_1</token> to help protect your organization’s data:</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9#BKMK_SharingAppIntro">RMS sharing application for Windows and mobile platforms</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9#BKMK_OfficeAppsIntro">Office applications: Word, Excel, PowerPoint, Outlook</link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9#BKMK_ExchangeIntro">Exchange Online and Exchange Server</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9#BKMK_SharePointIntro">SharePoint Online and SharePoint Server</link>
            </para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9#BKMK_FCIIntro">File servers that run Windows Server and use File Classification Infrastructure (FCI)</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9#BKMK_APIAppsIntro">Other applications that support the RMS APIs</link>
        </para>
      </listItem>
    </list>
    <alert class="note">
      <para>To verify the applications and versions that <token>aad_rightsmanagement_1</token> (Azure RMS) supports, see <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link>.</para>
    </alert>
    <para>In some cases, information protection is automatically applied, according to policies that you configure. For example, this is the case with SharePoint libraries, classified files, and Exchange transport rules. In other cases, users must apply information protection themselves from their applications, either by selecting a template or by selecting specific options. For example, this is the case when users share a file by email, or protect a file in-place by restricting access or usage to selected users or to users outside the organization. </para>
    <para>Templates make it easier for users (and administrators who configure policies) to apply the correct level of protection and restrict access to people inside your organization. Although <token>aad_rightsmanagement_1</token> comes with two default templates, you will probably want to create custom templates to reduce the times when they have to specify individual options. For more information, see <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c">Configuring Custom Templates for Azure Rights Management</link>.</para>
    <para>For the cases where users must apply information protection themselves, be sure to provide them with instructions and guidance how and when to do this. The instructions should be specific for the application and versions that they use and how they use them, and the guidance for when and how to apply information protection should be appropriate for your business. For more information, see <link xlink:href="58f9a6ff-4121-4c8c-9865-1bb290604ad2">Instruct Users How to Protect Files by using Azure Rights Management</link>.</para>
    <para>For information about how to configure these applications for Azure RMS, see <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36">Configuring Applications for Azure Rights Management</link>.</para><alert class="tip">
      <para>For examples and screenshots of applications using Azure RMS, see the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_RMSpictures">Azure RMS in action: What administrators and users see</link> section from the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link> topic.</para>
    </alert>
  </introduction>
  <section address="BKMK_SharingAppIntro">
    <title>RMS sharing application for Windows and mobile platforms</title>
    <content>
      <para>The RMS sharing application is a free, downloadable application that is required to support Office 2010, but also recommended for Windows computers, Mac computers, and mobile devices. One of its benefits is that it can apply generic protection for applications and files that do not natively support <token>aad_rightsmanagement_2</token>, which means that all files can be protected. For more information about the different protection levels, see the <externalLink><linkText>Level of protection – native and generic</linkText><linkUri>http://technet.microsoft.com/library/dn339003.aspx#BKMK_LevelsofProtection</linkUri></externalLink> section from the <externalLink><linkText>Rights Management sharing application administrator guide</linkText><linkUri>http://technet.microsoft.com/library/dn339003.aspx</linkUri></externalLink>.</para>
      <para>When users protect their files by using the RMS sharing application, they can also track the documents that they protected, and if necessary, revoke access to them. They do this by using the <externalLink><linkText>document tracking site</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=529562</linkUri></externalLink>.</para>
      <para>For Windows computers, the RMS sharing application unobtrusively integrates with and enhances the  applications that users already use: </para>
      <list class="bullet">
        <listItem>
          <para>An Office add-in for Word, Excel, PowerPoint, and Outlook is installed. This provides users with a <ui>Share Protected</ui> button on the ribbon, which invokes an easy-to-use dialog box of settings that are most commonly used to protect files to be emailed. This button also provides a quick way to access the document tracking site.</para>
        </listItem>
        <listItem>
          <para>A new right-click option for File Explorer. This provides users with a <ui>Protect in-place</ui> option, which invokes an easy-to-use dialog box of settings that are most commonly used to protect files stored on a disk. </para>
        </listItem>
        <listItem>
          <para>A viewer to open files that have been protected by <token>aad_rightsmanagement_2</token>. This viewer is automatically invoked when there is no other application installed that could open the protected file.</para>
        </listItem>
        <listItem>
          <para>Backend configuration for Office 2010 that lets Word, Excel, PowerPoint, and Outlook from this suite work seamlessly with <token>aad_rightsmanagement_1</token>.</para>
        </listItem>
      </list>
      <para>Although the RMS sharing application for Windows can be downloaded and installed for a single computer by using the <externalLink><linkText>Microsoft Rights Management page</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=303970</linkUri></externalLink>, it also supports an enterprise deployment for silent installation and custom configuration. For more information, see the following resources:</para>
      <list class="bullet">
        <listItem>
          <para>
            <externalLink>
              <linkText>Rights Management sharing application administrator guide</linkText>
              <linkUri>http://technet.microsoft.com/library/dn339003.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Rights Management sharing application user guide</linkText>
              <linkUri>http://technet.microsoft.com/library/dn339006.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
      </list>
      <para>The RMS sharing application for mobile devices supports the most commonly used mobile devices, such as iPad and iPhone, Android, Windows Phone, and Windows RT. Users can download this app from the relevant store, and there are links to these from the <externalLink><linkText>Microsoft Rights Management page</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=303970</linkUri></externalLink>. <?xm-deletion_mark author="" time="20150617T153122-0800" data="Or, if you manage mobile devices by using Microsoft Intune, you can deploy the RMS sharing app to devices that run iOS and Android, as a policy managed app. For more information about deploying the RMS sharing app by using Intune, see &lt;maml:externalLink xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;&lt;maml:linkText&gt;Control apps using mobile application management policies with Microsoft Intune&lt;/maml:linkText&gt;&lt;maml:linkUri&gt;https://technet.microsoft.com/library/dn878026.aspx&lt;/maml:linkUri&gt;&lt;/maml:externalLink&gt; in the Microsoft Intune TechNet library."?></para>
    </content>
  </section>
  <section address="BKMK_OfficeAppsIntro">
    <title>Office applications: Word, Excel, PowerPoint, Outlook</title>
    <content>
      <para>These applications natively support Rights Management by using information rights management (IRM) and let users apply protection to a saved document or to an email message to be sent. Users can apply templates or choose very customized settings for access, rights, and usage restrictions. For example, users can configure a file so that it can be accessed only by people in your organization, or control whether the file can be edited, or restricted to read-only, or prevent it from being printed. For time-sensitive files, an expiration time can be configured (directly by users or by applying a template) for when the file can no longer be accessed. For Outlook, users can also choose the <ui>Do Not Forward</ui> option to help prevent data leakage.</para>
    </content>
    <sections>
      <section address="BKMK_ExchangeIntro">
        <title>Exchange Online and Exchange Server</title>
        <content>
          <para>When you use Exchange Online or Exchange Server, you can use information rights management (IRM) integration, which provides additional information protection solutions:</para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyBold>Exchange ActiveSync IRM</legacyBold> so that mobile devices can protect and consume protected email messages.</para>
            </listItem>
            <listItem>
              <para>RMS support for the <legacyBold>Outlook Web App</legacyBold>, implemented similarly to the Outlook client, so that users can protect email messages by templates or by specifying individual options, and users can read and use protected email messages that are sent to them.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Protection rules</legacyBold> for Outlook clients that an administrator configures to automatically apply RMS templates to email messages for specified recipients. For example, when internal emails are sent to your legal department, they can only be read by members of the legal department and cannot be forwarded. Users see the protection applied to the email message before sending it, and by default, they can remove it if they decide it is not necessary. Emails are encrypted before they are sent. For more information, see <externalLink><linkText>Outlook Protection Rules</linkText><linkUri>http://technet.microsoft.com/library/dd638178(v=exchg.150).aspx</linkUri></externalLink> and <externalLink><linkText>Create an Outlook Protection Rule</linkText><linkUri>http://technet.microsoft.com/library/dd638196(v=exchg.150).aspx</linkUri></externalLink> in the Exchange library.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Transport rules</legacyBold> that an administrator configures to automatically apply RMS templates to email messages based on properties such as sender, recipient, message subject, and content. These are similar in concept to protection rules but do not let users remove the protection, can be applied to Outlook Web Access and emails sent by mobile devices, and do not encrypt email messages before they are sent from the client. For more information, see <externalLink><linkText>Create a Transport Protection Rule</linkText><linkUri>http://technet.microsoft.com/library/dd302432.aspx</linkUri></externalLink> in the Exchange library.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Data loss prevention (DLP) policies</legacyBold> that contain sets of conditions to filter email messages, and take actions to help prevent data loss for confidential or sensitive content (for example, personal information or credit card information). Policy Tips can be used when sensitive data is detected, to alert users that they might need to apply information protection, based on the information in the email message. For more information, see <externalLink><linkText>Data Loss Prevention</linkText><linkUri>http://technet.microsoft.com/library/jj150527(v=exchg.150).aspx</linkUri></externalLink> in the Exchange library.</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Office 365 Message Encryption</legacyBold> that uses transport rules to send encrypted emails to people outside your company, and the email is read in a browser with an interface similar to the Outlook Web App. You can customize the disclaimer text and header text in your company’s encrypted emails, and even add your company logo. For more information, see <externalLink><linkText>Office 365 Message Encryption</linkText><linkUri>http://office.microsoft.com/o365-message-encryption-FX104179182.aspx</linkUri></externalLink> from the Office website.</para>
            </listItem>
          </list>
          <para>If you use Exchange Server, you can use the information protection features with <token>aad_rightsmanagement_1</token> by deploying the RMS connector, which acts as a relay between your on-premises servers and the RMS cloud service. For more information, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066">Deploying the Azure Rights Management Connector</link>.</para>
        </content>
      </section>
      <section address="BKMK_SharePointIntro">
        <title>SharePoint Online and SharePoint Server</title>
        <content>
          <para>When you use SharePoint Online or SharePoint Server, you can use information rights management (IRM) integration, which lets administrators protect lists or libraries so that when a user checks-out a document, the file is protected so that only authorized people can view and use the file according to the information protection policies that you specify. For example, the file might be read-only, disable the copying of text, prevent saving a local copy, and prevent printing the file.</para>
          <para>For lists and libraries,  information protection is always applied by an administrator, never an end user. And it is applied at the list or library level for all documents in that container, rather than on individual files.  If you use SharePoint Online, users can also apply IRM to their OneDrive for Business library.</para>
          <para>The IRM service must first be enabled for SharePoint. Then, you specify Information Rights Management for a library. In the case of SharePoint Online and OneDrive for Business, users can also specify Information Rights Management for their OneDrive for Business library. SharePoint does not use rights policy templates, although there are SharePoint configuration settings that you can select that closely match the settings that you can specify in templates. </para>
          <para>If you use SharePoint Server, you can use the information protection features with <token>aad_rightsmanagement_1</token> by deploying the RMS connector, which acts as a relay between your on-premises servers and the RMS cloud service. For more information, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066">Deploying the Azure Rights Management Connector</link>.</para>
        <alert class="note">
 <para>Currently, there are some limitations when you use IRM with SharePoint:</para>
<list class="bullet"><listItem><para>You cannot use the default or custom templates that you manage in the Azure classic portal.</para></listItem><listItem><para>Files that have a .PPDF file name extension for protected PDF files are not supported. Files that have .PDF file name extension and that have been natively protected by RMS are supported when you use a PDF reader that natively supports RMS.</para></listItem><listItem><para> Because Office on mobile devices does not yet support RMS, these devices must use a browser to view files that have been protected with RMS, and the files are read-only.</para></listItem></list></alert><para>Azure RMS applies usage restrictions and data encryption for documents when they are downloaded from SharePoint, and not when the document is first created in SharePoint or uploaded to the library. For information about how documents are protected before they are downloaded, see <externalLink><linkText>Data Encryption in OneDrive for Business and SharePoint Online</linkText><linkUri>https://technet.microsoft.com/library/dn905447.aspx</linkUri></externalLink> from the SharePoint documentation. </para><para>For more information about using Azure RMS with SharePoint, see the following  post from the Office blog: <externalLink><linkText>What’s New with Information Rights Management in SharePoint and SharePoint Online</linkText><linkUri>http://blogs.office.com/2012/11/09/whats-new-with-information-rights-management-in-sharepoint-and-sharepoint-online/</linkUri></externalLink></para></content>
      </section>
    </sections>
  </section>
  <section address="BKMK_FCIIntro">
    <title>File servers that run Windows Server and use File Classification Infrastructure (FCI)</title>
    <content>
      <para>When you configure Windows Server to use File Classification Infrastructure, this File Server Resource Manager feature can scan local files and determine whether they contain sensitive data. For files that meet this criteria, they are tagged with classification properties that an administrator defines. The File Classification Infrastructure can then take automatic action, according to the classification. One of these actions include applying information protection by using <token>aad_rightsmanagement_1</token> and the deployment of the Rights Management connector (also known as the RMS connector). Office files are then automatically protected by Azure RMS. </para>
      <para>To protect all file types, you would not use the RMS connector, but instead, run a Windows PowerShell script, using cmdlets from the <externalLink><linkText>RMS Protection tool</linkText><linkUri>https://www.microsoft.com/en-us/download/details.aspx?id=47256</linkUri></externalLink>. </para><para>The classification policies are fully configurable and highly extensible so that you can prevent potential data leakage from unauthorized and authorized users. It can even help to reduce the risk of data leakage by network administrators because you can configure policies that don’t require these administrators to have access to the files.</para>
      <para>For instructions to deploy and configure the RMS connector for Office files, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066">Deploying the Azure Rights Management Connector</link>.</para>
    <para>For instructions to use the Windows PowerShell script for all file types, see <link xlink:href="9aa693db-9727-4284-9f64-867681e114c9">RMS Protection with Windows Server File Classification Infrastructure (FCI)</link>.</para></content>
  </section>
  <section address="BKMK_APIAppsIntro">
    <title>Other applications that support the RMS APIs</title>
    <content>
      <para>By using the RMS SDK, your internal developers can write line-of-business applications to natively support <token>aad_rightsmanagement_1</token>. How information protection is integrated with these applications depends on how they are written. For example, the integration might be automatically applied with minimal user interaction required, or for a more customized experience, users might be prompted to configure settings to apply information protection to files. For more information about <?Comment CB: Updated link per Gagan 2014-04-23T09:27:00Z  Id='0?>the SDK<?CommentEnd Id='0'
    ?>, see the <externalLink><linkText>Microsoft Rights Management SDK</linkText><linkUri>http://msdn.microsoft.com/library/hh552972(v=vs.85).aspx</linkUri></externalLink>. </para>
      <para>Similarly, many software vendors provide applications to provide  information protection solutions, also known as enterprise rights management (ERM) products. A popular example is a PDF reader that supports <token>aad_rightsmanagement_2</token> for specific platforms. You can use the table in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_ClientCapabilities">Client device capabilities</link> section of the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic to identify applications that support RMS (RMS-enlightened applications), and then use a web search to purchase or download the application. </para>
      <alert class="tip">
        <para>For newly released applications, check the RMS community channels, listed in <link xlink:href="7cc73d92-27d6-49ff-a8ab-2fae73519b4b">Information and Support for Azure Rights Management</link>.</para>
      </alert>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting started with Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
