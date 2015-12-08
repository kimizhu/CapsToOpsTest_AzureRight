---
description: na
search: na
title: Deploying the Azure Rights Management Connector
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 2015-11-01
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# Deploying the Azure Rights Management Connector
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use this information to learn about the Microsoft Rights Management (RMS) connector and how you can use it to provide information protection with existing on-premises deployments that use Microsoft Exchange Server, Microsoft SharePoint Server, or file servers that run Windows Server and use the File Classification Infrastructure (FCI) capability of File Server Resource Manager.</para>
    <alert class="tip">
      <para>For a high-level example scenario with screenshots, see the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Example_FCI">Automatically protecting files on file servers running Windows Server and File Classification Infrastructure</link> section in the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link> topic.</para>
    </alert>
  </introduction>
  <section address="OverviewConnector">
    <title>Overview of the Microsoft Rights Management connector</title>
    <content>
      <para>The Microsoft Rights Management (RMS) connector lets you quickly enable existing on-premises servers to use their Information Rights Management (IRM) functionality with the cloud-based Microsoft Rights Management service (Azure RMS). With this functionality, IT and users can easily protect documents and pictures both inside your organization and outside, without having to install additional infrastructure or establish trust relationships with other organizations. You can use this connector even if some of your users are connecting to online services, in a hybrid scenario. For example, some users' mailboxes use Exchange Online and some users' mailboxes use Exchange Server. After you install the RMS connector, all users can protect and consume emails and attachments by using Azure RMS, and information protection works seamlessly between the two deployment configurations. </para>
      <para>The RMS connector is a small-footprint service that you install on-premises, on servers that run Windows Server 2012 R2, Windows Server 2012, or Windows Server 2008 R2. In addition to running the connector on physical computers, you can also run it on virtual machines, including Azure IaaS VMs. After you install and configure the connector, it acts as a communications interface (a relay) between the on-premises servers and the cloud service. </para>
      <para>If you manage your own tenant key for Azure RMS (the bring you own key, or BYOK scenario), the RMS connector and the on-premises servers that use it do not access the hardware security module (HSM) that contains your tenant key. This is because all cryptographic operations that use the tenant key are performed in Azure RMS, and not on-premises.</para>
      <mediaLink>
        <image xlink:href="fca243be-b886-43ad-91e6-6900f7e2cd85"/>
      </mediaLink>
      <para/>
      <para/>
      <para>The RMS connector supports the following on-premises servers: Exchange Server, SharePoint Server, and file servers that run Windows Server and use File Classification Infrastructure to classify and apply policies to Office documents in a folder. If you want to protect all files types using File Classification, do not use the RMS connector, but instead, use the <externalLink><linkText>RMS Protection cmdlets</linkText><linkUri>https://msdn.microsoft.com/library/azure/mt433195.aspx</linkUri></externalLink>.</para>
      <alert class="note">
        <para>For supported versions of these on-premises servers, see “On-premises servers that support Azure RMS” in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedApplications">Applications that support Azure RMS</link> section of the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic.</para>
      </alert>
      <para>Use the following sections to help you plan for, install, and configure the RMS connector. You must then do some post installation configuration so that your servers can use the connector.</para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_Prereqs">Prerequisites for the RMS connector</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Step 1: </embeddedLabel><link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_InstallingConnector">Installing the RMS connector</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Step 2: </embeddedLabel><link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#EnteringCredentials">Entering credentials</link></para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Step 3: </embeddedLabel><link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#AuthorizingServers">Authorizing servers to use the RMS connector</link></para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Step 4: </embeddedLabel><link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#ConfiguringConnector">Configuring load balancing and high availability</link></para>
        </listItem>
        <listItem>
          <para>Optional: <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_ConfiguringHTTPS">Configuring the RMS connector to use HTTPS</link></para>
        </listItem>
        <listItem>
          <para>Optional: <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_ConfiguringWebProxy">Configuring the RMS connector for a web proxy server</link></para>
        </listItem>
        <listItem>
          <para>Optional: <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_InstallingStandaloneTool">Installing the RMS connector administration tool on administrative computers</link></para>
        </listItem>
        <listItem>
          <para>
            <embeddedLabel>Step 5: </embeddedLabel><link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#ConfiguringServers">Configuring servers to use the RMS connector</link></para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_ExchangeServer">Configuring an Exchange server to use the connector</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_ConfiguringSharePoint">Configuring a SharePoint server to use the connector</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_FileServer">Configuring a file server for File Classification Infrastructure to use the connector</link>
              </para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_NextSteps">Next steps</link>
          </para>
        </listItem>
      </list>
    </content>
  </section>
  <section address="BKMK_Prereqs">
    <title>Prerequisites for the RMS connector</title>
    <content>
      <para>Before you install the RMS connector, make sure that the following requirements are in place.</para>
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
              <para>The Rights Management (RMS) service is activated</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214">Activating Azure Rights Management</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Directory synchronization between your Active Directory forests and Azure Active Directory</para>
            </TD>
            <TD>
              <para>After RMS is activated, Azure Active Directory must be configured to work with the users and groups in your Active Directory database. </para>
              <alert class="important">
                <para>You must do this directory synchronization step for the RMS connector to work, even for a test network. Although you can use Office 365 and Azure Active Directory by using accounts that you manually create in Azure Active Directory, this connector requires that the accounts in Azure Active Directory are synchronized with Active Directory Domain Services; manual password synchronization is not sufficient.</para>
              </alert>
              <para>For more information, see the following resources:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Instructions for configuring your Azure AD tenant</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh967611.aspx</linkUri>
                    </externalLink>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <externalLink>
                      <linkText>Instructions for enabling directory synchronization with AAD using DirSync</linkText>
                      <linkUri>http://technet.microsoft.com/library/hh967642.aspx</linkUri>
                    </externalLink>
                    <br/>
                  </para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Optional but recommended: </para>
              <list class="bullet">
                <listItem>
                  <para>Enable federation between your on-premises Active Directory and Azure Active Directory  </para>
                </listItem>
              </list>
            </TD>
            <TD>
              <para>You can enable identity federation between your on-premises directory and Azure Active Directory. This configuration enables a more seamless user experience by using single sign-on to the RMS service. Without single sign on, users are prompted for their credentials before they can use rights-protected content. </para>
              <para>For instructions to configure federation by using Active Directory Federation Services (AD FS) between Active Directory Domain Services and Azure Active Directory, see the <externalLink><linkText>Checklist: Use AD FS to implement and manage single sign-on</linkText><linkUri>http://technet.microsoft.com/library/jj205462.aspx</linkUri></externalLink> in the Windows Server library.  </para>
              
            </TD>
          </tr>
          <tr>
            <TD>
              <para>A minimum of two member computers on which to install the RMS connector:</para>
              <list class="bullet">
                <listItem>
                  <para>A 64-bit physical or virtual computer running one of the following operating systems: </para>
                  <list class="bullet">
                    <listItem>
                      <para>Windows Server 2012 R2</para>
                    </listItem>
                    <listItem>
                      <para>Windows Server 2012</para>
                    </listItem>
                    <listItem>
                      <para>Windows Server 2008 R2</para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>At least 1 GB of RAM</para>
                </listItem>
                <listItem>
                  <para>A minimum of 64 GB of disk space</para>
                </listItem>
                <listItem>
                  <para>At least one network interface</para>
                </listItem>
                <listItem>
                  <para>Access to the Internet via a firewall (or web proxy) that does not require authentication</para>
                </listItem>
                <listItem>
                  <para>Must be in a forest or domain that trusts other forests in the organization that contain installations of Exchange or SharePoint servers that you want to use with the RMS connector</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <para>For fault tolerance and high availability, you must install the RMS connector on a minimum of two computers.</para>
              <alert class="tip">
                <para>If you are using Outlook Web Access or mobile devices that use Exchange ActiveSync IRM and it is critical that you maintain access to emails and attachments that are protected by Azure RMS, we recommend that you deploy a load-balanced group of connector servers to ensure high availability.</para>
              </alert>
              <?Comment CB: 252104 2014-04-26T11:24:00Z  Id='0?>
              <para>You do not need dedicated servers to run the connector but you must install it on a separate computer from the servers that will use the connector. <?CommentEnd Id='0'
    ?></para>
              <alert class="important">
                <para>Do not install the connector on a computer that runs Exchange Server, SharePoint Server, or a file server that is configured for file classification infrastructure if you want to use the functionality from these services with Azure RMS. Also, do not install this connector on a domain controller.</para>
              </alert>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section address="BKMK_InstallingConnector">
    <title>Installing the RMS connector</title>
    <content>
      <para>After you have confirmed the prerequisites in the preceding section, use the following instructions to install the RMS connector:</para>
      <list class="ordered">
        <listItem>
          <para>Identify the computers (minimum of two) that will run the RMS connector. They must meet the minimum specification listed in the preceding section. </para>
          <alert class="note">
            <para>You will install a single RMS connector (consisting of multiple servers for high availability) per tenant (Office 365 tenant or Azure AD tenant). Unlike Active Directory RMS, you do not have to install an RMS connector in each forest.</para>
          </alert>
        </listItem>
        <listItem>
          <para>Download the source files for the RMS connector from the <externalLink><linkText>Microsoft Download Center</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=314106</linkUri></externalLink>. </para>
          <para>To install the RMS connector, download RMSConnectorSetup.exe. </para>
          <para>In addition:</para>
          <list class="bullet">
            <listItem>
              <para>If you later want to configure the connector from a 32-bit computer, also download RMSConnectorAdminToolSetup_x86.exe.</para>
            </listItem>
            <listItem>
              <para>If you want to use the server configuration tool for the RMS connector, to automate the configuration of registry settings on you on-premises servers, also download GenConnectorConfig.ps1.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>On the computer on which you want to install the RMS connector, run <legacyBold>RMSConnectorSetup.exe</legacyBold> with Administrator privileges.  </para>
        </listItem>
        <listItem>
          <para>On the Welcome page of the Microsoft Rights Management Connector Setup page, select <ui>Install Microsoft Rights Management connector on the computer</ui>, and then click <ui>Next</ui>.</para>
        </listItem>
        <listItem>
          <para>Read and agree to the RMS connector license terms, and then click <legacyBold>Next</legacyBold>.</para>
        </listItem>
      </list>
      <para>To continue, enter an account and password to configure the RMS connector.</para>
    </content>
  </section>
  <section address="EnteringCredentials">
    <title>Entering credentials</title>
    <content>
      <para>Before you can configure the RMS connector, you must enter credentials for an account that has sufficient privileges to configure the RMS connector. </para>
      <para>In addition, if you have implemented <externalLink><linkText>onboarding controls</linkText><linkUri>https://technet.microsoft.com/library/jj658941.aspx#BKMK_OnboardingControls</linkUri></externalLink>, make sure that the account you specify is able to protect content. For example, if you restricted the ability to protect content to the “IT department” group, the account that you specify here must be a member of that group. If not, you will see the error message: <ui>The attempt to discover the location of the administration service and organization failed. Make sure Microsoft Rights Management service is enabled for your organization.</ui></para>
      <para>You can use an account that has one of the following privileges:</para>
      <list class="bullet">
        <listItem>
          <para>
            <legacyBold>Office 365 tenant administrator</legacyBold>: An account that is a global admin for your Office 365 tenant.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold> Azure Rights Management global administrator</legacyBold>: An account with administrator privileges for the Azure RMS tenant.</para>
        </listItem>
        <listItem>
          <para>
            <legacyBold>Microsoft RMS connector Administrator</legacyBold>: An account in Azure Active Directory that has been granted rights to install and administer the RMS connector for your organization.</para>
          <para/>
          <alert class="note">
            <para>If you want to use the Microsoft RMS connector Administrator account, you must first do the following to assign the RMS connector administrator role:</para>
            <list class="ordered">
              <listItem>
                <para>On the same computer, download and install Windows PowerShell for Rights Management. For more information, see <link xlink:href="0d665ed6-b1de-4d63-854a-bc57c1c49844">Installing Windows PowerShell for Azure Rights Management</link>.</para>
                <para>Start Windows PowerShell with the <ui>Run as administrator</ui> command, and connect to the Azure RMS service by using the <externalLink><linkText>Connect-AadrmService</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629415.aspx</linkUri></externalLink> command: </para>
                <code>Connect-AadrmService                   //provide Office 365 tenant administrator or Azure RMS global administrator credentials</code>
              </listItem>
              <listItem>
                <para>Then run the <externalLink><linkText>Add-AadrmRoleBasedAdministrator</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629417.aspx</linkUri></externalLink> command, using just one of the following parameters:   </para>
                <code>Add-AadrmRoleBasedAdministrator -EmailAddress &lt;email address&gt; -Role "ConnectorAdministrator"</code>
                <code>Add-AadrmRoleBasedAdministrator -ObjectId &lt;object id&gt; -Role "ConnectorAdministrator"</code>
                <code>Add-AadrmRoleBasedAdministrator -SecurityGroupDisplayName &lt;group Name&gt; -Role "ConnectorAdministrator"</code>
                <para>For example, type: <userInput>Add-AadrmRoleBasedAdministrator -EmailAddress melisa@contoso.com -Role " ConnectorAdministrator "</userInput></para>
                <para>Although these commands use the ConnectorAdministrator role, you could also use the GlobalAdministrator role here, as well.</para>
              </listItem>
            </list>
          </alert>
        </listItem>
      </list>
      <para>During the RMS connector installation process, all prerequisite software is validated and installed, Internet Information Services (IIS) is installed if not already present, and the connector software is installed and configured. In addition, Azure RMS is <?Comment CB: The UI talks about accounts in Active Directory &amp; granting them rights – what accounts, what rights? 2014-04-26T11:24:00Z  Id='2?>prepared for configuration by creating the following<?CommentEnd Id='2'
    ?>:  </para>
      <list class="bullet">
        <listItem>
          <para>An empty table of servers that are authorized to use the connector to communicate with Azure RMS. You will add servers to this table later.</para>
        </listItem>
        <listItem>
          <para>A set of security tokens for the connector, which authorize operations with Azure RMS. These tokens are downloaded from Azure RMS and installed on the local computer in the registry. They are protected by using the data protection application programming interface (DPAPI) and the Local System account credentials.</para>
        </listItem>
      </list>
      <para>On the final page of the wizard, do the following, and then click <ui>Finish</ui>:</para>
      <list class="bullet">
        <listItem>
          <para>If this is the first connector that you have installed, do not select <ui>Launch connector administrator console to authorize servers</ui> at this time. You will select this option after you have installed your second (or final) RMS connector. Instead, run the wizard again on at least one other computer. You must install a minimum of two connectors.</para>
        </listItem>
        <listItem>
          <para>If you have installed your second (or final) connector, select <ui>Launch connector administrator console to authorize servers</ui>. </para>
        </listItem>
      </list>
      <alert class="tip">
        <para>At this point, there is a verification test that you can perform to test whether the web services for the RMS connector are operational: </para>
        <list class="bullet">
          <listItem>
            <para>From a web browser, connect to <userInput>http://&lt;connectoraddress&gt;/_wmcs/certification/servercertification.asmx</userInput>, replacing <placeholder>&lt;connectoraddress&gt;</placeholder> with the server address or name that has the RMS connector installed. A successful connection displays a <ui>ServerCertificationWebService</ui> page.</para>
          </listItem>
        </list>
      </alert>
      <para>If you need to uninstall the RMS connector, run the wizard again and select the uninstall option.</para>
    </content>
  </section>
  <section address="AuthorizingServers">
    <title>Authorizing servers to use the RMS connector</title>
    <content>
      <para>When you have installed the RMS connector on at least two computers, you are ready to authorize the servers and services that you want to use the RMS connector. For example, servers running Exchange Server 2013 or SharePoint Server 2013.</para>
      <para>To define these servers, run the RMS connector administration tool and add entries to the list of allowed servers. You can run this tool when you select <ui>Launch connector administration console to authorize servers</ui> at the end of the Microsoft Rights Management connector Setup wizard, or you can run it separately from the wizard.</para>
      <para>When you authorize these servers, be aware of the following considerations:</para>
      <list class="bullet">
        <listItem>
          <para>Servers that you add will be granted special privileges. All accounts that you specify for the Exchange Server role in the connector configuration will be granted the <externalLink><linkText>super user role</linkText><linkUri>https://technet.microsoft.com/library/mt147272.aspx</linkUri></externalLink> in Azure RMS, which gives them access to all content for this RMS tenant. The super user feature is automatically enabled at this point, if necessary. To avoid the security risk of elevation of privileges, be careful to specify only the accounts that are used by your organization’s Exchange servers. All servers configured as SharePoint servers or file servers that use FCI will be granted regular user privileges. </para>
        </listItem>
        <listItem>
          <para>You can add multiple servers as a single entry by specifying an Active Directory security or distribution group, or a service account that is used by more than one server. When you use this configuration, the group of servers will share the same RMS certificates and will all be considered owners for content that any of them have protected. To minimize administrative overheads, we recommend that you use this configuration of a single group rather than individual servers to authorize your organization’s Exchange servers or a SharePoint server farm.</para>
        </listItem>
      </list>
      <para>On the <ui>Servers allowed to utilize the connector</ui> page, click <ui>Add</ui>.</para>
    </content>
    <sections>
      <section address="BKMK_AddServer">
        <title>Add a server to the list of allowed servers</title>
        <content>
          <para>On the <ui>Allow a server to utilize the connector</ui> page, enter the name of the object, or browse to identify the object to authorize. </para>
          <para>It is important that you authorize the correct object. For a server to use the connector, the account that runs the on-premises service (for example, Exchange or SharePoint) must be selected for authorization. For example, if the service is running as a configured service account, add the name of that service account to the list. If the service is running as Local System, add the name of the computer object (for example, SERVERNAME$). As a best practice, create a group that contains these accounts and specify the group instead of individual server names.</para>
          <para>More information about the different server roles:</para>
          <list class="bullet">
            <listItem>
              <para>For servers that run Exchange: You must specify a security group and you can use the default group (<ui>Exchange Servers</ui>) that Exchange automatically creates and maintains of all Exchange servers in the forest. </para>
            </listItem>
            <listItem>
              <para>For servers that run SharePoint: </para>
              <list class="bullet"><listItem><para>If a SharePoint 2010 server is configured to run as Local System (it's not using a service account), manually create a security group in Active Directory Domain Services, and add the computer name object for the server in this configuration to this group.</para></listItem><listItem><para>If a SharePoint server is configured to use a service account (the recommended practice for SharePoint 2010 and the only option for SharePoint 2013), do the following:</para><list class="ordered">
                <listItem>
                  <para>Add the service account that runs the SharePoint Central Administration service to enable SharePoint to be configured from its <?Comment CB: ? 2014-04-26T11:24:00Z  Id='41?>administrator console<?CommentEnd Id='41'
    ?>.</para>
                </listItem>
                <listItem>
                  <para>Add the account that is configured for the SharePoint App Pool.</para>
                </listItem>
              </list><alert class="tip">
                <para>If these two accounts are different, consider creating a single group that contains both accounts to minimize the administrative overheads.   </para>
              </alert></listItem></list>
              
            </listItem>
            <listItem>
              <para>For file servers that use File Classification Infrastructure, the associated services run as the Local System account, so you must authorize the computer account for the file servers (for example, SERVERNAME$) or a group that contains those computer accounts.</para>
            </listItem>
          </list>
          <para>When you have finished adding servers to the list, click <ui>Close</ui>. </para>
          <para>If you haven’t already done so, you must now configure load balancing for the servers that have the RMS connector installed, and consider whether to use HTTPS for the connections between these servers and the servers that you have just authorized.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="ConfiguringConnector">
    <title>Configuring load balancing and high availability</title>
    <content>
      <para>After you have installed the second or final instance of the RMS connector, define a connector URL server name and configure a load balancing system.</para>
      <para>The connector URL server name can be any name under a namespace that you control. For example, you could create an entry in your DNS system for <userInput>rmsconnector.contoso.com</userInput> and configure this entry to use an IP address in your load balancing system. There are no special requirements for this name and it doesn’t need to be configured on the connector servers themselves. Unless your Exchange and SharePoint servers are going to be communicating with the connector over the Internet, this name doesn’t have to resolve on the Internet. </para>
      <alert class="important">
        <para>We recommend that you don’t change this name after you have configured Exchange or SharePoint servers to use the connector, because you have to then clear these servers of all IRM configurations and then reconfigure them.</para>
      </alert>
      <para>After the name is created in DNS and is configured for an IP address, configure load balancing for that address, which directs traffic to the connector servers. You can use any IP-based load balancer for this purpose, which includes  the Network Load Balancing (NLB) feature in Windows Server. For more information, see <externalLink><linkText>Load Balancing Deployment Guide</linkText><linkUri>http://technet.microsoft.com/library/cc754833(v=WS.10).aspx</linkUri></externalLink>. </para>
      <para>Use the following settings to configure the NLB cluster:</para>
      <list class="bullet">
        <listItem>
          <para>Ports: 80 (for HTTP) or 443 (for HTTPS)</para>
          <para>For more information about whether to use HTTP or HTTPS, see the next section.</para>
        </listItem>
        <listItem>
          <para>Affinity: None</para>
        </listItem>
        <listItem>
          <para>Distribution method: Equal</para>
        </listItem>
      </list>
      <para>This name that you define for the load-balanced system (for the servers running the RMS connector service) is your organization’s RMS connector name that you will use later, when you configure the on-premises servers to use Azure RMS.  </para>
    </content>
  </section>
  <section address="BKMK_ConfiguringHTTPS">
    <title>Configuring the RMS connector to use HTTPS</title>
    <content>
      <alert class="note">
        <para>This configuration step is optional, but recommended for additional security.</para>
      </alert>
      <para>Although the use of TLS or SSL is optional for the RMS connector, we recommend it for any HTTP-based security-sensitive service. This configuration authenticates the servers running the connector to your Exchange and SharePoint servers that use the connector. In addition, all data that is sent from these servers to the connector is encrypted.</para>
      <para>To enable the RMS connector to use TLS, on each server that runs the RMS connector, install a server authentication certificate that contains the name that you will use for the connector. For example, if your RMS connector name that you defined in DNS is <system>rmsconnector.contoso.com</system>, deploy a server authentication certificate that contains <system>rmsconnector.contoso.com</system> in the certificate subject as the common name. Or, specify <system>rmsconnector.contoso.com</system> in the certificate alternative name as the DNS value. The certificate does not have to include the name of the server. Then in IIS, bind this certificate to the Default Web Site. </para>
      <para>If you use the HTTPS option, ensure that all servers that run the connector have a valid server authentication certificate that chains to a root CA that your Exchange and SharePoint servers trust. In addition, if the certification authority (CA) that issued the certificates for the connector servers publishes a certificate revocation list (CRL), the Exchange and SharePoint servers must be able to download this CRL.</para>
      <alert class="tip">
        <para>You can use the following information and resources to help you request and install a server authentication certificate, and to bind this certificate to the Default Web Site in IIS:</para>
        <list class="bullet">
          <listItem>
            <para>If you use Active Directory Certificate Services (AD CS) and an enterprise certification authority (CA) to deploy these server authentication certificates, you can duplicate and then use the Web Server certificate template. This certificate template uses <ui>Supplied in the request</ui> for the certificate subject name, which means that you can provide the FQDN of the RMS connector name for the certificate subject name or subject alternative name when you request the certificate. </para>
          </listItem>
          <listItem>
            <para>If you use a stand-alone CA or purchase this certificate from another company, see <externalLink><linkText>Configuring Internet Server Certificates (IIS 7)</linkText><linkUri>http://technet.microsoft.com/library/cc731977(v=ws.10).aspx</linkUri></externalLink> in the <externalLink><linkText>Web Server (IIS)</linkText><linkUri>http://technet.microsoft.com/library/cc753433(v=ws.10).aspx</linkUri></externalLink> documentation library on TechNet.</para>
          </listItem>
          <listItem>
            <para>To configure IIS to use the certificate, see <externalLink><linkText>Add a Binding to a Site (IIS 7)</linkText><linkUri>http://technet.microsoft.com/library/cc731692.aspx</linkUri></externalLink> in the in the <externalLink><linkText>Web Server (IIS)</linkText><linkUri>http://technet.microsoft.com/library/cc753433(v=ws.10).aspx</linkUri></externalLink> documentation library on TechNet.</para>
          </listItem>
        </list>
      </alert>
    </content>
  </section>
  <section address="BKMK_ConfiguringWebProxy">
    <title>Configuring the RMS connector for a web proxy server</title>
    <content>
      <para>If your connector servers are installed in a network that does not have direct Internet connectivity and requires manual configuration of a web proxy server for outbound Internet access, you must configure the registry on these servers for the RMS connector. </para>
      <procedure>
        <title>To configure the RMS connector to use a web proxy server</title>
        <steps class="ordered">
          <step>
            <content>
              <para>On each server running the RMS connector, open a registry editor, such as Regedit.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Navigate to <ui>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\AADRM\Connector</ui></para>
            </content>
          </step>
          <step>
            <content>
              <para>Add the string value of <ui>ProxyAddress</ui> and then set the Data for this value to be <ui>http://&lt;MyProxyDomainOrIPaddress&gt;:&lt;MyProxyPort&gt;</ui></para>
              <para>For example: <userInput>http://proxyserver.contoso.com:8080</userInput></para>
            </content>
          </step>
          <step>
            <content>
              <para>Close the registry editor, and then restart the server or perform an IISReset command to restart IIS.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
  </section>
  <section address="BKMK_InstallingStandaloneTool">
    <title>Installing the RMS connector administration tool on administrative computers</title>
    <content>
      <para>You can run the RMS connector administration tool from a computer that does not have the RMS connector installed, if that computer meets the following requirements:</para>
      <list class="bullet">
        <listItem>
          <para>A physical or virtual computer running Windows Server 2012 or Windows Server 2012 R2 (all editions), Windows Server 2008 R2 or Windows Server 2008 R2 Service Pack 1 (all editions), Windows 8.1, Windows 8, or Windows 7.</para>
        </listItem>
        <listItem>
          <para>At least 1 GB of RAM.</para>
        </listItem>
        <listItem>
          <para>A minimum of 64 GB of disk space.</para>
        </listItem>
        <listItem>
          <para>At least one network interface.</para>
        </listItem>
        <listItem>
          <para>Access to the Internet via a firewall (or web proxy).  </para>
        </listItem>
      </list>
      <para>To install the RMS connector administration tool, run the following files:</para>
      <list class="bullet">
        <listItem>
          <para>For a 32-bit computer: RMSConnectorAdminToolSetup_x86.exe</para>
        </listItem>
        <listItem>
          <para>For a 64-bit computer: RMSConnectorSetup.exe</para>
        </listItem>
      </list>
      <para>If you haven’t already downloaded these files, you can do so from the <externalLink><linkText>Microsoft Download Center</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=314106</linkUri></externalLink>.</para>
    </content>
  </section>
  <section address="ConfiguringServers">
    <title>Configuring servers to use the RMS connector</title>
    <content>
      <para>After you have installed and configured the RMS connector, you are ready to configure your on-premises servers that will use Rights Management and connect to Azure RMS by using the connector. This means configuring the following servers: </para>
      <list class="bullet">
        <listItem>
          <para>For Exchange 2013: Client access servers and mailbox servers</para>
        </listItem>
        <listItem>
          <para>For Exchange 2010: Client access servers and hub transport servers</para>
        </listItem>
        <listItem>
          <para>For SharePoint: Front-end SharePoint webservers, including those hosting the Central Administration server</para>
        </listItem>
        <listItem>
          <para>For File Classification Infrastructure: Windows Server computers that have installed File Resource Manager</para>
        </listItem>
      </list>
      <para>This configuration requires registry settings. To do this, you have two options:</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Configuration option</para>
            </TD>
            <TD>
              <para>Advantages</para>
            </TD>
            <TD>
              <para>Disadvantages</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Automatically by using the server configuration tool for Microsoft RMS connector</para>
            </TD>
            <TD>
              <para>No direct editing of the registry. This is automated for you by using a script.</para>
              <para>No need to run a Windows PowerShell cmdlet to obtain your Microsoft RMS URL.</para>
              <para>The prerequisites are automatically checked for you (but not automatically remediated) if you run it locally.</para>
            </TD>
            <TD>
              <para>When you run the tool, you must make a connection to a server that is already running the RMS connector.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Manually by editing the registry</para>
            </TD>
            <TD>
              <para>No connectivity to a server running the RMS connector is required.</para>
            </TD>
            <TD>
              <para>More administrative overheads that are error-prone.</para>
              <para>You must obtain your Microsoft RMS URL, which requires you to run a Windows PowerShell command.</para>
              <para>You must always make all the prerequisites checks yourself.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para/>
      <alert class="important">
        <para>In both cases, you must manually install any prerequisites and configure Exchange, SharePoint, and File Classification Infrastructure to use Rights Management. </para>
      </alert>
      <para>For most organizations, automatic configuration by using the server configuration tool for Microsoft RMS connector will be the better option, because it provides greater efficiency and reliability than manual configuration.</para>
      <para>After making the configuration changes on these servers, you must restart them if they are running Exchange or SharePoint and previously configured to use AD RMS. There is no need to restart these servers if you are configuring them for Rights Management for the first time. You must always restart the file server that is configured to use File Classification Infrastructure after you make these configuration changes.</para>
      <procedure address="BKMK_HowToRunTheTool">
        <title>How to use the server configuration tool for Microsoft RMS connector</title>
        <steps class="ordered">
          <step>
            <content>
              <para>If you haven’t already downloaded the script for the server configuration tool for Microsoft RMS connector (GenConnectorConfig.ps1), download it from the <externalLink><linkText>Microsoft Download Center</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=314106</linkUri></externalLink>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Save the GenConnectorConfig.ps1 file on the computer where you will run the tool. If you will run the tool locally, this must be the server that you want to configure to communicate with the RMS connector. Otherwise, you can save it on any computer.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Decide how to run the tool:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <embeddedLabel>Locally</embeddedLabel>: You can run the tool interactively, from the server to be configured to communicate with the RMS connector. This is useful for a one-off configuration, such as a testing environment.</para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Software deployment</embeddedLabel>: You can run the tool to produce registry files that you then deploy to one or more relevant servers by using a systems management application that supports software deployment, such as System Center Configuration Manager.</para>
                 </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Group Policy</embeddedLabel>: You can run the tool to produce a script that you give to an administrator who can create Group Policy objects for the servers to be configured. This script creates one Group Policy object for each server type to be configured, which the administrator can then assign to the relevant servers.</para>
                </listItem>
              </list>
              <alert class="note">
                <para>This tool configures the servers that will communicate with the RMS connector and that are listed at the beginning of this section. Do not run this tool on the servers that run the RMS connector.</para>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>Start Windows PowerShell with the <ui>Run as an administrator</ui> option, and use the Get-help command to read instructions how to the use the tool for your chosen configuration method:</para>
              <code>Get-help .\GenConnectorConfig.ps1 -detailed</code>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>To run the script, you must enter the URL of the RMS connector for your organization. Enter the protocol prefix (HTTP:// or HTTPS://) and the name of the connector that you defined in DNS for the load balanced address of your connector. For example, https://connector.contoso.com. The tool then uses that URL to contact the servers running the RMS connector and obtain other parameters that are used to create the required configurations.</para>
            <alert class="important">
              <para>When you run this tool, make sure that you specify the name of the load-balanced RMS connector for your organization and not the name of a single server that runs the RMS connector service.</para>
            </alert>
          </content>
        </conclusion>
      </procedure>
      <para>Use the following sections for specific information for each service type:</para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_ExchangeServer">Configuring an Exchange server to use the connector</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_ConfiguringSharePoint">Configuring a SharePoint server to use the connector</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_FileServer">Configuring a file server for File Classification Infrastructure to use the connector</link>
          </para>
        </listItem>
      </list>
      <alert class="note">
        <para>After these servers are configured to use the connector, client applications that are installed locally on these servers might not work with RMS. When this happens, it is because the applications try to use the connector rather than use RMS directly, which is not supported. </para>
        <para>In addition, if Office 2010 is installed locally on an Exchange server, the client app’s IRM features might work from that computer after the server is configured to use the connector, but this is not supported. </para>
        <para>In both scenarios, you must install the client applications on separate computers that are not configured to use the connector. They will then correctly use RMS directly.</para>
      </alert>
    </content>
    <sections>
      <section address="BKMK_ExchangeServer">
        <title>Configuring an Exchange server to use the connector</title>
        <content>
          <para>The following Exchange roles communicate with the RMS connector:</para>
          <list class="bullet">
            <listItem>
              <para>For Exchange 2013: Client access server and mailbox server</para>
            </listItem>
            <listItem>
              <para>For Exchange 2010: Client access server and hub transport server</para>
            </listItem>
          </list>
          <para>To use the RMS connector, these servers running Exchange must be running one of the following software versions:</para>
          <list class="bullet">
            <listItem>
              <para>Exchange Server 2013 with Exchange 2013 Cumulative Update 3</para>
            </listItem>
            <listItem>
              <para>Exchange Server 2010 with Exchange 2010 Service Pack 3 Rollup Update 6</para>
            </listItem>
          </list>
          <para>You will also need to install on these servers, a version of the RMS client that includes support for RMS Cryptographic Mode 2. The minimum version that is supported in Windows Server 2008 is included in the hotfix that you can download from <externalLink><linkText>RSA key length is increased to 2048 bits for AD RMS in Windows Server 2008 R2 and in Windows Server 2008</linkText><linkUri>http://support.microsoft.com/kb/2627272</linkUri></externalLink>. The minimum version for Windows Server 2008 R2 can be downloaded from <externalLink><linkText>RSA key length is increased to 2048 bits for AD RMS in Windows 7 or in Windows Server 2008 R2</linkText><linkUri>http://support.microsoft.com/kb/2627273</linkUri></externalLink>. Windows Server 2012 and Windows Server 2012 R2 natively support Cryptographic Mode 2.</para>
          <alert class="important">
            <para>If these versions or later versions of Exchange and the RMS client are not installed, you will not be able to configure Exchange to use the connector. Check that these versions are installed before you continue.</para>
          </alert>
          <procedure>
            <title>To configure Exchange servers to use the connector</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>On the Exchange server roles that communicate with the RMS connector, do one of the following:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Run the server configuration tool for Microsoft RMS connector. For more information, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_HowToRunTheTool">How to use the server configuration tool for Microsoft RMS connector</link> in this topic.</para>
                    <para>For example, to run the tool locally to configure a server running Exchange 2013: </para><code>.\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetExchange2013</code></listItem>
                    <listItem>
                      <para>Make manual registry edits by using the tables in the following sections to manually add registry settings on the servers.</para>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>Enable IRM functionality in Exchange. For more information, see <externalLink><linkText>Information Rights Management Procedures</linkText><linkUri>https://technet.microsoft.com/library/dd351212(v=exchg.150).aspx</linkUri></externalLink> in the Exchange library.</para>
                </content>
              </step>
            </steps>
          </procedure>
          <para>Use the tables in the following sections only if you want to manually add or check registry settings on these servers, which configures the servers to use the RMS connector. Instructions for when you use these tables:</para>
          <list class="bullet">
            <listItem>
              <para>
                <placeholder>MicrosoftRMSURL</placeholder> is your organization’s Microsoft RMS service URL. <?Comment CB: 251527– updated, again 2014-04-26T11:24:00Z  Id='50?>To find this value:<?CommentEnd Id='50'
    ?></para>
              <list class="ordered">
                <listItem>
                  <para>Run the <externalLink><linkText>Get-AadrmConfiguration</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629410.aspx</linkUri></externalLink> cmdlet for Azure RMS. If you haven’t already installed the Windows PowerShell module for Azure RMS, see <link xlink:href="0d665ed6-b1de-4d63-854a-bc57c1c49844">Installing Windows PowerShell for Azure Rights Management</link>.</para>
                </listItem>
                <listItem>
                  <para>From the output, identify the <ui>LicensingIntranetDistributionPointUrl</ui> value. </para>
                  <para>For example: <ui>LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing</ui></para>
                </listItem>
                <listItem>
                  <para>From the value, remove <ui>/_wmcs/licensing</ui> from this string. The remaining string is your Microsoft RMS URL. In our example, the Microsoft RMS URL would be the following value:</para>
                  <para>
                    <ui>https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com</ui>
                  </para>
                </listItem>
              </list>
            </listItem>
            <listItem>
              <para>
                <placeholder>ConnectorFQDN</placeholder> is the load-balancing name that you defined in DNS for the connector. For example, <system>rmsconnector.contoso.com</system>.</para>
            </listItem>
            <listItem>
              <para>Use the HTTPS prefix for the connector URL if you have configured the connector to use HTTPS to communicate with your on-premises servers. For more information, see the <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_ConfiguringHTTPS">Configuring the RMS connector to use HTTPS</link> section in this topic. The Microsoft RMS URLs always use HTTPS.</para>
            </listItem>
          </list>
        </content>
        <sections>
          <section expanded="false">
            <title>Table for Exchange 2013 registry settings</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Registry path</para>
                    </TD>
                    <TD>
                      <para>Type</para>
                    </TD>
                    <TD>
                      <para>Value</para>
                    </TD>
                    <TD>
                      <para>Data</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                    </TD>
                    <TD>
                      <para>Default</para>
                    </TD>
                    <TD>
                      <para>https://<placeholder>MicrosoftRMSURL/_wmcs/certification</placeholder></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                    </TD>
                    <TD>
                      <para>Default</para>
                    </TD>
                    <TD>
                      <para>https://MicrosoftRMSURL/_wmcs/Licensing</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\CertificationServerRedirection</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                      <para/>
                    </TD>
                    <TD>
                      <para>https://<placeholder>MicrosoftRMSURL</placeholder></para>
                    </TD>
                    <TD>
                      <para>One of the following, depending on whether you are using HTTP or HTTPS from your Exchange server to the RMS connector:</para>
                      <list class="bullet">
                        <listItem>
                          <para>http://<placeholder>ConnectorFQDN</placeholder></para>
                        </listItem>
                        <listItem>
                          <para>https://<placeholder>ConnectorFQDN</placeholder></para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                      <para/>
                    </TD>
                    <TD>
                      <para>https://<placeholder>MicrosoftRMSURL</placeholder></para>
                    </TD>
                    <TD>
                      <para>One of the following, depending on whether you are using HTTP or HTTPS from your Exchange server to the RMS connector:</para>
                      <list class="bullet">
                        <listItem>
                          <para>http://<placeholder>ConnectorFQDN</placeholder></para>
                        </listItem>
                        <listItem>
                          <para>https://<placeholder>ConnectorFQDN</placeholder></para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
          <section expanded="false">
            <title>Table for Exchange 2010 registry settings</title>
            <content>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Registry path</para>
                    </TD>
                    <TD>
                      <para>Type</para>
                    </TD>
                    <TD>
                      <para>Value</para>
                    </TD>
                    <TD>
                      <para>Data</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\Activation</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                    </TD>
                    <TD>
                      <para>Default</para>
                    </TD>
                    <TD>
                      <para>https://<placeholder>MicrosoftRMSURL</placeholder>/_wmcs/certification</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                    </TD>
                    <TD>
                      <para>Default</para>
                    </TD>
                    <TD>
                      <para>https://<placeholder>MicrosoftRMSURL</placeholder>/_wmcs/Licensing</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\CertificationServerRedirection</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                    </TD>
                    <TD>
                      <para>https://<placeholder>MicrosoftRMSURL</placeholder></para>
                    </TD>
                    <TD>
                      <para>One of the following, depending on whether you are using HTTP or HTTPS from your Exchange server to the RMS connector:</para>
                      <list class="bullet">
                        <listItem>
                          <para>http://<placeholder>ConnectorFQDN</placeholder></para>
                        </listItem>
                        <listItem>
                          <para>https://<placeholder>ConnectorFQDN</placeholder></para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                    </TD>
                    <TD>
                      <para>https://<placeholder>MicrosoftRMSURL</placeholder></para>
                    </TD>
                    <TD>
                      <para>One of the following, depending on whether you are using HTTP or HTTPS from your Exchange server to the RMS connector:</para>
                      <list class="bullet">
                        <listItem>
                          <para>http://<placeholder>ConnectorFQDN</placeholder></para>
                        </listItem>
                        <listItem>
                          <para>https://<placeholder>ConnectorFQDN</placeholder></para>
                        </listItem>
                      </list>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
        </sections>
      </section>
      <section address="BKMK_ConfiguringSharePoint">
        <title>Configuring a SharePoint server to use the connector</title>
        <content>
          <para>The following SharePoint roles communicate with the RMS connector:</para>
          <list class="bullet">
            <listItem>
              <para>Front-end SharePoint webservers, including those hosting the Central Administration server</para>
            </listItem>
          </list>
          <para>To use the RMS connector, these servers running SharePoint must be running one of the following software versions:</para>
          <list class="bullet">
            <listItem>
              <para>SharePoint Server 2013</para>
            </listItem>
            <listItem>
              <para>SharePoint Server 2010</para>
            </listItem>
          </list>
          <para>A SharePoint 2013 server must also be running a version of the MSIPC client 2.1 <?xm-insertion_mark_start author="" time="20151110T105224-0800"?>that is <?xm-insertion_mark_end?>from<?xm-deletion_mark author="" time="20151110T105516-0800" data=" "?>1.0.622.34 through 1.0.10907.0. <?xm-deletion_mark author="" time="20151110T105213-0800" data="You can download the latest MSIPC client from the &lt;maml:externalLink xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;&lt;maml:linkText&gt;Microsoft Download Center&lt;/maml:linkText&gt;&lt;maml:linkUri&gt;http://www.microsoft.com/download/details.aspx?id=38396&lt;/maml:linkUri&gt;&lt;/maml:externalLink&gt;."?></para>
          <alert class="warning">
            <para>
              <?Comment CB: 247334 2014-04-26T11:24:00Z  Id='52?>There are multiple versions of the MSIPC 2.1 client, so make sure to install <?xm-deletion_mark author="" time="20151110T110122-0800" data="the"?><?xm-insertion_mark_start author="" time="20151110T110122-0800"?>a<?xm-insertion_mark_end?> version referenced in <?xm-deletion_mark author="" time="20151110T110126-0800" data="the"?><?xm-insertion_mark_start author="" time="20151110T110126-0800"?>this<?xm-insertion_mark_end?> article<?xm-insertion_mark_start author="" time="20151110T125916-0800"?>.<?xm-insertion_mark_end?> <?xm-deletion_mark author="" time="20151110T110130-0800" data="from the Download Center. Or, install a later version of the client."?></para>
            <para>You can verify the client version by checking the version number of MSIPC.dll, which is located in <system>\Program Files\Active Directory Rights Management Services Client 2.1</system>. The properties dialog box <?xm-deletion_mark author="" time="20151110T110143-0800" data="should"?> show<?xm-insertion_mark_start author="" time="20151110T110145-0800"?>s the<?xm-insertion_mark_end?> version<?xm-insertion_mark_start author="" time="20151110T130052-0800"?> number of the MSIPC 2.1 client<?xm-insertion_mark_end?><?xm-deletion_mark author="" time="20151110T110159-0800" data=" 1.0.622.34 or later"?>.<?CommentEnd Id='52'
    ?></para>
          </alert>
          <para>These servers running SharePoint 2010 must have installed a version of the MSDRM client that includes support for RMS Cryptographic Mode 2. The minimum version that is supported in Windows Server 2008 is included in the hotfix that you can download from <externalLink><linkText>RSA key length is increased to 2048 bits for AD RMS in Windows Server 2008 R2 and in Windows Server 2008</linkText><linkUri>http://support.microsoft.com/kb/2627272</linkUri></externalLink>, and the minimum version for Windows Server 2008 R2 can be downloaded from <externalLink><linkText>RSA key length is increased to 2048 bits for AD RMS in Windows 7 or in Windows Server 2008 R2</linkText><linkUri>http://support.microsoft.com/kb/2627273</linkUri></externalLink>. Windows Server 2012 and Windows Server 2012 R2 natively support Cryptographic Mode 2.</para>
          <procedure>
            <title>To configure SharePoint servers to use the connector</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>On the SharePoint servers that communicate with the RMS connector, do one of the following:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Run the server configuration tool for Microsoft RMS connector. For more information, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_HowToRunTheTool">How to use the server configuration tool for Microsoft RMS connector</link> in this topic.</para>
                    <para>For example, to run the tool locally to configure a server running SharePoint 2013: </para><code>.\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetSharePoint2013</code></listItem>
                    <listItem>
                      <para>If you are using SharePoint 2013, make manual registry edits by using the table in the following section to manually add registry settings on the servers.</para>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>Enable IRM in SharePoint. For more information, see <externalLink><linkText>Configure Information Rights Management (SharePoint Server 2010)</linkText><linkUri>https://technet.microsoft.com/library/hh545607(v=office.14).aspx</linkUri></externalLink> in the SharePoint library.</para>
                  <para>When you follow these instructions, you must configure SharePoint to use the connector by specifying <ui>Use this RMS server</ui>, and then enter the load-balancing connector URL that you configured. Enter the protocol prefix (HTTP:// or HTTPS://) and the name of the connector that you defined in DNS for the load balanced address of your connector. For example, if your connector name is  https://connector.contoso.com, your configuration will look like the following picture:</para>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="82377fdd-0c4b-4c2a-8c52-4d19e19f2cda"/>
                    </mediaLinkInline>
                  </para>
                  <para>After IRM is enabled on a SharePoint farm, you can enable IRM on individual libraries by using the <ui>Information Rights Management</ui> option on the <ui>Library Settings</ui> page for each of the libraries.</para>
                  <alert class="important">
                    <para>For SharePoint to access RMS by using the connector, you must authorize the corresponding accounts in the RMS connector administration tool. If you haven’t already done this, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#AuthorizingServers">Authorizing servers to use the RMS connector</link> in this topic.</para>
                  </alert>
                </content>
              </step>
            </steps>
          </procedure>
          <para>Use the table in the following section only if you want to manually add or check registry settings on a server that runs SharePoint 2013.</para>
        </content>
        <sections>
          <section expanded="false">
            <title>Table for SharePoint 2013 registry settings</title>
            <content>
              <para>Instructions for when you use this table:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <placeholder>MicrosoftRMSURL</placeholder> is your organization’s Microsoft RMS service URL. <?Comment CB: 251527– updated, again 2014-04-26T11:24:00Z  Id='67?>To find this value<?CommentEnd Id='67'
    ?>:</para>
                  <list class="ordered">
                    <listItem>
                      <para>Run the <externalLink><linkText>Get-AadrmConfiguration</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629410.aspx</linkUri></externalLink> cmdlet for Azure RMS. If you haven’t already installed the Windows PowerShell module for Azure RMS, see <link xlink:href="0d665ed6-b1de-4d63-854a-bc57c1c49844">Installing Windows PowerShell for Azure Rights Management</link>.</para>
                    </listItem>
                    <listItem>
                      <para>From the output, identify the <ui>LicensingIntranetDistributionPointUrl</ui> value. </para>
                      <para>For example: <ui>LicensingIntranetDistributionPointUrl   : https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com/_wmcs/licensing</ui></para>
                    </listItem>
                    <listItem>
                      <para>From the value, remove <ui>/_wmcs/licensing</ui> from this string. The remaining string is your Microsoft RMS URL. In our example, the Microsoft RMS URL would be the following value:</para>
                      <para>
                        <ui>https://5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com</ui>
                      </para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>
                    <placeholder>ConnectorFQDN</placeholder> is the load-balancing name that you defined in DNS for the connector. For example, <system>rmsconnector.contoso.com</system>.</para>
                </listItem>
                <listItem>
                  <para>Use the HTTPS prefix for the connector URL if you have configured the connector to use HTTPS to communicate with your on-premises servers. For more information, see the <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_ConfiguringHTTPS">Configuring the RMS connector to use HTTPS</link> section in this topic. The Microsoft RMS URLs always use HTTPS.</para>
                </listItem>
              </list>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Registry path </para>
                    </TD>
                    <TD>
                      <para>Type</para>
                    </TD>
                    <TD>
                      <para>Value</para>
                    </TD>
                    <TD>
                      <para>Data</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\LicensingRedirection</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                    </TD>
                    <TD>
                      <para>https://<placeholder>MicrosoftRMSURL</placeholder>/_wmcs/licensing</para>
                    </TD>
                    <TD>
                      <para>One of the following, depending on whether you are using HTTP or HTTPS from your SharePoint server to the RMS connector:</para><list class="bullet"><listItem><para>http://<placeholder>ConnectorFQDN</placeholder>/_wmcs/licensing</para>
                    </listItem><listItem><para>https://<placeholder>ConnectorFQDN</placeholder>/_wmcs/licensing</para>
                    </listItem></list>
                    </TD>
                  </tr><tr><TD><para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterpriseCertification</para></TD><TD><para>Reg_SZ</para></TD><TD><para>Default</para></TD><TD><para>One of the following, depending on whether you are using HTTP or HTTPS from your SharePoint server to the RMS connector:</para>
                      <list class="bullet">
                        <listItem>
                          <para>http://<placeholder>ConnectorFQDN</placeholder>/_wmcs/certification</para>
                        </listItem>
                        <listItem>
                          <para>https://<placeholder>ConnectorFQDN</placeholder>/_wmcs/certification</para>
                        </listItem>
                      </list></TD></tr><tr><TD><para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation\EnterprisePublishing</para></TD><TD><para>Reg_SZ</para></TD><TD><para>Default</para></TD><TD><para>One of the following, depending on whether you are using HTTP or HTTPS from your SharePoint server to the RMS connector:</para>
                      <list class="bullet">
                        <listItem>
                          <para>http://<placeholder>ConnectorFQDN</placeholder>/_wmcs/licensing</para>
                        </listItem>
                        <listItem>
                          <para>https://<placeholder>ConnectorFQDN</placeholder>/_wmcs/licensing</para>
                        </listItem>
                      </list></TD></tr>
                </tbody>
              </table>
            </content>
          </section>
        </sections>
      </section>
      <section address="BKMK_FileServer">
        <title>Configuring a file server for File Classification Infrastructure to use the connector</title>
        <content>
          <para>To use the RMS connector and File Classification Infrastructure to protect Office documents, the file server must be running one of the following operating systems:</para>
          <list class="bullet">
            <listItem>
              <para>Windows Server 2012 R2</para>
            </listItem>
            <listItem>
              <para>Windows Server 2012</para>
            </listItem>
          </list>
          <procedure>
            <title>To configure file servers to use the connector</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>On the file servers configured for File Classification Infrastructure and that will communicate with the RMS connector, do one of the following:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Run the server configuration tool for Microsoft RMS connector. For more information, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_HowToRunTheTool">How to use the server configuration tool for Microsoft RMS connector</link> in this topic.</para>
                    <para>For example, to run the tool locally to configure a file server running FCI: </para><code>.\GenConnectorConfig.ps1 -ConnectorUri https://rmsconnector.contoso.com -SetFCI2012</code></listItem>
                    <listItem>
                      <para>Make manual registry edits by using the table in the following section to manually add registry settings on the servers.</para>
                    </listItem>
                  </list>
                </content>
              </step>
              <step>
                <content>
                  <para>Create classification rules and file management tasks to protect documents with RMS Encryption, and then specify an RMS template to automatically apply RMS policies. For more information, see <externalLink><linkText>File Server Resource Manager Overview</linkText><linkUri>http://technet.microsoft.com/library/hh831701.aspx</linkUri></externalLink> in the Windows Server documentation library.</para>
                </content>
              </step>
            </steps>
          </procedure>
          <para>Use the table in the following section only if you want to manually add or check registry settings on a file server that uses the File Classification Infrastructure to protect documents.</para>
        </content>
        <sections>
          <section expanded="false">
            <title>Table for file server and File Classification Infrastructure registry settings</title>
            <content>
              <para>Instructions for when you use this table:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <placeholder>ConnectorFQDN</placeholder> is the load-balancing name that you defined in DNS for the connector. For example, <system>rmsconnector.contoso.com</system>.</para>
                </listItem>
                <listItem>
                  <para>Use the HTTPS prefix for the connector URL if you have configured the connector to use HTTPS to communicate with your on-premises servers. For more information, see the <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066#BKMK_ConfiguringHTTPS">Configuring the RMS connector to use HTTPS</link> section in this topic. The Microsoft RMS URLs always use HTTPS.</para>
                </listItem>
              </list>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Registry path </para>
                    </TD>
                    <TD>
                      <para>Type</para>
                    </TD>
                    <TD>
                      <para>Value</para>
                    </TD>
                    <TD>
                      <para>Data</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\EnterprisePublishing</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                    </TD>
                    <TD>
                      <para>Default</para>
                    </TD>
                    <TD>
                      <para>http://<placeholder>ConnectorFQDN</placeholder>/_wmcs/licensing</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSDRM\ServiceLocation\Activation</para>
                    </TD>
                    <TD>
                      <para>Reg_SZ</para>
                    </TD>
                    <TD>
                      <para>Default</para>
                    </TD>
                    <TD>
                      <para>http://<placeholder>ConnectorFQDN</placeholder>/_wmcs/certification</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section address="BKMK_NextSteps">
    <title>Next steps</title>
    <content>
      <para>Now that the RMS connector is installed and configured, and your servers are configured to use it, IT administrators and users can protect and consume email message and documents by using Azure RMS. To make this easy for users, deploy the RMS sharing application, which installs an add-on for Office and adds new right-click options to File Explorer. For more information, see the <externalLink><linkText>Rights Management sharing application administrator guide</linkText><linkUri>http://technet.microsoft.com/library/ dn339003(v=ws.10).aspx</linkUri></externalLink>.</para>
      <para>In addition, you might consider the following to help you monitor the RMS connector and your organization’s usage of Azure RMS:</para>
      <list class="bullet">
        <listItem>
          <para>The built-in <ui>Microsoft Rights Management connector</ui> performance counters.</para>
        </listItem>
        <listItem><para>The <externalLink><linkText>RMS Analyzer tool</linkText><linkUri>https://www.microsoft.com/en-us/download/details.aspx?id=46437</linkUri></externalLink>, using the RMS connector option to help you monitor the health of the connector and identify any configuration issues.</para></listItem><listItem>
          <para>
            <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e">Log and analyze rights management usage</link>
          </para>
        </listItem>
      </list>
      <para>You can use the <link xlink:href="086600c2-c5d8-47ec-a4c0-c782e1797486">Azure Rights Management Deployment Roadmap</link> to check whether there are other configuration steps that you might want to do before you roll out <token>aad_rightsmanagement_1</token> to users and administrators. If there are no other configuration steps that you need to do, see <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using Azure Rights Management</link> for operational guidance to support a successful deployment for your organization.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring rights management</link>
  </relatedTopics>
</developerConceptualDocument>
