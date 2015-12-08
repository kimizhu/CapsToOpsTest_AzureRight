---
description: na
search: na
title: Configuring Applications for Azure Rights Management
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 2015-10-01
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# Configuring Applications for Azure Rights Management
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <alert class="note">
      <para>This information is for IT administrators and consultants who have deployed Azure Rights Management. If you are looking for user help and information about how to use Rights Management for a specific application or how to open a file that is rights-protected, use the help and guidance that accompanies your application.</para>
      <para>For example, for Office applications, click the Help icon and enter search terms such as <userInput>Rights Management</userInput> or <userInput>IRM</userInput>. For the RMS sharing application for Windows, see the <externalLink><linkText>Rights Management sharing application user guide</linkText><linkUri>http://technet.microsoft.com/library/dn339006.aspx</linkUri></externalLink>.</para>
    </alert>
    <para>After you have deployed Azure Rights Management (Azure RMS) for your organization, use the following information to configure applications and services to support Azure RMS. These include Office applications such as Word 2013 and Word 2010, and services such as Exchange Online (transport rules, data loss prevention, do not forward, and message encryption) and SharePoint Online (protected libraries). For information about how these applications and services support Rights Management, see <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link>.</para>
    <alert class="important">
      <para>For information about supported versions and other requirements, see <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link>.</para>
    </alert>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_O365">Office 365: Configuration for clients and online services</link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_ExchangeOnline">Exchange Online: IRM Configuration</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="#BKMK_SharePointOnline">SharePoint Online and OneDrive for Business: IRM Configuration</link>
            </para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="#BKMK_Office2013Configuration">Office 2016 and Office 2013: Configuration for clients</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_Office2010Configuration">Office 2010: Configuration for clients</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_SharingApp">Rights Management sharing application: Installation and configuration for clients</link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_SharingAppforWindows">The RMS sharing application for Windows: Installation and configuration</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_SharingAppMovileDevices">The RMS sharing application for mobile platforms: Installation</link>
            </para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_RMSAPIs">Other applications that support the RMS APIs: Installation and configuration</link>
        </para>
      </listItem>
    </list>
    <para>To configure on-premises servers such as Exchange Server and SharePoint Server, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066">Deploying the Azure Rights Management Connector</link>.</para>
    <alert class="tip">
      <para>For high-level examples and screenshots of applications configured to use Azure RMS, see the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_RMSpictures">Azure RMS in action: What administrators and users see</link> section from the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link> topic.</para>
    </alert>
  </introduction>
  <section address="BKMK_O365">
    <title>Office 365: Configuration for clients and online services</title>
    <content>
      <para>Because Office 365 natively supports Azure RMS, no client computer configuration is required to support the information rights management (IRM) features for applications such as Word, Excel, PowerPoint, Outlook and the Outlook Web App. All users have to do is sign in to their Office applications with their <token>o365_1</token> credentials and they can protect files and emails, and use files and emails that have been protected by others.  </para>
      <para>However, we recommend that you supplement these applications with the Rights Management sharing application, so that users get the benefit of the Office add-in. For more information, see the <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_SharingApp">Rights Management sharing application: Installation and configuration for clients</link> section in this topic.</para>
    </content>
    <sections>
      <section address="BKMK_ExchangeOnline" expanded="false">
        <title>Exchange Online: IRM Configuration</title>
        <content>
          <para>To configure Exchange Online to support Azure RMS, you must configure the information rights management (IRM) service for Exchange Online. To do this, you use Windows PowerShell (no need to install a separate module), and run <externalLink><linkText>PowerShell commands for Exchange Online</linkText><linkUri>https://technet.microsoft.com/library/jj200677.aspx</linkUri></externalLink>. </para><alert class="note">
 <para>You cannot currently configure Exchange Online to support Azure RMS if you are using a customer-managed tenant key (BYOK) for Azure RMS, rather than the default configuration of a Microsoft-managed tenant key. For more information, see the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_Pricing">BYOK pricing and restrictions</link> section in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and Implementing Your Azure Rights Management Tenant Key</link> topic.</para>
<para>If you try to configure Exchange Online when Azure RMS is using BYOK, the command to import the key (step 5,  in the following procedure) fails with the error message <ui>[FailureCategory=Cmdlet-FailedToGetTrustedPublishingDomainFromRmsOnlineException]</ui>.</para></alert><para>The following steps provide a typical set of commands that you would run to enable Exchange Online to use Azure RMS:</para><list class="ordered"><listItem><para>If this is the first time that you have used Windows PowerShell for Exchange Online on your computer, you must configure Windows PowerShell to run signed scripts. Start your Windows PowerShell session by using the <ui>Run as administrator</ui> option, and then type:</para><code>
Set-ExecutionPolicy RemoteSigned </code></listItem><listItem><para>In your Windows PowerShell session, sign in to Exchange Online by using an account that is enabled for remote Shell access. By default, all accounts that are created in Exchange Online are enabled for remote Shell access but this can be disabled  (and enabled) by using the   <externalLink><linkText>Set-User &lt;UserIdentity&gt; -RemotePowerShellEnabled</linkText><linkUri>https://technet.microsoft.com/library/jj984292(v=exchg.160).aspx</linkUri></externalLink> command. </para><para>To sign in, type:</para><code>$Cred = Get-Credential</code><para>In the <ui>Windows PowerShell credential request</ui> dialog box, supply your Office 365 user name and password.</para></listItem><listItem><para>Connect to the Exchange Online service by running the following two commands:</para><code>$Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.outlook.com/powershell/ -Credential $Cred -Authentication Basic –AllowRedirection</code><code>Import-PSSession $Session</code></listItem><listItem><para>Specify the location of the Azure RMS tenant key, according to your region:</para><para>For North America (and government subscriptions):</para><code>Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.na.aadrm.com/TenantManagement/ServicePartner.svc"</code><para>For Europe:</para><code>Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.eu.aadrm.com/TenantManagement/ServicePartner.svc"</code><para>For Asia:</para><code>Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.ap.aadrm.com/TenantManagement/ServicePartner.svc"</code><para>For South America:</para><code>Set-IRMConfiguration -RMSOnlineKeySharingLocation "https://sp-rms.sa.aadrm.com/TenantManagement/ServicePartner.svc"</code></listItem><listItem><para>Import configuration data from Azure RMS to Exchange Online, in the form of the trusted publishing domain (TPD). This includes the Azure RMS tenant key and Azure RMS templates:</para><code>Import-RMSTrustedPublishingDomain -RMSOnline -name "RMS Online"</code><para>In this command, we used the name of <ui>RMS Online</ui>  for the base name of the TPD for Azure RMS in Exchange Online. After the TPD is imported, it is named <system>RMS Online - 1</system> in Exchange Online. </para></listItem><listItem><para>Enable Azure RMS functionality so that IRM features are available for Exchange Online:</para><code>Set-IRMConfiguration -InternalLicensingEnabled $true</code><para>After running this command, Rights Management is automatically enabled for the Outlook client, the Outlook Web app, and Exchange Active Sync.</para></listItem><listItem><para>Optionally, test that this configuration is successful by using the following command:</para><code>Test-IRMConfiguration -Sender &lt;user email address&gt;</code><para>For example: <userInput>Test-IRMConfiguration -Sender  adams@contoso.com</userInput></para><para>This command runs a series of checks that includes verifying connectivity to the service, retrieving the configuration, retrieving URIs, licenses, and any templates. In the Windows PowerShell session, you will see the results of each and at the end, if everything passes these checks: <ui>OVERALL RESULT: PASS</ui> </para></listItem><listItem><para>Disconnect your remote PowerShell session:</para><code>Remove-PSSession $Session</code></listItem></list><para>Users can now protect their email messages by using Azure RMS. For example,  in the Outlook Web App, select <ui>Set permissions</ui> from the extended menu (<ui>...</ui>), and then choose <ui>Do Not Forward</ui> or one of the available templates to apply information protection to the email message and any attachments. However, because the Outlook Web App caches the UI for a day, wait for this time period to elapse before you try applying information protection to email messages and after running these configuration commands. Before the UI updates to reflect the new configuration, you will not see any options from the <ui>Set permissions</ui> menu.</para>
        <alert class="important">
 <para>If you create new <externalLink><linkText>custom templates</linkText><linkUri>https://technet.microsoft.com/library/dn642472.aspx</linkUri></externalLink> for Azure RMS or update the templates, each time, you must run the following Exchange Online PowerShell command (if necessary, run steps 2 and 3 first) to synchronize these changes to Exchange Online: <codeInline>Import-RMSTrustedPublishingDomain -Name "RMS Online - 1" -RefreshTemplates –RMSOnline</codeInline></para>
</alert><para>As an Exchange administrator, you can now configure features that apply information protection automatically, such as <externalLink><linkText>transport rules</linkText><linkUri>https://technet.microsoft.com/library/dd302432.aspx</linkUri></externalLink>, <externalLink><linkText>data loss prevention (DLP) policies</linkText><linkUri>https://technet.microsoft.com/library/jj150527(v=exchg.150).aspx</linkUri></externalLink>, and <externalLink><linkText>protected voice mail</linkText><linkUri>https://technet.microsoft.com/library/dn198211(v=exchg.150).aspx</linkUri></externalLink> (Unified Messaging).</para><para> For detailed instructions to configure Exchange Online to enable IRM functionality, see the documentation in the Exchange library. For example: </para><list class="bullet"><listItem><para><externalLink><linkText>Connect to Exchange Online using remote PowerShell</linkText><linkUri>https://technet.microsoft.com/library/jj984289(v=exchg.160).aspx</linkUri></externalLink></para></listItem><listItem><para><externalLink><linkText>Configure IRM to use Azure Rights Management</linkText><linkUri>https://technet.microsoft.com/library/dn151475(v=exchg.150).aspx</linkUri></externalLink></para></listItem></list></content>
      <sections><section>
<title>Office 365 Message Encryption</title><content><para>Run the same steps as documented in the previous section, but if you don't want templates to be displayed, before step 6,  run the following command to prevent IRM templates from being available in the Outlook Web App and Outlook client: <codeInline>Set-IRMConfiguration -ClientAccessServerEnabled $false</codeInline></para><para>Then, you're ready to configure <externalLink><linkText>transport rules</linkText><linkUri>https://technet.microsoft.com/library/dd302432.aspx</linkUri></externalLink> to automatically modify the message security when recipients are located outside the organization, and select the <ui>Apply Office 365 Message Encryption</ui> option.</para><para>For more information about message encryption, see <externalLink><linkText>Encryption in Office 365</linkText><linkUri>https://technet.microsoft.com/library/dn569286.aspx</linkUri></externalLink> in the Exchange library.</para></content>
</section></sections></section>
      <section address="BKMK_SharePointOnline" expanded="false">
        <title>SharePoint Online and OneDrive for Business: IRM Configuration</title>
        <content>
          <para>To configure SharePoint Online and OneDrive for Business to support Azure RMS, you must first enable the information rights management (IRM) service for SharePoint Online by using the SharePoint admin center. Then, site owners can  IRM-protect their SharePoint lists and document libraries, and users can IRM-protect their OneDrive for Business library so that documents that are saved there, and shared with others, are automatically protected by Azure RMS.</para>
          <para>To enable the  information rights management (IRM) service for SharePoint Online, see the following instructions from the Office website:</para>
          <list class="bullet">
            <listItem>
              <para>
                <externalLink>
                  <linkText>Set up Information Rights Management (IRM) in SharePoint admin center</linkText>
                  <linkUri>http://office.microsoft.com/office365-sharepoint-online-enterprise-help/set-up-information-rights-management-irm-insharepoint-online-HA102895193.aspx</linkUri>
                </externalLink>
              </para>
            </listItem>
            
          </list>
        <para>This configuration is done by the Office 365 administrator.</para></content>
      <sections><section>
<title>Configuring IRM for libraries and lists</title><content><para>After you have enabled the   IRM service for SharePoint, site owners can  IRM-protect their SharePoint document libraries and lists. For instructions, see the following from the Office website:</para><list class="bullet">
            
            <listItem>
              <para> <externalLink><linkText>Apply Information Rights Management to a list or library</linkText><linkUri>http://office.microsoft.com/sharepoint-help/apply-information-rights-management-to-a-list-or-library-HA102891460.aspx</linkUri></externalLink></para>
            </listItem>
          </list><para>This configuration is done by the SharePoint site administrator.</para></content>
</section><section address="BKMK_OneDrive" expanded="true">
<title>Configuring IRM for OneDrive for Business</title><content><para>After you have enabled the   IRM service for SharePoint Online, users' OneDrive for Business document library can then be configured for  Rights Management protection.  Users can configure this for themselves by using the <ui>Settings</ui> icon in their OneDrive. Although administrators cannot configure Rights Management for users' OneDrive for Business by using the SharePoint admin center, you can do this by using Windows PowerShell.</para><alert class="note">
 <para>For more information about configuring OneDrive for Business, see the Office documentation,<externalLink><linkText>Set up OneDrive for Business in Office 365</linkText><linkUri>https://support.office.com/article/Set-up-OneDrive-for-Business-in-Office-365-3e21f8f0-e0a1-43be-aa3e-8c0236bf11bb</linkUri></externalLink>.</para>
</alert></content>
<sections><section>
<title>Configuration for users</title><content><para>Give users these instructions so that they can configure their OneDrive for Business and IRM-protect their business files.</para><list class="ordered"><listItem><para>In OneDrive, click the <ui>Settings</ui> icon, to open the Settings menu, and then click <ui>Site Contents</ui>. </para></listItem><listItem><para>Hover on the <ui>Documents</ui> tile, chose the ellipses (<ui>...</ui>), and then click <ui>SETTINGS.</ui></para></listItem><listItem><para>On the <ui>Settings</ui> page, in the <ui>Permissions and Management</ui> section, click <ui>Information Rights Management</ui>.</para></listItem><listItem><para>On the <ui>Information Rights Management Settings</ui> page, select <ui>Restrict permissions on this library on download</ui> check box, specify your choice of  name and a description for the permissions, and optionally, click <ui>SHOW OPTIONS</ui> to configure optional configurations, and then click <ui>OK</ui>.</para><para>For more information about the configuration options, see the instructions in <externalLink><linkText>Apply Information Rights Management to a list or library</linkText><linkUri>https://support.office.com/article/Apply-Information-Rights-Management-to-a-list-or-library-3bdb5c4e-94fc-4741-b02f-4e7cc3c54aa1</linkUri></externalLink> from the Office documentation. </para></listItem></list><para>Because this configuration relies on users rather than an administrator to IRM-protect their OneDrive for Business library, educate users about the  benefits of protecting their files and how to do this. For example, explain that when they share a document from OneDrive for Business, only people they authorize can access it with  any restrictions that they configure, even if the file is renamed and copied somewhere else.</para></content>
</section><section>
<title>Configuration for administrators</title><content><para>Although you cannot configure IRM for users' OneDrive for Business by using the SharePoint admin center, you can do this by using Windows PowerShell. To enable IRM for these libraries, follow these steps:</para><list class="ordered"><listItem><para>Download and install the <externalLink><linkText>SharePoint Online Client Components SDK</linkText><linkUri>http://www.microsoft.com/en-us/download/details.aspx?id=42038</linkUri></externalLink>.</para></listItem><listItem><para>Download and install the <externalLink><linkText>SharePoint Online Management Shell</linkText><linkUri>http://www.microsoft.com/en-us/download/details.aspx?id=35588</linkUri></externalLink>.</para></listItem><listItem><para>Copy the contents of the following script and name the file Set-IRMOnOneDriveForBusiness.ps1 on your computer.</para><para><legacyItalic><embeddedLabel>Disclaimer</embeddedLabel></legacyItalic>: This sample script is not supported under any Microsoft standard support program or service. This sample script is provided AS IS without warranty of any kind.</para><code># Requires Windows PowerShell version 3

&lt;#
  Description:

    Configures IRM policy settings for OneDrive for Business and can also be used for SharePoint Online libraries and lists

 Script Installation Requirements: 

   SharePoint Online Client Components SDK
   http://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   http://www.microsoft.com/en-us/download/details.aspx?id=35588

==============================================================
#&gt;

# URL will be in the format https://&lt;tenant-name&gt;-admin.sharepoint.com
$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.com"

$webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
             "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
             "https://contoso-my.sharepoint.com/personal/user3_contoso_com")

&lt;# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row). 
   Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

#&gt;

$listTitle = "Documents"

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI 
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Set-IrmConfiguration
{
    [cmdletbinding()]
    param(
        [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List,
        [parameter(Mandatory=$true)][string]$PolicyTitle,
        [parameter(Mandatory=$true)][string]$PolicyDescription,
        [parameter(Mandatory=$false)][switch]$IrmReject,
        [parameter(Mandatory=$false)][DateTime]$ProtectionExpirationDate,
        [parameter(Mandatory=$false)][switch]$DisableDocumentBrowserView,
        [parameter(Mandatory=$false)][switch]$AllowPrint,
        [parameter(Mandatory=$false)][switch]$AllowScript,
        [parameter(Mandatory=$false)][switch]$AllowWriteCopy,
        [parameter(Mandatory=$false)][int]$DocumentAccessExpireDays,
        [parameter(Mandatory=$false)][int]$LicenseCacheExpireDays,
        [parameter(Mandatory=$false)][string]$GroupName
    )

    process
    {
        Write-Verbose "Applying IRM Configuration on '$($List.Title)'"

        # reset the value to the default settings
        $list.InformationRightsManagementSettings.Reset()

        $list.IrmEnabled = $true

        # IRM Policy title and description

            $list.InformationRightsManagementSettings.PolicyTitle       = $PolicyTitle
            $list.InformationRightsManagementSettings.PolicyDescription = $PolicyDescription


        # Set additional IRM library settings

            # Do not allow users to upload documents that do not support IRM
            $list.IrmReject = $IrmReject.IsPresent

            $parsedDate = Get-Date
            if([DateTime]::TryParse($ProtectionExpirationDate, [ref]$parsedDate))
            {
                # Stop restricting access to the library at &lt;date&gt;
                $list.IrmExpire = $true
                $list.InformationRightsManagementSettings.DocumentLibraryProtectionExpireDate = $ProtectionExpirationDate
            }

            # Prevent opening documents in the browser for this Document Library
            $list.InformationRightsManagementSettings.DisableDocumentBrowserView = $DisableDocumentBrowserView.IsPresent

        # Configure document access rights

            # Allow viewers to print 
            $list.InformationRightsManagementSettings.AllowPrint = $AllowPrint.IsPresent

            # Allow viewers to run script and screen reader to function on downloaded documents
            $list.InformationRightsManagementSettings.AllowScript = $AllowScript.IsPresent

            # Allow viewers to write on a copy of the downloaded document
            $list.InformationRightsManagementSettings.AllowWriteCopy = $AllowWriteCopy.IsPresent

            if($DocumentAccessExpireDays)
            {
                # After download, document access rights will expire after these number of days (1-365)
                $list.InformationRightsManagementSettings.EnableDocumentAccessExpire = $true
                $list.InformationRightsManagementSettings.DocumentAccessExpireDays   = $DocumentAccessExpireDays
            }

        # Set group protection and credentials interval

            if($LicenseCacheExpireDays)
            {
                # Users must verify their credentials using this interval (days)
                $list.InformationRightsManagementSettings.EnableLicenseCacheExpire = $true
                $list.InformationRightsManagementSettings.LicenseCacheExpireDays   = $LicenseCacheExpireDays
            }

            if($GroupName)
            {
                # Allow group protection. Default group:
                $list.InformationRightsManagementSettings.EnableGroupProtection = $true
                $list.InformationRightsManagementSettings.GroupName             = $GroupName
            }
    }
    end
    {
        if($list)
        {
            Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
            $list.InformationRightsManagementSettings.Update()
            $list.Update()
            $script:clientContext.Load($list)
            $script:clientContext.ExecuteQuery()
        }
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }


# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use 
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        { 
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return 
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }


# connect to Office365 first, required for SharePoint Online cmdlets to run

    Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential


# enumerate each of the specified site URLs

    foreach($webUrl in $webUrls)
    {
        $grantedSiteCollectionAdmin = $false
        
        try
        {
            # establish the client context and set the credentials to connect to the site
            $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
            $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

            # initialize the site and web context
            $script:clientContext.Load($script:clientContext.Site)
            $script:clientContext.Load($script:clientContext.Web)
            $script:clientContext.ExecuteQuery()

            # load and ensure the tenant admin user account if present on the target SharePoint site
            $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
            $script:clientContext.Load($tenantAdminUser)
            $script:clientContext.ExecuteQuery()

            # check if the tenant admin is a site admin
            if( -not $tenantAdminUser.IsSiteAdmin ) 
            {
                try
                {
                    # grant the tenant admin temporary admin rights to the site collection
                    Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                    $grantedSiteCollectionAdmin = $true
                }
                catch
                {
                    Write-Error $_.Exception
                    return
                }
            }

            try
            {
                # load the list orlibrary using CSOM

                $list = $null
                $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                $script:clientContext.Load($list)
                $script:clientContext.ExecuteQuery()


                # **************  ADMIN INSTRUCTIONS  **************
                # If necessary, modify the following Set-IrmConfiguration parameters to match your required values 
                # The supplied options and values are for example only
                # Example that shows the Set-IrmConfiguration command with all parameters: Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users" -IrmReject -ProtectionExpirationDate $(Get-Date).AddDays(180) -DisableDocumentBrowserView -AllowPrint -AllowScript -AllowWriteCopy -LicenseCacheExpireDays 25 -DocumentAccessExpireDays 90

                Set-IrmConfiguration -List $list -PolicyTitle "Protected Files" -PolicyDescription "This policy restricts access to authorized users"  
            }
            catch
            {
                Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
            }
       }
       finally
       {
            if($grantedSiteCollectionAdmin)
            {
                # remove the temporary admin rights to the site collection
                Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
            }
       }
    }

Disconnect-SPOService -ErrorAction SilentlyContinue

</code></listItem><listItem><para>Review the script and make the following changes:</para><list class="ordered"><listItem><para>Search for <codeInline>$sharepointAdminCenterUrl</codeInline> and replace the example value with your own SharePoint admin center URL.</para><para>You'll find this value as the base URL when you go into the SharePoint admin center, and it has the following format: https://<placeholder>&lt;tenant_name&gt;</placeholder>-admin.sharepoint.com</para><para>For example, if the tenant name is "contoso", then you would specify: <userInput>https://contoso-admin.sharepoint.com</userInput></para></listItem><listItem><para>Search for <codeInline>$tenantAdmin</codeInline> and replace the example value with your own fully qualified global administrator account for Office 365.</para><para>This value is the same as the one you use to sign in to the Office 365 admin portal as the global administrator and has the following format: user_name@<placeholder>&lt;tenant domain name&gt;</placeholder>.com</para><para>For example, if the Office 365 global administrator user name is "admin" for the "contoso.com" tenant domain, you would specify: <userInput>admin@contoso.com</userInput></para></listItem><listItem><para>Search for <codeInline>$webUrls</codeInline> and replace the example values with your users' OneDrive for Business web URLs, adding or deleting as many entries as you need. </para><para>Alternatively, see the comments in the script about how to replace this array by importing a .CSV file that contains all the URLs you need to configure.  We've provided another sample script to automatically search for and extract the URLs to populate this .CSV file. When you're ready to do this, expand the <link xlink:href="#BKMK_Script_OD4B_URLS">Additional script to output all OneDrive for Business URLs to a .CSV file</link> section immediately after these steps. </para><para>The web URL for the user's OneDrive for Business is in the following format: https://<placeholder>&lt;tenant name&gt;</placeholder>-my.sharepoint.com/personal/<placeholder>&lt;user_name&gt;</placeholder>_<placeholder>&lt;tenant name&gt;</placeholder>_com</para><para>For example, if the user in the contoso tenant has a user name of "rsimone", you would specify: <userInput>https://contoso-my.sharepoint.com/personal/rsimone_contoso_com</userInput></para></listItem><listItem><para>Because we are using the script to configure OneDrive for Business, do not change the value of <system>Documents</system> for the <codeInline>$listTitle</codeInline> variable.</para></listItem><listItem><para>Search for <codeInline>ADMIN INSTRUCTIONS</codeInline>. If you make no changes to this section, the user's OneDrive for Business will be configured for IRM with the policy title of "Protected Files" and the description of "This policy restricts access to authorized users".  No other IRM options will be set, which is probably appropriate for most environments. However, you can change the suggested policy title and description, and also add any other IRM options that are appropriate for your environment. See the commented example in the script to help you construct your own set of parameters for the Set-IrmConfiguration command.</para></listItem></list></listItem><listItem><para>Save the script and sign it. If you do not sign the script (more secure), Windows PowerShell must be configured on your computer to run unsigned scripts. To do this, run a Windows PowerShell session with the <ui>Run as Administrator</ui> option, and type: <userInput>Set-ExecutionPolicy Unrestricted</userInput>. However, this configuration lets all unsigned scripts run (less secure). </para><para>For more information about signing Windows PowerShell scripts, see <externalLink><linkText>about_Signing</linkText><linkUri>https://technet.microsoft.com/library/hh847874.aspx</linkUri></externalLink> in the PowerShell documentation library.</para></listItem><listItem><para>Run the script and if prompted, supply the password for the Office 365 admin account. If you modify the script and run it in the same Windows PowerShell session, you won't be prompted for credentials.</para></listItem></list><alert class="tip">
 <para>You can also use this script to configure IRM for a SharePoint Online library. For this configuration, you will likely want to enable the additional option <ui>Do not allow users to upload documents that do not support IRM</ui>, to ensure that the library contains only protected documents.    To do that, add the <codeInline>-IrmReject</codeInline> parameter to the Set-IrmConfiguration command in the script.</para>
<para>You would also need to modify the <codeInline>$webUrls</codeInline> variable (for example, <userInput>https://contoso.sharepoint.com</userInput>) and  <codeInline>$listTitle</codeInline> variable (for example, <userInput>$Reports</userInput>).</para></alert><para>If you need to disable IRM for user's OneDrive for Business libraries, expand the <link xlink:href="#BKMK_Script_OD4B_DisableIRM">Script to disable IRM for OneDrive for Business</link> section.</para></content>
<sections><section expanded="false" address="BKMK_Script_OD4B_URLS">
<title>Additional script to output all OneDrive for Business URLs to a .CSV file</title><content><para>For step 4c above, you can use the following Windows PowerShell script to extract the URLs for all users' OneDrive for Business libraries, which you can then check, edit if necessary, and then import into the main script.</para><para>This script also requires the <externalLink><linkText>SharePoint Online Client Components SDK</linkText><linkUri>http://www.microsoft.com/en-us/download/details.aspx?id=42038</linkUri></externalLink> and the <externalLink><linkText>SharePoint Online Management Shell</linkText><linkUri>http://www.microsoft.com/en-us/download/details.aspx?id=35588</linkUri></externalLink>. Follow the same instructions to copy and paste it, save the file locally (for example, "Report-OneDriveForBusinessSiteInfo.ps1"), modify the   <codeInline>$sharepointAdminCenterUrl</codeInline> and <codeInline>$tenantAdmin</codeInline> values as before, and then run the script.</para><para><legacyItalic><embeddedLabel>Disclaimer</embeddedLabel></legacyItalic>: This sample script is not supported under any Microsoft standard support program or service. This sample script is provided AS IS without warranty of any kind.</para><code># Requires Windows PowerShell version 3

&lt;#
  Description:

    Queries the search service of an Office 365 tenant to retrieve all OneDrive for Business sites.  
    Details of the discovered sites are written to a .CSV file (by default,"OneDriveForBusinessSiteInfo_&lt;date&gt;.csv").


 Script Installation Requirements: 

   SharePoint Online Client Components SDK
   http://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   http://www.microsoft.com/en-us/download/details.aspx?id=35588

==============================================================
#&gt;

# URL will be in the format https://&lt;tenant-name&gt;-admin.sharepoint.com
$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.onmicrosoft.com"                           

$reportName = "OneDriveForBusinessSiteInfo_$((Get-Date).ToString("yyyy-MM-dd_hh.mm.ss")).csv"

$oneDriveForBusinessSiteUrls= @()
$resultsProcessed = 0


function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI 
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }


# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use 
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        { 
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return 
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }


# establish the client context and set the credentials to connect to the site

    $clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($sharepointAdminCenterUrl)
    $clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)


# run a query against the Office 365 tenant search service to retrieve all OneDrive for Business URLs

    do
    {
        # build the query object
	    $query = New-Object Microsoft.SharePoint.Client.Search.Query.KeywordQuery($clientContext)
	    $query.TrimDuplicates        = $false
	    $query.RowLimit              = 500
	    $query.QueryText             = "SPSiteUrl:'/personal/' AND contentclass:STS_Site"
	    $query.StartRow              = $resultsProcessed
	    $query.TotalRowsExactMinimum = 500000

        # run the query 
	    $searchExecutor = New-Object Microsoft.SharePoint.Client.Search.Query.SearchExecutor($clientContext)
	    $queryResults = $searchExecutor.ExecuteQuery($query)
	    $clientContext.ExecuteQuery()

        # enumerate the search results and store the site URLs
        $queryResults.Value[0].ResultRows | % {
            $oneDriveForBusinessSiteUrls += $_.Path
            $resultsProcessed++
        }
    }
    while($resultsProcessed -lt $queryResults.Value.TotalRows)

$oneDriveForBusinessSiteUrls | Out-File -FilePath $reportName
</code></content>
</section><section expanded="false" address="BKMK_Script_OD4B_DisableIRM">
<title>Script to disable IRM for OneDrive for Business</title><content><para>Use the following sample script if you need to disable IRM for users' OneDrive for Business.</para><para>This script also requires the <externalLink><linkText>SharePoint Online Client Components SDK</linkText><linkUri>http://www.microsoft.com/en-us/download/details.aspx?id=42038</linkUri></externalLink> and the <externalLink><linkText>SharePoint Online Management Shell</linkText><linkUri>http://www.microsoft.com/en-us/download/details.aspx?id=35588</linkUri></externalLink>. Copy and paste the contents, save the file locally (for example, "Disable-IRMOnOneDriveForBusiness.ps1"), and modify the   <codeInline>$sharepointAdminCenterUrl</codeInline> and <codeInline>$tenantAdmin</codeInline> values. Manually specify the OneDrive for Business URLs or use the script in the previous section so that you can import these, and then run the script.</para><para><legacyItalic><embeddedLabel>Disclaimer</embeddedLabel></legacyItalic>: This sample script is not supported under any Microsoft standard support program or service. This sample script is provided AS IS without warranty of any kind.</para><code># Requires Windows PowerShell version 3

&lt;#
  Description:

    Disables IRM for OneDrive for Business and can also be used for SharePoint Online libraries and lists

 Script Installation Requirements: 

   SharePoint Online Client Components SDK
   http://www.microsoft.com/en-us/download/details.aspx?id=42038

   SharePoint Online Management Shell
   http://www.microsoft.com/en-us/download/details.aspx?id=35588

==============================================================
#&gt;

$sharepointAdminCenterUrl = "https://contoso-admin.sharepoint.com"

$tenantAdmin = "admin@contoso.com"

$webUrls = @("https://contoso-my.sharepoint.com/personal/user1_contoso_com",
             "https://contoso-my.sharepoint.com/personal/user2_contoso_com",
             "https://contoso-my.sharepoint.com/personal/person3_contoso_com")

            
&lt;# As an alternative to specifying the URLs as an array, you can import them from a CSV file (no header, single value per row). 
   Then, use: $webUrls = Get-Content -Path "File_path_and_name.csv"

#&gt;

$listTitle = "Documents"

function Load-SharePointOnlineClientComponentAssemblies
{
    [cmdletbinding()]
    param()

    process
    {
        # assembly location: C:\Program Files\Common Files\microsoft shared\Web Server Extensions\16\ISAPI 
        try
        {
            Write-Verbose "Loading Assembly: Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.Policy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.Office.Client.TranslationServices, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.DocumentManagement, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Publishing, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Runtime, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search.Applications, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Search, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.Taxonomy, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            Write-Verbose "Loading Assembly: Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c"
            [System.Reflection.Assembly]::Load("Microsoft.SharePoint.Client.UserProfiles, Version=16.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c") | Out-Null

            return $true
        }
        catch
        {
            if($_.Exception.Message -match "Could not load file or assembly")
            {
                Write-Error -Message "Unable to load the SharePoint Server 2013 Client Components.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=42038"
            }
            else
            {
                Write-Error -Exception $_.Exception
            }
            return $false
        }
    }
}

function Load-SharePointOnlineModule
{
    [cmdletbinding()]
    param()

    process
    {
        do
        {
            # Installation location: C:\Program Files\SharePoint Online Management Shell\Microsoft.Online.SharePoint.PowerShell
            $spoModule = Get-Module -Name Microsoft.Online.SharePoint.PowerShell -ErrorAction SilentlyContinue

            if(-not $spoModule)
            {
                try
                {
                    Import-Module Microsoft.Online.SharePoint.PowerShell -DisableNameChecking
                    return $true
                }
                catch
                {
                    if($_.Exception.Message -match "Could not load file or assembly")
                    {
                        Write-Error -Message "Unable to load the SharePoint Online Management Shell.`nDownload Location: http://www.microsoft.com/en-us/download/details.aspx?id=35588"
                    }
                    else
                    {
                        Write-Error -Exception $_.Exception
                    }
                    return $false
                }
            }
            else
            {
                return $true
            }
        }
        while(-not $spoModule)
    }
}

function Remove-IrmConfiguration
{
    [cmdletbinding()]
    param(
        [parameter(Mandatory=$true)][Microsoft.SharePoint.Client.List]$List
    )

    process
    {
        Write-Verbose "Disabling IRM Configuration on '$($List.Title)'"
     
        $List.IrmEnabled = $false
        $List.IrmExpire  = $false
        $List.IrmReject  = $false
        $List.InformationRightsManagementSettings.Reset()
    }
    end
    {
        if($List)
        {
            Write-Verbose "Committing IRM configuration settings on '$($list.Title)'"
            $list.InformationRightsManagementSettings.Update()
            $list.Update()
            $script:clientContext.Load($list)
            $script:clientContext.ExecuteQuery()
        }
    }
} 


function Get-CredentialFromCredentialCache
{
    [cmdletbinding()]
    param([string]$CredentialName)

    #if( Test-Path variable:\global:CredentialCache )
    if( Get-Variable O365TenantAdminCredentialCache -Scope Global -ErrorAction SilentlyContinue )
    {
        if($global:O365TenantAdminCredentialCache.ContainsKey($CredentialName))
        {
            Write-Verbose "Credential Cache Hit: $CredentialName"
            return $global:O365TenantAdminCredentialCache[$CredentialName]
        }
    }
    Write-Verbose "Credential Cache Miss: $CredentialName"
    return $null
}

function Add-CredentialToCredentialCache
{
    [cmdletbinding()]
    param([System.Management.Automation.PSCredential]$Credential)

    if(-not (Get-Variable CredentialCache -Scope Global -ErrorAction SilentlyContinue))
    {
        Write-Verbose "Initializing the Credential Cache"
        $global:O365TenantAdminCredentialCache = @{}
    }

    Write-Verbose "Adding Credential to the Credential Cache"
    $global:O365TenantAdminCredentialCache[$Credential.UserName] = $Credential
}

# load the required assemblies and Windows PowerShell modules

    if(-not ((Load-SharePointOnlineClientComponentAssemblies) -and (Load-SharePointOnlineModule)) ) { return }


# Add the credentials to the client context and SharePoint Online service connection

    # check for cached credentials to use 
    $o365TenantAdminCredential = Get-CredentialFromCredentialCache -CredentialName $tenantAdmin

    if(-not $o365TenantAdminCredential)
    {
        # when credentials are not cached, prompt for the tenant admin credentials
        $o365TenantAdminCredential = Get-Credential -UserName $tenantAdmin -Message "Enter the password for the Office 365 admin"

        if(-not $o365TenantAdminCredential -or -not $o365TenantAdminCredential.UserName -or $o365TenantAdminCredential.Password.Length -eq 0 )
        { 
            Write-Error -Message "Could not validate the supplied tenant admin credentials"
            return 
        }

        # add the credentials to the cache
        Add-CredentialToCredentialCache -Credential $o365TenantAdminCredential
    }


# connect to Office365 first, required for SharePoint Online cmdlets to run

    Connect-SPOService -Url $sharepointAdminCenterUrl -Credential $o365TenantAdminCredential


# enumerate each of the specified site URLs

    foreach($webUrl in $webUrls)
    {
        $grantedSiteCollectionAdmin = $false
        
        try
        {
            # establish the client context and set the credentials to connect to the site
            $script:clientContext = New-Object Microsoft.SharePoint.Client.ClientContext($webUrl)
            $script:clientContext.Credentials = New-Object Microsoft.SharePoint.Client.SharePointOnlineCredentials($o365TenantAdminCredential.UserName, $o365TenantAdminCredential.Password)

            # initialize the site and web context
            $script:clientContext.Load($script:clientContext.Site)
            $script:clientContext.Load($script:clientContext.Web)
            $script:clientContext.ExecuteQuery()

            # load and ensure the tenant admin user account if present on the target SharePoint site
            $tenantAdminUser = $script:clientContext.Web.EnsureUser($o365TenantAdminCredential.UserName)
            $script:clientContext.Load($tenantAdminUser)
            $script:clientContext.ExecuteQuery()

            # check if the tenant admin is a site admin
            if( -not $tenantAdminUser.IsSiteAdmin ) 
            {
                try
                {
                    # grant the tenant admin temporary admin rights to the site collection
                    Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $true | Out-Null
                    $grantedSiteCollectionAdmin = $true
                }
                catch
                {
                    Write-Error $_.Exception
                    return
                }
            }

            try
            {
                # load the list orlibrary using CSOM

                $list = $null
                $list = $script:clientContext.Web.Lists.GetByTitle($listTitle)
                $script:clientContext.Load($list)
                $script:clientContext.ExecuteQuery()

               Remove-IrmConfiguration -List $list                 
            }
            catch
            {
                Write-Error -Message "Error setting IRM configuration on site: $webUrl.`nError Details: $($_.Exception.ToString())"
            }
       }
       finally
       {
            if($grantedSiteCollectionAdmin)
            {
                # remove the temporary admin rights to the site collection
                Set-SPOUser -Site $script:clientContext.Site.Url -LoginName $o365TenantAdminCredential.UserName -IsSiteCollectionAdmin $false | Out-Null
            }
       }
    }

Disconnect-SPOService -ErrorAction SilentlyContinue
</code></content>
</section></sections></section></sections></section></sections></section>
    </sections>
  </section>
  <section address="BKMK_Office2013Configuration">
    <title>Office 2016 and Office 2013: Configuration for clients</title>
    <content>
      <para>Because these later versions of Office  natively support Azure RMS, no client computer configuration is required to support the information rights management (IRM) features for applications such as Word, Excel, PowerPoint, Outlook and the Outlook Web App. All users have to do is sign in to their Office applications with their <token>o365_1</token> credentials and they can protect files and emails, and use files and emails that have been protected by others. </para>
      <para>However, we recommend that you supplement these applications with the Rights Management sharing application, so that users get the benefit of the Office add-in. For more information, see the <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_SharingApp">Rights Management sharing application: Installation and configuration for clients</link> section in this topic.</para>
    </content>
  </section>
  <section address="BKMK_Office2010Configuration">
    <title>Office 2010: Configuration for clients</title>
    <content>
      <para>For client computers to use Azure RMS with Office 2010, they must have installed the Rights Management sharing application for Windows. No further configuration is required other than users must sign in with their <token>o365_1</token> credentials and they can then protect files and use files that have been protected by others.</para>
      <para>For more information about the Rights Management sharing application, see the <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_SharingApp">Rights Management sharing application: Installation and configuration for clients</link> section in this topic.</para>
    </content>
  </section>
  <section address="BKMK_SharingApp">
    <title>Rights Management sharing application: Installation and configuration for clients</title>
    <content>
      <para>The Rights Management (RMS) sharing application is required for client computers to use Azure RMS with Office 2010, and recommended for all computers and mobile devices that support Azure RMS. The RMS sharing application integrates with Office applications by installing an Office add-in so that users can easily protect files and emails directly from the ribbon. It also offers generic protection for files types that are not natively supported by Azure RMS, and a document tracking site for users to track and revoke files that they have protected.</para>
    </content>
    <sections>
      <section address="BKMK_SharingAppforWindows" expanded="false">
        <title>The RMS sharing application for Windows: Installation and configuration</title>
        <content>
          <para>To install and configure the RMS sharing application for Windows for an enterprise deployment, see the <externalLink><linkText>Rights Management sharing application administrator guide</linkText><linkUri>http://technet.microsoft.com/library/dn339003.aspx</linkUri></externalLink>. </para>
          <alert class="tip">
            <para>If you want to quickly install and test the RMS sharing application for a single computer, see <externalLink><linkText>Download and install the Rights Management sharing application</linkText><linkUri>http://technet.microsoft.com/library/dn574734.aspx</linkUri></externalLink> from the <externalLink><linkText>Rights Management sharing application user guide</linkText><linkUri>http://technet.microsoft.com/library/dn339006.aspx</linkUri></externalLink>.</para>
          </alert>
        </content>
      </section>
      <section address="BKMK_SharingAppMovileDevices" expanded="false">
        <title>The RMS sharing application for mobile platforms: Installation</title>
        <content>
          <para>To install the RMS sharing application for mobile platforms, you can download the relevant app by using the links on the <externalLink><linkText>Microsoft Rights Management page</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=303970</linkUri></externalLink>. No configuration is required to use Azure RMS with this app.</para>
          <?xm-deletion_mark author="" time="20150617T153301-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Alternatively, if you manage mobile devices by using Microsoft Intune, you can deploy the RMS sharing app for iOS and Android as a &lt;maml:legacyBold&gt;policy managed app&lt;/maml:legacyBold&gt;, because it has the Microsoft Intune App Software Development Kit built in. For more information and instructions, see &lt;maml:externalLink&gt;&lt;maml:linkText&gt;Control apps using mobile application management policies with Microsoft Intune&lt;/maml:linkText&gt;&lt;maml:linkUri&gt;https://technet.microsoft.com/library/dn878026.aspx&lt;/maml:linkUri&gt;&lt;/maml:externalLink&gt; in the Microsoft Intune TechNet library, and in Step 2, use the instructions to publish a policy managed app.. &lt;/maml:para&gt;
        "?></content>
      </section>
    </sections>
  </section>
  <section address="BKMK_RMSAPIs">
    <title>Other applications that support the RMS APIs: Installation and configuration</title>
    <content>
      <para>This category includes line-of-business applications that are written in-house by using the RMS SDK, and applications from software vendors that are written by using the RMS SDK. For these applications, follow the instructions that are provided with the application.</para>
    </content>
  </section>
  <section>
    <title>Next steps</title>
    <content>
      <para>After you’ve configured your applications to support Azure Rights Management, use the <link xlink:href="086600c2-c5d8-47ec-a4c0-c782e1797486">Azure Rights Management Deployment Roadmap</link> to check whether there are other configuration steps that you might want to do before you roll out <token>aad_rightsmanagement_1</token> to users and administrators. If not, see <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using Azure Rights Management</link> for your next steps.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring rights management</link>
  </relatedTopics>
</developerConceptualDocument>
