---
description: na
search: na
title: Frequently Asked Questions for Azure Rights Management
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 2015-11-01
ms.author: e8f708ba3bce4153b61467184c747c7f
capscontentguid: 71ce491f-41c1-4d15-9646-455a6eaa157d
---
# Frequently Asked Questions for Azure Rights Management
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Some frequently asked questions for Microsoft <token>aad_rightsmanagement_1</token>, also known as Azure RMS:</para>
  </introduction>
  <section expanded="false">
    <title>What do I need to deploy Azure RMS and how do I get going?</title>
    <content>
      <para>First, check <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link>, which has information about the cloud subscription options, how you can use your on-premises servers with Azure RMS, which deployment scenarios are not currently supported, which devices and applications support Azure RMS, and a link if you need a list of IP addresses and domain names for firewalls or proxy servers. You might also want to check the other topics in the <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting Started with Azure Rights Management</link> section, to get a basic understanding of how <token>aad_rightsmanagement_1</token> can help protect your organization’s data, how it works with applications, how it compares with the on-premises version of Active Directory Rights Management, and understand the terms and abbreviations that are specific to <token>aad_rightsmanagement_1</token>.</para>
      <para>Then when you’re ready to test Azure RMS for yourself, or deploy it for your organization, use the <link xlink:href="086600c2-c5d8-47ec-a4c0-c782e1797486">Azure Rights Management Deployment Roadmap</link> for a list of steps with links for more information and how-to instructions.</para>
      <para>If you need additional information, resources, and support options, see <link xlink:href="7cc73d92-27d6-49ff-a8ab-2fae73519b4b">Information and Support for Azure Rights Management</link>.</para>
    </content>
  </section>
  <section expanded="false">
    <title>Can I integrate Azure RMS with my on-premises servers?</title>
    <content>
      <para>Yes. Azure RMS can be integrated with your on-premises servers, such as Exchange Server, SharePoint, and Windows file servers. To do this, you use the <externalLink><linkText>Rights Management connector</linkText><linkUri>https://technet.microsoft.com/library/dn375964.aspx</linkUri></externalLink>. Or, if you're just interested in using File Classification Infrastructure (FC) with Windows Server, you can use the <externalLink><linkText>RMS Protection cmdlets</linkText><linkUri>https://technet.microsoft.com/library/mt601315(v=ws.10).aspx</linkUri></externalLink>. You can also synchronize and federate your Active Directory domain controllers with Azure AD for a more seamless authentication experience for users, for example, by using <externalLink><linkText>Azure AD Connect</linkText><linkUri>http://azure.microsoft.com/documentation/articles/active-directory-aadconnect/</linkUri></externalLink>. </para>
      <para>Azure RMS automatically generates and manages XrML certificates as required, so it doesn’t use an on-premises PKI. For more information about how Azure RMS uses certificates, see the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Walthrough">Walkthrough of how Azure RMS works: First use, content protection, content consumption</link> section in the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link> topic.</para>
    </content>
  </section>
  <section expanded="false">
    <title>I have a hybrid deployment of Exchange with some users on Exchange Online and others on Exchange Server—is this supported by Azure RMS?</title>
    <content>
      <para>Absolutely, and the nice thing is, users will be able to seamlessly protect and consume protected emails and attachments across the two Exchange deployments. For this configuration, <externalLink><linkText>activate Azure RMS</linkText><linkUri>https://technet.microsoft.com/library/jj658941.aspx</linkUri></externalLink> and <externalLink><linkText>enable IRM for Exchange Online</linkText><linkUri>https://technet.microsoft.com/library/dn151475(v=exchg.150).aspx</linkUri></externalLink>, then <externalLink><linkText>deploy and configure the RMS connector</linkText><linkUri>https://technet.microsoft.com/library/dn375964.aspx</linkUri></externalLink> for Exchange Server. </para>
      <para></para>
    </content>
  </section><section expanded="false">
    <title>If I deploy Azure RMS in production, is my company then locked into the solution or risk losing access to content that we protected with Azure RMS?</title>
    <content>
      <para>No, you always remain in control of your data and can continue to access it, even if you decide to no longer use Azure RMS. For more information, see <link xlink:href="0b1c2064-0d01-45ae-a541-cebd7fd762ad">Decommissioning and Deactivating Azure Rights Management</link>.</para>
      <para>However, before you decommission your Azure RMS deployment, we would like to hear from you and understand why you made this decision. If Azure RMS does not fulfil your business requirements, check with us in case new functionality is planned for the near-future or if there are alternatives. Send an email message to <externalLink><linkText>AskIPTeam@Microsoft.com</linkText><linkUri>mailto:askipteam@microsoft.com?subject=Planning%20to%20decommission%20Azure%20RMS</linkUri></externalLink> and we’ll be happy to discuss your technical and business requirements.</para>
    </content>
  </section>
  <section expanded="false">
    <title>Can I control which of my users can use Azure RMS to protect content?</title>
    <content>
      <para>Yes, Azure RMS has user onboarding controls for this scenario. For more information, see the <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214#BKMK_OnboardingControls">Configuring onboarding controls for a phased deployment</link> section in the <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214">Activating Azure Rights Management</link> topic.</para>
    </content>
  </section>
  <section expanded="false">
    <title>Can I prevent users from sharing protected documents with specific organizations?</title>
    <content>
      <para>One of the biggest benefits of Azure RMS is that it supports business-to-business collaboration without you having to configure explicit trusts for each partner organization, because Azure AD takes care of the authentication for you.</para>
      <para>There is no administration option to prevent users from securely sharing documents with specific organizations. For example, you want to block an organization that you don’t trust or that has a competing business. Preventing Azure RMS from sending protected documents to users in these organizations wouldn’t make sense because your users would then share their documents unprotected, which is probably the last thing you want to happen in this scenario! For example, you wouldn’t be able to identify who is sharing company-confidential documents with which users in these organizations, which you can do when the document (or email) is protected by Azure RMS.</para>
    </content>
  </section>
  <section expanded="false">
    <title>When I share a protected document with somebody outside my company, how does that user get authenticated?</title>
    <content>
      <para>Azure RMS always uses an Azure Active Directory account and an associated email address for user authentication, which makes business-to-business collaboration seamless for administrators. If the other organization uses Azure services, users will already have accounts in Azure Active Directory, even if these accounts are created and managed on-premises and then synchronized to Azure.  If the organization has Office 365, under the covers, this service also uses Azure Active Directory for the user accounts.  If the user’s organization doesn’t have managed accounts in Azure, users can sign up for <externalLink><linkText>RMS for individuals</linkText><linkUri>https://technet.microsoft.com/library/dn592127.aspx</linkUri></externalLink>, which creates an unmanaged Azure tenant and directory for the organization with an account for the user, so that this user can then be authenticated for Azure RMS.</para>
      
    <para>The authentication method for these accounts can vary, depending on how the administrator in the other organization has configured the Azure Active Directory accounts. For example, they could use passwords that were created for these accounts, multi-factor authentication (MFA), federation, or passwords that were created in Active Directory Domain Services and then synchronized to Azure Active Directory.</para></content>
  </section><section expanded="false">
    <title>Can I add users from outside my company to custom templates?</title>
    <content>
      <para>Yes.  Creating custom templates that end users (and administrators) can select from applications makes it quick and easily for them to apply information protection, using predefined policies that you specify. One of the settings in the template is who is able to access the content, and you can specify users and groups from within your organization, and users from outside your organization.</para>
      
    <para>To specify users from outside your organization, use the <externalLink><linkText>Windows PowerShell module for Azure Rights Management</linkText><linkUri>https://technet.microsoft.com/library/jj585012.aspx</linkUri></externalLink>. You can use either of these options: </para><list class="bullet"><listItem><para><embeddedLabel>Export, edit, and import the updated template</embeddedLabel>:  This is the easiest method if you want to add these external users to an existing template that includes other groups. Use the <externalLink><linkText>Export-AadrmTemplate</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727078.aspx</linkUri></externalLink> cmdlet to export the template to a .XML file that you can edit to add the external email addresses of these users and their rights to the existing groups and rights. Then use the <externalLink><linkText>Import-AadrmTemplate</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727077.aspx</linkUri></externalLink> cmdlet to import this change back into Azure RMS. </para></listItem><listItem><para><embeddedLabel>Use a rights definition object to create or update a template</embeddedLabel>:    Specify the external email addresses and their rights in a rights definition object, which you then use to create or update a template. You specify the rights definition object by using the <externalLink><linkText>New-AadrmRightsDefinition</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727080.aspx</linkUri></externalLink> cmdlet to create a variable and then supply this variable to the  -RightsDefinition parameter with the <externalLink><linkText>Add-AadrmTemplate</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727075.aspx</linkUri></externalLink> cmdlet (for a new template) or <externalLink><linkText>Set-AadrmTemplateProperty</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727076.aspx</linkUri></externalLink> cmdlet (if you're modifying an existing template). However, if you're adding these users to an existing template, you will need to define rights definition objects for the existing groups in the templates and not just the external users.</para></listItem></list><para>For more information about custom templates, see <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c">Configuring Custom Templates for Azure Rights Management</link>.</para></content>
  </section><section expanded="false">
    <title>What devices and which file types are supported by Azure RMS?</title>
    <content>
      <para>For a list of supported devices, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedDevices">Client devices that support Azure RMS</link> section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic. Because not all supported devices can currently support all RMS capabilities, be sure to also check the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_ClientCapabilities">Client device capabilities</link> table in the same topic.</para>
      <para>Azure RMS can support all file types. For text, image, Microsoft Office (Word, Excel, PowerPoint) files, .pdf files, and some other application file types, Azure RMS provides native protection that includes both encryption and enforcement of rights (permissions). For all other applications and file types, generic protection provides file encapsulation and authentication to verify if a user is authorized to open the file.</para>
      <para>For a list of file name extensions that are natively supported by Azure RMS, see the <externalLink><linkText>Supported file types and file name extensions</linkText><linkUri>http://technet.microsoft.com/library/dn339003.aspx</linkUri></externalLink> section of the <externalLink><linkText>Rights Management sharing application administrator guide</linkText><linkUri>http://technet.microsoft.com/library/dn339003.aspx</linkUri></externalLink>. File name extensions not listed are supported by using the RMS sharing application that automatically applies generic protection to these files.</para>
    </content>
  </section>
  <section expanded="false">
    <title>When will you support migration from AD RMS?</title>
    <content>
      <para>Initially, Azure RMS didn’t support migration from an on-premises deployment of Rights Management, such as AD RMS. But it’s supported now.</para>
      <para>For more information, see <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172">Migrating from AD RMS to Azure Rights Management</link>.</para>
    </content>
  </section>
  <section expanded="false">
    <title>We really want to use BYOK with Azure RMS but learned that this isn’t compatible with Exchange Online—what’s your advice?</title>
    <content>
      <para>Don’t let this current limitation delay your Azure RMS deployment. If you have Exchange Online and want to use bring your own key (BYOK), we recommend that you deploy Azure RMS in the default key management mode now, where Microsoft generates and manages your key. That way, you get all the benefits of protecting your important files and emails now, with the option to move to BYOK later (for example, when Exchange Online does support BYOK). </para>
      <para>However, if your company policies require you to use a hardware security module (HSM) and this would otherwise block your Azure RMS deployment, another option is to deploy Azure RMS with BYOK now, with reduced RMS functionality for Exchange. For more information, see the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_Pricing">BYOK pricing and restrictions</link> section in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and Implementing Your Azure Rights Management Tenant Key</link> topic.</para>
    </content>
  </section><section expanded="false">
    <title>A feature I am looking for doesn’t seem to work with SharePoint protected libraries—is support for my feature planned?</title>
    <content>
      <para>Currently, SharePoint supports RMS protected documents by using IRM protected libraries, which do not support custom templates, document tracking, and some other capabilities.  For more information, expand the   <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_SharePointOnline">SharePoint Online and OneDrive for Business: IRM Configuration</link> section in the <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link> topic .</para>
      <para>If you are interested in a specific  capability that isn't yet supported,  be sure to keep an eye on announcements on the <externalLink><linkText>RMS team blog</linkText><linkUri>http://blogs.technet.com/b/rms/</linkUri></externalLink>.</para>
    </content>
  </section><section expanded="false">
    <title>How do I configure One Drive for Business in SharePoint Online, so that users can safely share their files with people inside and outside the company?</title>
    <content>
      <para>By default, as an Office 365 administrator, you don’t configure this; users do. </para>
      
    <para>Just as a SharePoint site administrator enables and configures IRM for a SharePoint library that they own, OneDrive for Business is designed for users to enable and configure IRM for their own OneDrive for Business library.  However, by using PowerShell, you can do this for them. For instructions, expand the <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_SharePointOnline">SharePoint Online and OneDrive for Business: IRM Configuration</link>  section in the <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36">Configuring Applications for Azure Rights Management</link> article.  </para></content>
  </section><section expanded="false">
    <title>Do you have any tips or tricks for a successful RMS deployment?</title>
    <content>
      <para>After overseeing many deployments and listening to our customers, partners, consultants, and support engineers – one of the biggest tips we can pass on from experience: <legacyBold>Design and deploy simple rights policies</legacyBold>.</para>
      <para>Because Azure RMS supports sharing securely with anyone, you can afford to be ambitious with your information protection reach. But be conservative with your rights policies. For many organizations, the biggest business impact comes from preventing data leakage by applying the default rights policy template that restricts access to people in your organization. Of course, you can get much more granular than that if you need to – prevent people from printing, editing etc. But keep the more granular restrictions as the exception for documents that really need high-level security, and don’t implement these more restrictive policies on day one, but plan for a more phased approach.</para>
    </content>
  </section>
  <section expanded="false">
    <title>What features can or can’t be used with the different subscriptions for Azure RMS?</title>
    <content>
      <para>For the paid subscriptions that support Azure RMS (Office 365, Azure RMS Premium, and Enterprise Mobility Suite), there are some differences in the RMS features that are supported. For a list of these, see <externalLink><linkText>Comparison of Rights Management Services (RMS) Offerings</linkText><linkUri>http://technet.microsoft.com/dn858608</linkUri></externalLink>.</para>
      <para>The free subscription that supports Azure RMS (RMS for individuals) supports consuming content that has been protected by Azure RMS. For more information, see <link xlink:href="2efcb440-fefd-45e9-872b-f471573aadf2">RMS for Individuals and Azure Rights Management</link>.</para>
    </content>
  </section>
  <section expanded="false">
    <title>Where can I get technical information about the free Azure RMS subscription (RMS for individuals)—for example, how it really works, how to take control of the accounts, and <?Comment CB: 13986 2014-09-11T14:09:00Z  Id='138?>which domains can’t be used<?CommentEnd Id='138'
    ?>?</title>
    <content>
      <para>You’ll find answers to these questions in the <link xlink:href="2efcb440-fefd-45e9-872b-f471573aadf2">RMS for Individuals and Azure Rights Management</link> topic.</para>
    </content>
  </section>
  <section expanded="false">
    <title>How do we regain access to files that were protected by an employee who has now left the organization?</title>
    <content>
      <para>Use the super user feature of Azure RMS, which lets authorized users have full owner rights for all use licenses that were granted by your organization’s RMS tenant. This same feature lets authorized services index and inspect files, as needed. </para>
      <para>For more information, see <link xlink:href="acb4c00b-d3a9-4d74-94fe-91eeb481f7e3">Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery</link>.</para>
    </content>
  </section>
  <section expanded="false">
    <title>Can Rights Management prevent screen captures?</title>
    <content>
      <para>Rights Management does block screen captures from most of the commonly used screen capture tools, which can help to avoid accidental or negligent disclosure of confidential or sensitive information. However, there are many ways that a user can share data that is displayed on a screen, and taking a screen shot is only one method. For example, a user intent on sharing displayed information can take a picture of it using their camera phone, retype the data, or simply verbally relay it to somebody. </para>
      <para>As these examples demonstrate, technology alone cannot always prevent users from sharing data that they should not. While Rights Management can help to safeguard your important data by using authorization and usage policies, this enterprise rights management solution should be used with other controls. For example, implement physical security, carefully screen and monitor people who have authorized access to your organization's data, and invest in user education so users understand what data should not be shared.</para>
    </content>
  </section><section expanded="false">
    <title>Where can I find supporting information for Azure RMS—such as legal, compliance, and SLAs?</title>
    <content>
      <para>Azure RMS supports other services and also relies on other services. If you’re looking for information that is related to Azure RMS but not about how to use the Azure RMS service, check the following resources: </para>
      <para>
        <embeddedLabel>Legal and privacy:</embeddedLabel>
      </para>
      <list class="bullet">
        <listItem>
          <para>For Microsoft Azure agreement information: <externalLink><linkText>Microsoft Azure Agreement</linkText><linkUri>http://azure.microsoft.com/support/legal/subscription-agreement/</linkUri></externalLink></para>
        </listItem>
        <listItem>
          <para>For Microsoft Azure privacy information: <externalLink><linkText>Microsoft Azure Privacy Statement</linkText><linkUri>http://azure.microsoft.com/support/legal/privacy-statement/</linkUri></externalLink></para>
        </listItem>
      </list>
      <para>
        <embeddedLabel>Security, compliance, and auditing:</embeddedLabel>
      </para>
      <para>See the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_RMScompliance">Security, compliance, and regulatory requirements</link> section in the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link> topic. In addition:</para>
      <list class="bullet">
        <listItem>
          <para>For external certifications for Azure RMS: <externalLink><linkText>Microsoft Azure Trust Center</linkText><linkUri>http://azure.microsoft.com/support/trust-center/</linkUri></externalLink></para>
        </listItem>
        <listItem>
          <para>For FIPS 140 information: <externalLink><linkText>FIPS 140 Validation</linkText><linkUri>https://technet.microsoft.com/library/security/cc750357.aspx</linkUri></externalLink></para>
        </listItem>
      </list>
      <para>
        <embeddedLabel>Service level agreements:</embeddedLabel>
      </para>
      <list class="bullet">
        <listItem>
          <para>Service level agreement for Azure RMS, by selected country: <externalLink><linkText>Service level agreement</linkText><linkUri>http://microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&amp;DocumentTypeId=37</linkUri></externalLink> </para>
        </listItem>
        <listItem>
          <para>Service level agreement for Azure Active Directory: <externalLink><linkText>Service Level Agreements</linkText><linkUri>http://azure.microsoft.com/support/legal/sla/</linkUri></externalLink></para>
        </listItem>
      </list>
      <para>
        <embeddedLabel>Documentation:</embeddedLabel>
      </para>
      <list class="bullet">
        <listItem>
          <para>Azure Active Directory Documentation site: <externalLink><linkText>Azure Active Directory</linkText><linkUri>http://azure.microsoft.com/documentation/services/active-directory/</linkUri></externalLink></para>
        </listItem>
        <listItem>
          <para>Azure Active Directory Library: <externalLink><linkText>Azure Active Directory</linkText><linkUri>http://msdn.microsoft.com/library/azure/jj673460.aspx</linkUri></externalLink></para>
        </listItem>
        <listItem>
          <para>Office 365 Library: <externalLink><linkText>Office 365</linkText><linkUri>http://technet.microsoft.com/library/dn127064(v=office.14).aspx</linkUri></externalLink></para>
        </listItem>
      </list>
    </content>
  </section>
  <section expanded="false">
    <title>What do I do if my question isn’t here?</title>
    <content>
      
      
      <para>Use the links and resources listed in <link xlink:href="7cc73d92-27d6-49ff-a8ab-2fae73519b4b">Information and Support for Azure Rights Management</link>.</para>
      <para>In addition, there are FAQs designed for end-users:</para><list class="bullet"><listItem><para><externalLink><linkText>FAQ for Rights Management Sharing Application for Windows</linkText><linkUri>https://technet.microsoft.com/dn467883</linkUri></externalLink></para></listItem><listItem><para><externalLink><linkText> FAQ for Rights Management Sharing Application for Mobile and Mac Platforms</linkText><linkUri>https://technet.microsoft.com/dn451248</linkUri></externalLink></para></listItem><listItem><para><externalLink><linkText>FAQ for Document Tracking</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=523977</linkUri></externalLink></para></listItem></list><para>This FAQ page will be updated regularly, with new additions listed in the monthly documentation update announcements on the <externalLink><linkText>Microsoft Rights Management (RMS) Team</linkText><linkUri>http://blogs.technet.com/b/rms/</linkUri></externalLink> blog. </para>
      <alert class="tip">
        <para>You can use the <externalLink><linkText>docs tag</linkText><linkUri>http://blogs.technet.com/b/rms/archive/tags/docs/</linkUri></externalLink> on the blog, to more easily find these documentation announcements.</para>
      </alert>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting Started with Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
