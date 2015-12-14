---
description: na
keywords: na
pagetitle: Requirements for Azure Rights Management
search: na
ms.author: e8f708ba3bce4153b61467184c747c7f
ms.date: 2015-12-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc78321d-d759-4653-8818-80da74b6cdeb
---
# Requirements for Azure Rights Management
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>To deploy Microsoft Azure Rights Management (Azure RMS) in your organization, make sure that you have the following prerequisites. You can then use the <link xlink:href="086600c2-c5d8-47ec-a4c0-c782e1797486">Azure Rights Management Deployment Roadmap</link> to deploy Rights Management for your organization.</para>
    <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
      <thead>
        <tr>
          <TD>
            <para>Requirement</para>
          </TD>
          <TD>
            <para>More information</para>
          </TD>
        </tr>
      </thead>
      <tbody>
        <tr>
          <TD>
            <para>A cloud subscription for RMS</para>
          </TD>
          <TD>
            <para>Your organization must have a cloud subscription that supports RMS.</para>
            <para>For licensing information, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedSubscriptions">Cloud subscriptions that support Azure RMS</link> section in this topic.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Azure AD directory </para>
          </TD>
          <TD>
            <para>Your organization must have an Azure AD directory to support user authentication for RMS. In addition, if you want to use your user accounts from your on-premises directory (AD DS), you must also configure directory integration. </para>
            <para>Multi-factor authentication (MFA) is supported with Azure RMS when you have the required client software and correctly configured     MFA supporting infrastructure.</para><para>For more information, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_AzureADTenant">Azure AD directory</link> section in this topic.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Client devices</para>
          </TD>
          <TD>
            <para>Users must have a client devices (computer or mobile device) that run an operating system that supports RMS.</para>
            <para>For more information, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedDevices">Client devices that support Azure RMS</link> section in this topic.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Applications</para>
          </TD>
          <TD>
            <para>Users must run applications that support RMS.</para>
            <para>For more information, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedApplications">Applications that support Azure RMS</link> section in this topic.</para>
          </TD>
        </tr>
        <tr>
          <TD>
            <para>Infrastructure that supports connectivity to the Internet and dependent cloud services</para>
          </TD>
          <TD>
            <?Comment CB: 13983 2015-03-05T08:43:00Z  Id='3?>
            <para>If you have a firewall or similar intervening network devices that must be configured to allow specific connections, see <externalLink><linkText>Office 356 URLs and IP address ranges</linkText><linkUri>https://support.office.com/en-US/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2</linkUri></externalLink>. <?CommentEnd Id='3'
    ?></para>
            <para>The list of URLs and IP addresses in the <embeddedLabel>Office 356 portal and identity</embeddedLabel> section apply to the Office 365 portal, Azure Active Directory resources, and Azure Rights Management. Use the instructions in this article to keep up-to-date with changes to this information, by subscribing to an RSS feed.</para>
            <para>In addition to the information in the Office article, specific to Azure RMS:</para>
            <list class="bullet">
              <listItem>
                <para>Do not terminate the TLS client-to-service connection (for example, to do packet-level inspection). Doing so breaks the certificate pinning that RMS clients use with Microsoft-managed CAs to help secure their communication with Azure RMS.</para>
              </listItem>
              <listItem>
                <para>Do not use a web proxy configuration that authenticates on behalf of a user.</para>
              </listItem>
            </list>
          </TD>
        </tr>
      </tbody>
    </table>
    <para> </para>
    <para>If you want to use Azure RMS with on-premises servers, the following products are supported:</para>
    <list class="bullet">
      <listItem>
        <para>Exchange Server</para>
      </listItem>
      <listItem>
        <para>SharePoint Server</para>
      </listItem>
      <listItem>
        <para>Windows Server file servers that support File Classification Infrastructure</para>
      </listItem>
    </list>
    <para>For information about the additional Azure RMS requirements for this scenario, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedServers">On-premises servers that support Azure RMS</link> section in this topic.</para>
    <alert class="important">
      <para>The following deployment scenario is not supported: </para>
      <list class="bullet">
        <listItem>
          <para>Running AD RMS and Azure RMS side-by-side in the same organization, except during migration, as described in <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172">Migrating from AD RMS to Azure Rights Management</link>.</para>
        </listItem>
      </list>
      <para>There is a supported migration path <externalLink><linkText>from AD RMS to Azure RMS</linkText><linkUri>http://technet.microsoft.com/library/Dn858447.aspx</linkUri></externalLink>, and from <externalLink><linkText>Azure RMS to AD RMS</linkText><linkUri>http://msdn.microsoft.com/library/azure/dn629429.aspx</linkUri></externalLink>. If you deploy Azure RMS and then decide that you no longer want to use this cloud service, see <link xlink:href="0b1c2064-0d01-45ae-a541-cebd7fd762ad">Deactivating Azure Rights Management</link>. </para>
    </alert>
    <para>Use the following sections to learn more about the Azure RMS requirements.</para>
  </introduction>
  <section address="BKMK_SupportedSubscriptions">
    <title address="BKMK_Subscriptions">Cloud subscriptions that support Azure RMS</title>
    <content>
      <para>To use Azure RMS, your organization must have at least one of the following subscriptions with a sufficient number of licenses for users and services that will protect files and email messages. If you have a service that will apply protection for users (owners of the files or email messages), those users require one of these licenses. Users who will only consume (for example, read and edit) this protected data do not need a license.</para>
      <list class="bullet">
        <listItem>
          <para>Office 365</para>
        </listItem>
        <listItem>
          <para>Azure Rights Management Premium (formerly Azure RMS Standalone)</para>
        </listItem>
        <listItem>
          <para>Enterprise Mobility Suite</para>
        </listItem>
        <listItem>
          <para>RMS for individuals</para>
        </listItem>
      </list>
      <para>Use the following sections for more information and sign up options.</para>
      <para>For a licensing comparison of the Azure RMS capabilities for the paid subscriptions, see <externalLink><linkText>Comparison of Rights Management Services (RMS) Offerings</linkText><linkUri>http://technet.microsoft.com/dn858608</linkUri></externalLink>.</para>
    </content>
    <sections>
      <section expanded="false">
        <title>Office 365 subscription</title>
        <content>
          <para>
            <externalLink>
              <linkText>Free 30-day trial: Enterprise E3</linkText>
              <linkUri>http://go.microsoft.com/fwlink/p/?LinkID=403802</linkUri>
            </externalLink>
          </para>
          <para>This subscription is designed for organizations who want to use the Office online services and use their Information Rights Management feature, which uses Azure RMS. However, not all Office 365 subscriptions include Azure RMS. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Licensing option</para>
                </TD>
                <TD>
                  <para>Office 365 Business Essentials</para>
                </TD>
                <TD>
                  <para>Office 365 Business Premium</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise E1<br/><br/></para>
                  <para>Office 365 Education A1</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise E3<br/><br/></para>
                  <para>Office 365 Education A3<br/><br/></para>
                  <para>Office 365 Government G3</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise E4<br/> <br/></para>
                  <para>Office 365 Education A4<br/><br/></para>
                  <para>Office 365 Government G4</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise K1</para>
                </TD>
                <TD>
                  <para>SharePoint Plan 1<br/><br/>SharePoint Plan 2</para>
                </TD>
                <TD>
                  <para>Exchange Online Plan 1<br/> <br/>Exchange Online Plan 2</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Information Rights Protection (IRM) </para>
                </TD>
                <TD>
                  <para>No</para>
                </TD>
                <TD>
                  <para>No </para>
                </TD>
                <TD>
                  <para>No</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>No</para>
                </TD>
                <TD>
                  <para>No</para>
                </TD>
                <TD>
                  <para>No</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
      <section expanded="false">
        <title>Azure Rights Management Premium subscription</title>
        <content>
          
          <para>
            <externalLink>
              <linkText>Free 30-day trial</linkText>
              <linkUri>https://portal.microsoftonline.com/Signup/MainSignUp15.aspx?&amp;OfferId=A43415D3-404C-4df3-B31B-AAD28118A778&amp;dl=RIGHTSMANAGEMENT&amp;ali=1</linkUri>
            </externalLink>
          </para>
          <para>This subscription was formerly known as Azure RMS Standalone and it is designed for organizations that want to use Azure RMS but don’t have subscription that includes Azure RMS. For example, if you have a subscription for Office 365 Business Essentials or Office 365 Enterprise E1, these subscriptions do not include Azure RMS (see the table in the preceding section). To use Azure RMS, you could purchase a subscription for Azure Rights Management Premium (or purchase another subscription, such as Office 365 Enterprise E4, that includes Azure RMS).</para>
          <para>For more information, see <externalLink><linkText>Microsoft Azure Rights Management</linkText><linkUri>http://products.office.com/business/microsoft-azure-rights-management</linkUri></externalLink>.</para>
          <para>This subscription also offers a trial period for you to try out Azure RMS for 25 users, at no charge. If the subscription expires before you purchase a replacement subscription, see the following section, “What happens when the trial subscription expires?”</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Licensing option</para>
                </TD>
                <TD>
                  <para>Office 365 Business Essentials</para>
                </TD>
                <TD>
                  <para>Office 365 Business Premium</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise E1<br/><br/></para>
                  <para>Office 365 Education A1</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise E3<br/><br/></para>
                  <para>Office 365 Education A3<br/><br/></para>
                  <para>Office 365 Government G3</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise E4<br/> <br/></para>
                  <para>Office 365 Education A4<br/><br/></para>
                  <para>Office 365 Government G4</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise K1</para>
                </TD>
                <TD>
                  <para>SharePoint Plan 1<br/> <br/>SharePoint Plan 2</para>
                </TD>
                <TD>
                  <para>Exchange Online Plan 1<br/> <br/>Exchange Online Plan 2</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Information Rights Protection (IRM) </para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes <superscript>1</superscript></para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>
            <superscript>1</superscript> For Business Premium, there are some client restrictions: You can protect content and consume protected content with RMS by using the Outlook Web App and the RMS sharing app. You can consume protected content by using all other Office applications, which includes Office Online and the client applications for Office 365 Business Premium.</para>
        </content>
        <sections>
          <section address="BKMK_TrialExpiryBehavior">
            <title>What happens when the trial subscription expires?</title>
            <content>
              <para>If your trial subscription expires, you will lose access to content that was protected by using your trial subscription for Azure RMS. However, if you then purchase a subscription that supports Azure RMS, access is automatically restored.</para>
              <para>An exception to losing access upon expiry is if your organization used Azure RMS with the RMS for individuals subscription before you obtained the trial subscription. Then, access to previously protected content remains, even after the trial subscription expires.</para>
            </content>
          </section>
        </sections>
      </section>
      <section expanded="false">
        <title>Enterprise Mobility Suite subscription</title>
        <content>
          
          <para>
            <externalLink>
              <linkText>Free 30-day trial</linkText>
              <linkUri>http://go.microsoft.com/fwlink/?LinkId=615385</linkUri>
            </externalLink>
          </para><para>This subscription is designed for organizations who want to use a combination of Azure Active Directory Premium, Windows Intune, and Azure Rights Management. For more information, see the <externalLink><linkText>Microsoft Enterprise Mobility Overview</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=615386</linkUri></externalLink>.</para>
          <para/>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Licensing option</para>
                </TD>
                <TD>
                  <para>Office 365 Business Essentials</para>
                </TD>
                <TD>
                  <para>Office 365 Business Premium</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise E1<br/><br/></para>
                  <para>Office 365 Education A1</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise E3<br/><br/></para>
                  <para>Office 365 Education A3<br/><br/></para>
                  <para>Office 365 Government G3</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise E4<br/> <br/></para>
                  <para>Office 365 Education A4<br/><br/></para>
                  <para>Office 365 Government G4</para>
                </TD>
                <TD>
                  <para>Office 365 Enterprise K1</para>
                </TD>
                <TD>
                  <para>SharePoint Plan 1<br/> <br/>SharePoint Plan 2</para>
                </TD>
                <TD>
                  <para>Exchange Online Plan 1<br/> <br/>Exchange Online Plan 2</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>Information Rights Protection (IRM) </para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes <superscript>1</superscript></para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
                <TD>
                  <para>Yes</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>
            <superscript>1</superscript> For Business Premium, there are some client restrictions: You can protect content and consume protected content with RMS by using the Outlook Web App and the RMS sharing app. You can consume protected content by using all other Office applications, which includes Office Online and the client applications for Office 365 Business Premium.</para>
        </content>
      </section>
      <section expanded="false">
        <title>RMS for individuals subscription</title>
        <content>
          <para>This subscription is designed for individuals in an organization that hasn’t deployed Azure RMS or AD RMS. It lets these people read content that has been protected by an organization that is using Azure RMS, and they can also protect their own content.</para>
          <para>For more information, see <link xlink:href="2efcb440-fefd-45e9-872b-f471573aadf2">RMS for Individuals and Azure Rights Management</link>.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_AzureADTenant">
    <title>Azure AD directory</title>
    <content>
      <para>You must have an Azure AD directory to use Azure RMS. You use your organization account for this directory to sign in to the Azure classic portal, where, for example, you can configure and manage Rights Management templates. </para>
      <para>If you do not already have an Azure subscription for your organization, you can get one by signing up for a free trial.: Go to the <externalLink><linkText>Azure Get started</linkText><linkUri>https://account.windowsazure.com/organization</linkUri></externalLink> page and follow the instructions.</para>
      <para>For more information, see the following resources in the Azure Active Directory documentation:</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyLink xlink:href="185da266-58a9-43e6-9c66-2c8f702545c6">What is an Azure AD directory?</legacyLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <legacyLink xlink:href="edf05c2e-944a-4da5-a330-dc9dc479f127">How Azure subscriptions are associated with Azure AD</legacyLink>
          </para>
        </listItem>
      </list>
      <para>If you want to integrate your Azure AD directory with your on-premises AD forests, see <legacyLink xlink:href="bf82bdff-2467-403b-8c1a-0e9eebcf31e8">Directory integration</legacyLink>.</para>
      <alert class="note">
        <para>If you have mobile devices or Mac computers that authenticate on-premises by using AD FS or an equivalent authentication provider: </para>
        <list class="bullet">
          <listItem>
            <para>You must use AD FS on the minimum server version of <embeddedLabel>Windows Server 2012 R2</embeddedLabel>, or an alternative authentication provider that supports the OAuth 2.0 protocol.</para>
          </listItem>
        </list>
      </alert>
    </content>
  <sections><section address="BKMK_MFA">
<title>Multi-factor authentication (MFA) and Azure RMS</title><content><para>To use multi-factor authentication (MFA) with Azure RMS requires at least one of the following: </para><list class="bullet"><listItem><para>Office 2013 (minimum version):</para><list class="bullet"><listItem><para>   If you have Office 2013, you must also install the <externalLink><linkText>June 9, 2015, update for Office 2013 (KB3054853)</linkText><linkUri>https://support.microsoft.com/kb/3054853</linkUri></externalLink>. For more information about this update and how modern authentication brings Active Directory Authentication Library (ADAL)-based sign in to Office 2013, see <externalLink><linkText>Office 2013 modern authentication public preview announced</linkText><linkUri>https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/</linkUri></externalLink>  on the Office blog.</para></listItem></list></listItem><listItem><para>Rights Management sharing application for Windows: </para><list class="bullet"><listItem><para>You must have installed the minimum version of 1.0.1908.0, which can be confirmed by using Control Panel, Programs and Features. For more information about the sharing application, see  <link xlink:href="7d8a8abe-6de1-4088-90ee-e0c4bd6deec8">Rights Management Sharing Application for Windows</link>.</para></listItem></list></listItem><listItem><para>Rights Management sharing app for mobile devices and Mac computers: </para><list class="bullet"><listItem><para>Make sure that you have the latest version installed. MFA support went into the September 2015 release of the RMS sharing app.</para></listItem></list></listItem></list><para>Then, configure your MFA solution:</para><list class="bullet"><listItem><para>For Microsoft-managed tenants (you have Azure Active Directory or Office 365):  </para><list class="bullet"><listItem><para>Configure Azure MFA to enforce MFA for users. For instructions, see <externalLink><linkText>Getting started with Azure Multi-Factor Authentication in the cloud</linkText><linkUri>https://azure.microsoft.com/documentation/articles/multi-factor-authentication-get-started-cloud/</linkUri></externalLink> from the Azure documentation. </para><para>For more information about Azure MFA, see <externalLink><linkText>What is Azure Multi-Factor Authentication?</linkText><linkUri>https://azure.microsoft.com/documentation/articles/multi-factor-authentication/</linkUri></externalLink></para></listItem></list></listItem><listItem><para>For federated tenants (you operate federation servers on-premises):  </para> <list class="bullet"><listItem><para>Configure your federation servers for Azure Active Directory or Office 365. For example, if you are using AD FS, see <externalLink><linkText>Configure Additional Authentication Methods for AD FS</linkText><linkUri>https://technet.microsoft.com/library/dn758113.aspx</linkUri></externalLink> on TechNet.  </para><para> For more information about this scenario, see  <externalLink><linkText>The Works with Office 365 – Identity program now streamlined</linkText><linkUri>https://blogs.office.com/2014/01/30/the-works-with-office-365-identity-program-now-streamlined/</linkUri></externalLink> on the Office blog. </para></listItem></list></listItem></list></content>
</section></sections></section>
  <section address="BKMK_SupportedDevices">
    <title>Client devices that support Azure RMS</title>
    <content>
      <para>Use the following sections to identify which devices support Azure Rights Management (RMS), and which RMS capabilities they support:</para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_RMSSupportedComputers">Computers</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_RMSSupportedMobileDevices">Mobile devices</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_ClientCapabilities">Client device capabilities</link>
          </para>
        </listItem>
      </list>
    </content>
    <sections>
      <section address="BKMK_RMSSupportedComputers">
        <title>Computers</title>
        <content>
          <para>The following computer operating systems support Azure Rights Management:</para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyBold>Windows 7</legacyBold> (x86, x64)</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Windows 8</legacyBold> (x86, x64)</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Windows 8.1</legacyBold> (x86, x64)</para>
            </listItem><listItem>
              <para>
                <legacyBold>Windows 10</legacyBold> (x86, x64)</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Mac OS X</legacyBold>: Minimum version of Mac OS X 10.8 (Mountain Lion)</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_RMSSupportedMobileDevices">
        <title>Mobile devices</title>
        <content>
          <para>The following mobile device operating systems support Azure Rights Management:</para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyBold>Windows Phone</legacyBold>: Windows Phone 8.1</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Android phones and tablets</legacyBold>: Minimum version of Android 4.0.3</para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>iPhone and iPad</legacyBold>: Minimum version of iOS 7.0 </para>
            </listItem>
            <listItem>
              <para>
                <legacyBold>Windows RT tablets</legacyBold>: Windows 8 RT, Windows 8.1 RT</para>
            </listItem>
          </list>
          
        </content>
      </section>
      <section address="BKMK_ClientCapabilities">
        <title>Client device capabilities</title>
        <content>
          <para>Not all supported client devices currently support all RMS capabilities. Use the following table to identify which applications support the RMS capabilities, and the exceptions.</para>
          <para>Unless stated otherwise, the supported capabilities apply to both Azure RMS and AD RMS. In addition, AD RMS support on iOS, Android, OS X, and Windows Phone 8.1 requires <externalLink><linkText>Active Directory Rights Management Services Mobile Device Extension</linkText><linkUri>http://technet.microsoft.com/library/a69ead9d-7dd3-4b38-9830-4728e9757341</linkUri></externalLink>.</para>
          <para/>
          <para>Information about the table columns:</para>
          <list class="bullet">
            <listItem>
              <para>
                <embeddedLabel>Protected PDF</embeddedLabel>: Files that have a .ppdf file name extension and that are automatically created when you use the RMS sharing application to share Office files and PDF files by email. The RMS sharing application includes a reader for protected PDF files. Previously, if you created PDF files that you protected by using Azure RMS or AD RMS, you can continue to read these files on Windows, iOS, and Android devices by using Foxit Reader and Nitro Pro.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Email:</embeddedLabel> The email clients listed can protect the email message itself, which will automatically protect any attached files. In this scenario, the client’s preview feature can display the protected content (message and attachment) to authorized recipients. However, if an email message itself is not protected but the attachment is protected, the client’s preview feature cannot display the protected attachment to authorized recipients.</para>
            </listItem>
            <listItem>
              <para>
                <embeddedLabel>Other file types</embeddedLabel>: Text and image files include files that have a file name extension such as .txt, .xml, .jpg, .and jpeg. These files change their file name extension after they are natively protected by RMS, and become read-only. Files that cannot be natively protected have a .pfile file name extension after they are generically protected by RMS. For more information, see the <externalLink><linkText>Levels of protection – native and generic</linkText><linkUri>https://technet.microsoft.com/library/dn339003.aspx#BKMK_LevelsofProtection</linkUri></externalLink> and <externalLink><linkText>Supported file types and file name extensions</linkText><linkUri>https://technet.microsoft.com/library/dn339003.aspx#BKMK_SupportFileTypes</linkUri></externalLink> sections from the <externalLink><linkText>Rights Management sharing application administrator guide</linkText><linkUri>http://technet.microsoft.com/library/dn339003(v=ws.10).aspx</linkUri></externalLink>.</para>
            </listItem>
          </list>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Device operating system</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>Word, Excel, PowerPoint</para>
                </TD>
                <TD>
                  <para>Protected PDF</para>
                </TD>
                <TD>
                  <para>Email</para>
                </TD>
                <TD>
                  <para>Other file types</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD rowspan="1">
                  <para>
                    <embeddedLabel>Windows</embeddedLabel>
                  </para>
                </TD>
                <TD rowspan="1">
                  <para>Office 2010</para><para>Office 2013</para>
                  
                  <para>Office Mobile apps (Azure RMS only)<superscript>1</superscript></para><para>Office Online<superscript>2</superscript></para>
                </TD>
                <TD rowspan="1">
                  <para>Gaaiho Doc</para><para>GigaTrust Desktop PDF Client for Adobe</para>
                  <para>Foxit Reader</para>
                  <para>Nitro PDF Reader</para>
                  <para>RMS sharing app</para>
                </TD>
                <TD rowspan="1">
                  <para>Outlook 2010</para><para>Outlook 2013</para>
                  
                  <para>Outlook Web App (OWA)</para>
                <para>Windows Mail<superscript>3</superscript></para></TD>
                <TD rowspan="1">
                  <para>RMS sharing application for Windows: Text, images, pfile</para>
                <para>Siemens JT2Go: JT files (Windows 10 only)</para></TD>
              </tr>
              <tr>
                <TD rowspan="1">
                  <para>
                    <embeddedLabel>iOS</embeddedLabel>
                  </para>
                </TD>
                <TD rowspan="1">
                  <para>Office for iPad and iPhone<superscript>4</superscript></para><para>Office Online<superscript>2</superscript></para>
                <para>TITUS Docs</para></TD>
                <TD rowspan="1">
                  <para>Foxit Reader</para>
                  <para>RMS sharing app<superscript>1</superscript></para>
                  <para>TITUS Docs</para>
                </TD>
                <TD rowspan="1">
                  <para>NitroDesk</para>
                  <para>Outlook for iPad and iPhone<superscript>3</superscript></para><para>OWA for iOS </para>
                  <para>Secure Islands IQProtector<superscript>1</superscript></para><para>TITUS Mail</para>
                </TD>
                <TD rowspan="1">
                  <para>RMS sharing app<superscript>1</superscript>: Text, images, pfile</para>
                  <para>TITUS Docs: Pfile</para>
                </TD>
              </tr>
              <tr>
                <TD rowspan="1">
                  <para>
                    <embeddedLabel>Android</embeddedLabel>
                  </para>
                </TD>
                <TD rowspan="1">
                  <para>GigaTrust App for Android</para>
                  <para>Office Online<superscript>2</superscript></para>
                </TD>
                <TD rowspan="1">
                  <para>GigaTrust App for Android</para>
                  <para>Foxit Reader</para>
                  <para>RMS sharing app<superscript>1</superscript></para>
                </TD>
                <TD rowspan="1">
                  <para>9Folders</para>
                  <para>GigaTrust App for Android</para>
                  <para>NitroDesk</para>
                  <para>OWA for Android<superscript>5</superscript></para>
                  <para>Samsung Email (S3 and later)</para>
                  <para>Secure Islands IQProtector<superscript>1</superscript></para><para>TITUS Classification for Mobile</para>
                </TD>
                <TD rowspan="1">
                  <para>RMS sharing app<superscript>1</superscript>: Text, images, pfile</para>
                </TD>
              </tr>
              <tr>
                <TD rowspan="1">
                  <para>
                    <embeddedLabel>OS X</embeddedLabel>
                  </para>
                  <para/>
                </TD>
                <TD rowspan="1">
                  <para>Office 2011 (AD RMS only)</para>
                  <para>Office 2016 for Mac</para><para>Office Online<superscript>2</superscript></para>
                </TD>
                <TD rowspan="1">
                  <para>Foxit Reader</para><para>RMS sharing app<superscript>1</superscript></para>
                </TD>
                <TD rowspan="1">
                  <para>Outlook 2011 (AD RMS only)</para>
                  <para>Outlook 2016 for Mac</para><para>Outlook for Mac</para>
                </TD>
                <TD rowspan="1">
                  <para>RMS sharing app<superscript>1</superscript>: Text, images, pfile</para>
                </TD>
              </tr>
              <tr>
                <TD rowspan="1">
                  <para>
                    <embeddedLabel>Windows RT</embeddedLabel>
                  </para>
                </TD>
                <TD rowspan="1">
                  <para>Office 2013 RT</para>
                  <para>Office Online<superscript>2</superscript></para>
                </TD>
                <TD rowspan="1">
                  <para>Not supported</para>
                </TD>
                <TD rowspan="1">
                  <para>Outlook 2013 RT</para>
                  <para>Mail app for Windows</para>
                <para>Windows Mail<superscript>3</superscript></para></TD>
                <TD rowspan="1">
                  <para>Siemens JT2Go: JT files</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Windows Phone 8.1</embeddedLabel> </para>
                </TD>
                <TD>
                  <para> Office Mobile (AD RMS only)</para>
                </TD>
                <TD>
                  <para>RMS sharing app<superscript>1</superscript></para>
                </TD>
                <TD>
                  <para>Outlook Mobile</para>
                </TD>
                <TD>
                  <para>RMS sharing app<superscript>1</superscript>: Text, images, pfile </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <embeddedLabel>Blackberry 10</embeddedLabel>
                  </para>
                </TD>
                <TD>
                  <para>Not supported</para>
                </TD>
                <TD>
                  <para>Not supported</para>
                </TD>
                <TD>
                  <para>Blackberry email<superscript>3</superscript></para>
                </TD>
                <TD>
                  <para>Not supported</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>
            <superscript>1</superscript> Supports viewing protected content.</para><para><superscript>2</superscript> Supports viewing protected content in SharePoint Online, OneDrive for Business, and Outlook Web Access.</para><para><superscript>3</superscript> Uses Exchange ActiveSync IRM, which must be enabled by the Exchange administrator. Users can view, reply, and reply all for protected email messages but users cannot protect new email messages themselves. </para><para>
            <superscript>4</superscript> Supports viewing and editing protected documents. For more information, see the following post on the Office blog: <externalLink><linkText>Azure Rights Management support comes to Office for iPad and iPhone</linkText><linkUri>https://blogs.office.com/2015/07/22/azure-rights-management-support-comes-to-office-for-ipad-and-iphone-2/</linkUri></externalLink></para>
          
          <para>
            <superscript>5</superscript> For more information, see the following post on the Office blog: <externalLink><linkText>OWA for Android now available on select devices</linkText><linkUri>http://blogs.office.com/2014/06/11/owa-for-android-now-available-on-select-devices/</linkUri></externalLink></para>
        <alert class="tip">
 <para>For more information about upcoming RMS support in Office for different platforms, see the following post from the Office blog: <externalLink><linkText>Office everywhere, encryption everywhere</linkText><linkUri>http://blogs.office.com/2015/02/18/office-everywhere-encryption-everywhere/</linkUri></externalLink></para></alert></content>
      </section>
    </sections>
  </section>
  <section address="BKMK_SupportedApplications">
    <title>Applications that support Azure RMS</title>
    <content>
      <para>The following applications natively support Azure RMS, which means that RMS is tightly integrated into these applications by using RMS APIs to support usage restrictions. These applications are also known as RMS-enlightened:</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>Microsoft Office applications</legacyBold> (Word, Excel, PowerPoint, and Outlook) from the following suites can protect content by using Azure RMS:</para>
          <list class="bullet">
            <listItem>
              <para>Office 365 ProPlus</para>
            </listItem>
            <listItem>
              <para>Office 365 Enterprise E3</para>
            </listItem>
            <listItem>
              <para>Office 365 Enterprise E4</para>
            </listItem><listItem><para>Office Professional Plus 2016</para></listItem><listItem>
              <para>Office Professional Plus 2013</para>
            </listItem>
            <listItem>
              <para>Office Professional Plus 2010</para>
              
            </listItem>
          </list>
          <maml:para xmlns:maml="http://ddue.schemas.microsoft.com/authoring/2003/5">Other editions of Office (with the exception of Office 2007) can consume protected content. </maml:para>
        <alert class="note">
                <para>Azure RMS with Office Professional Plus 2010 or Office Professional 2010: </para>
                <list class="bullet">
                  <listItem>
                    <para>Requires the Rights Management sharing application for Windows</para>
                  </listItem>
                <listItem><para>Not supported on Windows 10</para></listItem></list>
              </alert></listItem>
        <listItem>
          <para>
            <legacyBold>The Rights Management sharing application for Windows</legacyBold>
          </para>
          <para>For more information about the Rights Management sharing application for Windows, see the following resources:</para>
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
        </listItem>
        <listItem>
          <para>
            <legacyBold>The Rights Management sharing application for mobile platforms</legacyBold>
          </para>
          <para>For more information about the Rights Management sharing application for mobile platforms, see the following resources:</para>
          <list class="bullet">
            <listItem>
              <para>Download the relevant app by using the links on the <externalLink><linkText>Microsoft Rights Management page</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=303970</linkUri></externalLink></para>
            </listItem>
            <!--Not to go live before  Intune goes out.--><maml:listItem xmlns:maml="http://ddue.schemas.microsoft.com/authoring/2003/5">
              <maml:para>If you manage mobile devices by using Microsoft Intune, you can deploy and configure the app on <maml:externalLink><maml:linkText>iOS and Android devices as a policy managed app</maml:linkText><maml:linkUri>https://technet.microsoft.com/library/dn878026.aspx</maml:linkUri></maml:externalLink>.</maml:para>
            </maml:listItem><listItem>
              <para>
                <externalLink>
                  <linkText>FAQ for Microsoft Rights Management Sharing Application for Mobile Platforms</linkText>
                  <linkUri>http://technet.microsoft.com/dn451248</linkUri>
                </externalLink>
              </para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Other applications that support the RMS APIs</legacyBold>:</para>
          <list class="bullet">
            <listItem>
              <para>Line-of-business applications that are written in-house by using the RMS SDK</para>
            </listItem>
            <listItem>
              <para>Applications from software vendors that are written by using the RMS SDK</para>
            </listItem>
          </list>
          <para>For more information about <?Comment CB: Updated link per Gagan 2015-03-05T08:43:00Z  Id='85?>the SDK<?CommentEnd Id='85'
    ?>, see the <externalLink><linkText>Microsoft Rights Management SDK</linkText><linkUri>http://msdn.microsoft.com/library/hh552972(v=vs.85).aspx</linkUri></externalLink>.</para>
        </listItem>
      </list>
      <alert class="important">
        <para>The following applications are not currently supported by Azure RMS:</para>
        <list class="bullet">
          <listItem>
            <para>Microsoft Office for Mac 2011</para>
          </listItem>
          
          <listItem>
            <para>Microsoft OneDrive for Business for SharePoint Server 2013</para>
          </listItem>
        <listItem><para>XPS Viewer </para></listItem></list>
        <para>In addition, the RMS sharing application has the following restrictions: </para>
        <list class="bullet">
          <listItem>
            <para>For Windows computers: Requires a minimum version of Windows 7 Service Pack 1</para>
          </listItem>
        </list>
      </alert>
      <para>For more information about how these applications support Azure RMS, see <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link>. </para>
      <para>For information about how to configure them, see <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36">Configuring Applications for Azure Rights Management</link>.</para>
    </content>
  </section>
  <section address="BKMK_SupportedServers">
    <title>On-premises servers that support Azure RMS</title>
    <content>
      <para>The following on-premises server products are supported with Azure RMS when you use the Azure RMS connector, which acts as a communications interface (a relay) between the on-premises servers and Azure RMS. In addition, this configuration requires that you configure directory synchronization between your Active Directory forests and Azure Active Directory.</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>Exchange Server</legacyBold>:</para>
          <list class="bullet">
            <listItem>
              <para>Exchange Server 2013</para>
            </listItem>
            <listItem>
              <para>Exchange Server 2010</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Office SharePoint Server</legacyBold>:</para>
          <list class="bullet">
            <listItem>
              <para>Office SharePoint Server 2013</para>
            </listItem>
            <listItem>
              <para>Office SharePoint Server 2010</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <legacyBold>File servers that run Windows Server and use File Classification Infrastructure (FCI)</legacyBold>:</para>
          <list class="bullet">
            <listItem>
              <para>Windows Server 2012 R2</para>
            </listItem>
            <listItem>
              <para>Windows Server 2012</para>
            </listItem>
          </list>
          <alert class="note">
            <para>Because file servers that run Windows Server 2008 R2 do not have a built-in file management task action to apply RMS protection, you cannot use the RMS connector for this scenario. However, you can use File Classification Infrastructure and Azure RMS on these operating systems if you configure a custom file management task to run an executable or script that can protect files by using Azure RMS. For example, a Windows PowerShell script that uses the <externalLink><linkText>RMS Protection cmdlets</linkText><linkUri>https://msdn.microsoft.com/library/azure/mt433195.aspx</linkUri></externalLink>. </para>
          <para>You can also use these cmdlets with servers running later versions of Windows Server, with the benefit that these cmdlets can protect all file types. The RMS connector protects Office files only. For how-to instructions, see <link xlink:href="9aa693db-9727-4284-9f64-867681e114c9">RMS Protection with Windows Server File Classification Infrastructure (FCI)</link>.</para></alert>
        </listItem>
      </list>
      <para>The RMS connector is supported on Windows Server 2012 R2, Windows Server 2012, and Windows Server 2008 R2.</para>
      <para>For more information about how to configure the RMS connector for these on-premises servers, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066">Deploying the Azure Rights Management Connector</link>.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting Started with Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
