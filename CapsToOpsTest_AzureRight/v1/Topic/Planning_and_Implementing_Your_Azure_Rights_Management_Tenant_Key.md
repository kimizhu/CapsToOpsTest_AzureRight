---
description: na
keywords: na
pagetitle: Planning and Implementing Your Azure Rights Management Tenant Key
search: na
ms.date: 2015-10-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# Planning and Implementing Your Azure Rights Management Tenant Key
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the information in this topic to help you plan for and manage your Rights Management service (RMS) tenant key for Azure RMS. For example, instead of Microsoft managing your tenant key (the default), you might want to manage your own tenant key to comply with specific regulations that apply to your organization.  Managing your own tenant key is also referred to as bring your own key, or BYOK.</para>
    <alert class="note">
      <para>The RMS tenant key is also known as the Server Licensor Certificate (SLC) key. Azure RMS maintains one or more keys for each organization that subscribes to Azure RMS. Whenever a key is used for RMS within an organization (such as user keys, computer keys, document encryption keys), they cryptographically chain to your RMS tenant key.</para>
    </alert><para><embeddedLabel>At a glance:</embeddedLabel> Use the following table as a quick guide to your recommended tenant key topology. Then, use the additional sections for more information.</para><para>If you deploy Azure RMS by using a tenant key that is managed by Microsoft, you can change to BYOK later. However, you cannot currently change your Azure RMS tenant key from BYOK to managed by Microsoft.</para><table>
<tbody><tr><TH><para>Business requirement</para></TH><TH><para>Recommended tenant key topology</para></TH></tr>
<tr><TD><para>Deploy Azure RMS quickly and without requiring special hardware</para></TD><TD><para>Managed by Microsoft</para></TD></tr><tr><TD><para>Need full IRM functionality in Exchange Online with Azure RMS</para></TD><TD><para>Managed by Microsoft</para></TD></tr><tr><TD><para>Your keys are created by you and protected in a hardware security module (HSM)</para></TD><TD><para>BYOK</para><para>Currently, this configuration will result in reduced IRM functionality in Exchange Online. For more information, see the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_Pricing">BYOK pricing and restrictions</link> section.</para></TD></tr>
</tbody></table>
    
    <para>Use the following sections to help you choose which tenant key topology to use, understand the tenant key lifecycle, how to implement bring your own key (BYOK), and what steps to take next:</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_ChooseTenantKey">Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_Pricing">BYOK pricing and restrictions</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_ImplementBYOK">Implementing bring your own key (BYOK)</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_NextSteps">Next steps</link>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMK_ChooseTenantKey">
    <title>Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)</title>
    <content>
      <para>Decide which tenant key topology is best for your organization. By default, Azure RMS generates your tenant key and manages most aspects of the tenant key lifecycle. This is the simplest option with the lowest administrative overheads. In most cases, you do not even need to know that you have a tenant key. You just sign up for Azure RMS and the rest of the key management process is handled by Microsoft.</para>
      <para>Alternatively, you might want complete control over your tenant key, which involves creating your tenant key and keeping the master copy on your premises. This scenario is often referred to as bring your own key (BYOK). With this option, the following happens:</para>
      <list class="ordered">
        <listItem>
          <para>You generate your tenant key on your premises, in line with your IT policies.</para>
        </listItem>
        <listItem>
          <para>You securely transfer the tenant key from a Hardware Security Module (HSM) in your possession to HSMs that are owned and managed by Microsoft. Throughout this process, your tenant key never leaves the hardware protection boundary.</para>
        </listItem>
        <listItem>
          <para>When you transfer your tenant key to Microsoft, it stays protected by Thales HSMs. Microsoft has worked with Thales to ensure that your tenant key cannot be extracted from Microsoft’s HSMs.</para>
        </listItem>
      </list>
      <para>Although it’s optional, you will also probably want to use the near real-time usage logs from Azure RMS to see exactly how and when your tenant key is being used.</para>
      <alert class="note">
        <para>As an additional protection measure, Azure RMS uses separate security worlds for its data centers in North America, EMEA (Europe, Middle East and Africa), and Asia. When you manage your own tenant key, it is tied to the security world of the region in which your RMS tenant is registered. For example, a tenant key from a European customer cannot be used in data centers in North America or Asia.</para>
      </alert>
    </content>
  </section>
  <section address="BKMK_OverviewLifecycle">
    <title>The tenant key lifecycle</title>
    <content>
      <para>If you decide that Microsoft should manage your tenant key, Microsoft handles most of the key lifecycle operations. However, if you decide to manage your tenant key, you are responsible for many of the key lifecycle operations and some additional procedures. </para>
      <para>The following diagrams show and compares these two options. The first diagram shows how little administrator overheads there are for you in the default configuration when Microsoft manages the tenant key. </para>
      <mediaLink>
        <caption>Tenant key managed by Microsoft</caption>
        <image xlink:href="66905ef5-1ba4-4c93-9513-c6d7a9173453"/>
      </mediaLink>
      <para/>
      <para>The second diagram shows the additional steps required when you manage your own tenant key.</para>
      <mediaLink>
        <caption>Tenant key managed by you (BYOK)</caption>
        <image xlink:href="ec00ba88-ad16-4426-81e3-d5d074ce0c31"/>
      </mediaLink>
      <para/>
      <para>If you decide to let Microsoft manage your tenant key, no further action is required for you to generate the key and you can skip the following sections and go straight to <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_NextSteps">Next steps</link>.</para>
      <para>If you decide to manage your tenant key yourself, read the following sections for more information.</para>
    </content>
    <sections>
      <section expanded="false">
        <title>More information about Thales HSMs and Microsoft additions</title>
        <content>
          <para>Azure RMS uses Thales HSMs to protect your keys. </para>
          <para>Thales e-Security is a leading global provider of data encryption and cyber security solutions to the financial services, high technology, manufacturing, government, and technology sectors. With a 40-year track record of protecting corporate and government information, Thales solutions are used by four of the five largest energy and aerospace companies, 22 NATO countries, and secure more than 80 per cent of worldwide payment transactions.</para>
          <para>Microsoft has collaborated with Thales to enhance the state of art for HSMs. These enhancements enable you to get the typical benefits of hosted services without relinquishing control over your keys. Specifically, these enhancements let Microsoft manage the HSMs so that you do not have to. As a cloud service, Azure RMS scales up at short notice to meet your organization’s usage spikes. At the same time, your key is protected inside Microsoft’s HSMs: You retain control over the key lifecycle because you generate the key and transfer it to Microsoft’s HSMs.</para>
          <para>For more information, see <externalLink><linkText>Thales HSMs and Azure RMS</linkText><linkUri>http://www.thales-esecurity.com/msrms/cloud</linkUri></externalLink> on the Thales web site.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_Pricing">
    <title>BYOK pricing and restrictions</title>
    <content>
      <para>Organization that have an IT-managed Azure subscription can use BYOK and log its usage at no extra charge. Organizations that use RMS for individuals cannot use BYOK and logging because they do not have a tenant administrator to configure these features.</para>
      <alert class="note">
        <para>For more information about RMS for individuals, see <link xlink:href="2efcb440-fefd-45e9-872b-f471573aadf2">RMS for Individuals and Azure Rights Management</link>.</para>
      </alert>
      <mediaLink>
        <image xlink:href="6417311a-9193-4c6e-a284-ac92b335ea80"/>
      </mediaLink>
      <para/>
      <para>BYOK and logging work seamlessly with every application that integrates with Azure RMS. This includes cloud services such as SharePoint Online, on-premises servers that run Exchange and SharePoint that work with Azure RMS by using the RMS connector, and client applications such as Office 2013. You will get key usage logs regardless of which application makes requests of Azure RMS. </para>
      <para>There is one exception: Currently, <embeddedLabel>Azure RMS BYOK is not compatible with Exchange Online</embeddedLabel>.  If you want to use Exchange Online, we recommend that you deploy Azure RMS in the default key management mode now, where Microsoft generates and manages your key. You have the option to move to BYOK later, for example, when Exchange Online does support Azure RMS BYOK. However, if you cannot wait, another option is to deploy Azure RMS with BYOK now, with reduced RMS functionality for Exchange Online (unprotected emails and unprotected attachments remain fully functional): </para>
      <list class="bullet"><listItem><para>Protected emails or protected attachments in Outlook Web Access cannot be displayed.</para></listItem><listItem><para>Protected emails on mobile devices that use Exchange ActiveSync IRM cannot be displayed.</para></listItem><listItem><para>Transport decryption (for example, to scan for malware) and journal  decryption is not possible, so protected emails and protected attachments will be skipped.</para></listItem><listItem><para>Transport protection rules and data loss prevention (DLP) that enforce IRM policies is not possible, so RMS protection cannot be applied by using these methods.</para></listItem><listItem><para>Server-based search for protected emails, so protected emails will be skipped.</para></listItem></list><para>When you use Azure RMS BYOK with reduced RMS functionality for Exchange Online, RMS will work with email clients in Outlook on Windows and Mac, and on other email clients that don't use Exchange ActiveSync IRM. </para><para>If you are migrating to Azure RMS from AD RMS, you might have imported your key as a trusted publishing domain (TPD) to Exchange Online (also called BYOK in Exchange terminology, which is separate from Azure RMS BYOK). In this scenario, you must remove the TPD from Exchange Online to avoid conflicting templates and policies. For more information, see <externalLink><linkText>Remove-RMSTrustedPublishingDomain</linkText><linkUri>https://technet.microsoft.com/library/jj200720(v=exchg.150).aspx</linkUri></externalLink> from the Exchange Online cmdlets library.</para>
    <para>Sometimes, the Azure RMS BYOK  exception for Exchange Online is not a problem in practice. For example, organizations that need BYOK and logging run their data applications (Exchange, SharePoint, Office) on-premises, and use Azure RMS for functionality that is not easily available with on-premises AD RMS (for example, collaboration with other companies and access from mobile clients). Both BYOK and logging work well in this scenario and allow the organization to have full control over their Azure RMS subscription.</para></content>
  </section>
  <section address="BKMK_ImplementBYOK">
    <title>Implementing bring your own key (BYOK)</title>
    <content>
      <para>Use the information and procedures in this section if you have decided to generate and manage your tenant key; the bring your own key (BYOK) scenario:</para>
      <list class="bullet">
        <listItem>
          <para>
            <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_Preqs">Prerequisites for BYOK</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_BYOK_Internet">Generate and transfer your tenant key – over the Internet</link>
          </para>
        </listItem>
        <listItem>
          <para>
            <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_BYOK_InPerson">Generate and transfer your tenant key – in person</link> </para>
        </listItem>
      </list>
      <alert class="important">
        <para>If you have already started to use <token>aad_rightsmanagement_1</token> (the service is activated) and you have users who run Office 2010, contact Microsoft Customer Support Services (CSS) before you run these procedures. Depending on your scenario and requirements, you can still use BYOK but with some limitations or additional steps. </para>
        <para>Also contact CSS if your organization has specific policies for handling keys.</para>
      </alert>
    </content>
    <sections>
      <section address="BKMK_Preqs">
        <title>Prerequisites for BYOK</title>
        <content>
          <para>See the following table for a list of prerequisites for bring your own key (BYOK).</para>
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
                  <para>A subscription that supports Azure RMS</para>
                </TD>
                <TD>
                  <para>For more information about the available subscriptions, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedSubscriptions">Cloud subscriptions that support Azure RMS</link> section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>You do not use RMS for individuals or Exchange Online. Or, if you use Exchange Online, you understand and accept the limitations of using BYOK with this configuration.</para>
                  
                </TD>
                <TD>
                  <para>For more information about the restrictions and current limitations for BYOK, see the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_Pricing">BYOK pricing and restrictions</link> section in this topic.</para>
                  <alert class="important">
                    <para>Currently, BYOK is not compatible with Exchange Online.  </para>
                  </alert>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Thales HSM, smartcards, and support software</para>
                  <para>If you are migrating from AD RMS to Azure RMS by using software key to hardware key, you must have a minimum version of 11.62 for the Thales drivers.</para>
                </TD>
                <TD>
                  <para>You must have access to a Thales Hardware Security Module and basic operational knowledge of Thales HSMs. See <externalLink><linkText>Thales Hardware Security Module</linkText><linkUri>http://www.thales-esecurity.com/msrms/buy</linkUri></externalLink> for the list of compatible models, or to purchase an HSM if you do not have one.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>If you want to transfer your tenant key over the Internet rather than physically be present in Redmond, USA:</para>
                  <list class="ordered">
                    <listItem>
                      <para>An offline x64 workstation with a minimum Windows operation system of Windows 7 and Thales nShield software that is at least version 11.62.</para>
                      <para>If this workstation runs Windows 7, you must <externalLink><linkText>install Microsoft .NET Framework 4.5</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=225702</linkUri></externalLink>.</para>
                    </listItem>
                    <listItem>
                      <para>A workstation that is connected to the Internet and has a minimum Windows operation system of Windows 7.</para>
                    </listItem>
                    <listItem>
                      <para>A USB drive or other portable storage device that has at least 16 MB free space.</para>
                    </listItem>
                  </list>
                </TD>
                <TD>
                  <para>These prerequisites are not required if you travel to Redmond and transfer your tenant key in person.</para>
                  <para>For security reasons, we recommend that the first workstation is not connected to a network. However, this is not programmatically enforced. </para>
                  <alert class="note">
                    <para>In the instructions that follow, this workstation is referred to as the disconnected workstation.</para>
                  </alert>
                  <para>In addition, if your tenant key is for a production network, we recommend that you use a second, separate workstation to download the toolset and upload the tenant key. But for testing purposes, you can use the same workstation as the first one. </para>
                  <alert class="note">
                    <para>In the instructions that follow, this second workstation is referred to as the Internet-connected workstation.</para>
                  </alert>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Optional: Azure subscription </para>
                </TD>
                <TD>
                  <para>If you want to log your tenant key usage (and Rights Management usage), you must have a subscription to Azure and sufficient storage on Azure to store your logs.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>The procedures to generate and use your own tenant key depend on whether you want to do this over the Internet or in person:</para>
          <list class="bullet">
            <listItem>
              <para>
                <legacyBold>Over the Internet:</legacyBold> This requires some extra configuration steps, such as downloading and using a toolset and Windows PowerShell cmdlets. However, you do not have to physically be in a Microsoft facility to transfer your tenant key. Security is maintained by the following methods: </para>
              <list class="bullet">
                <listItem>
                  <para>You generate the tenant key from an offline workstation, which reduces the attack surface.</para>
                </listItem>
                <listItem>
                  <para>The tenant key is encrypted with a Key Exchange Key (KEK), which stays encrypted until it is transferred to the Azure RMS HSMs. Only the encrypted version of your tenant key leaves the original workstation.</para>
                </listItem>
                <listItem>
                  <para>A tool sets properties on your tenant key that binds your tenant key to the Azure RMS security world. So after the Azure RMS HSMs receive and decrypt your tenant key, only these HSMs can use it. Your tenant key cannot be exported. This binding is enforced by the Thales HSMs.</para>
                </listItem>
                <listItem>
                  <para>The Key Exchange Key (KEK) that is used to encrypt your tenant key is generated inside the Azure RMS HSMs and is not exportable. The HSMs enforce that there can be no clear version of the KEK outside the HSMs. In addition, the toolset includes attestation from Thales that the KEK is not exportable and was generated inside a genuine HSM that was manufactured by Thales.</para>
                </listItem>
                <listItem>
                  <para>The toolset includes attestation from Thales that the Azure RMS security world was also generated on a genuine HSM manufactured by Thales. This proves to you that Microsoft is using genuine hardware.</para>
                </listItem>
                <listItem>
                  <para>Microsoft uses separate KEKs as well as separate Security Worlds in each geographical region, which ensures that your tenant key can be used only in data centers in the region in which you encrypted it. For example, a tenant key from a European customer cannot be used in data centers in North American or Asia.</para>
                </listItem>
              </list>
              <alert class="note">
                <para>Your tenant key can safely move through untrusted computers and networks because it is encrypted and secured with access control level permissions, which makes it usable only within your HSMs and Microsoft’s HSMs for Azure RMS. You can use the scripts that are provided in the toolset to verify the security measures and read more information about how this works from Thales: <externalLink><linkText>Hardware Key management in the RMS Cloud</linkText><linkUri>https://www.thales-esecurity.com/knowledge-base/white-papers/hardware-key-management-in-the-rms-cloud</linkUri></externalLink>. </para>
              </alert>
            </listItem>
            <listItem>
              <para>
                <legacyBold>In person:</legacyBold> This requires that you contact Microsoft Customer Support Services (CSS) to schedule a key transfer appointment for Azure RMS. You must travel to a Microsoft office in Redmond, Washington, United States of America to transfer your tenant key to the Azure RMS security world. </para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_BYOK_Internet" expanded="false">
        <title>Generate and transfer your tenant key – over the Internet</title>
        <content>
          <para>Use the following procedures if you want to transfer your tenant key over the Internet rather than travel to a Microsoft facility to transfer the tenant key in person: </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetPrepareWorkstation">Prepare your Internet-connected workstation</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_DisconnectedPrepareWorkstation">Prepare your disconnected workstation</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetGenerate">Generate your tenant key</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetPrepareTransfer">Prepare your tenant key for transfer</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetTransfer">Transfer your tenant key to Azure RMS</link>
              </para>
            </listItem>
          </list>
        </content>
        <sections>
          <section address="BKMK_InternetPrepareWorkstation">
            <title>Prepare your Internet-connected workstation</title>
            <content>
              <para>To prepare your workstation that is connected to the Internet, follow these 3 steps:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_PrepareInternetConnectedWorkstation1">Step 1: Install Windows PowerShell for Azure Rights Management</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_PrepareInternetConnectedWorkstation2">Step 2: Get your Azure Active Directory tenant ID</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_PrepareInternetConnectedWorkstation3">Step 3: Download the BYOK toolset</link>
                  </para>
                </listItem>
              </list>
            </content>
            <sections>
              <section address="BKMK_PrepareInternetConnectedWorkstation1">
                <title>Step 1: Install Windows PowerShell for Azure Rights Management</title>
                <content>
                  <para>From the Internet-connected workstation, download and install the Windows PowerShell module for Azure Rights Management.  </para>
                  <alert class="note">
                    <?Comment CB: 8073 2015-01-16T09:24:00Z  Id='8?>
                    <para>If you have previously downloaded this Windows PowerShell module, run the following command to check that your version number is at least 2.1.0.0: <codeInline>(Get-Module aadrm -ListAvailable).Version</codeInline> <?CommentEnd Id='8'
    ?></para>
                  </alert>
                  <para>For installation instructions, see <link xlink:href="0d665ed6-b1de-4d63-854a-bc57c1c49844">Installing Windows PowerShell for Azure Rights Management</link>.</para>
                </content>
              </section>
              <section address="BKMK_PrepareInternetConnectedWorkstation2">
                <title>Step 2: Get your Azure Active Directory tenant ID</title>
                <content>
                  <para>Start Windows PowerShell with the <ui>Run as administrator</ui> option, and then run the following commands:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Use the <externalLink><linkText>Connect-AadrmService</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629415.aspx</linkUri></externalLink> cmdlet to connect to the Azure RMS service:</para>
                      <code>Connect-AadrmService</code>
                      <para>When prompted, enter your <token>aad_rightsmanagement_1</token> tenant administrator credentials (typically, you will use an account that is a global administrator for Azure Active Directory or Office 365).</para>
                    </listItem>
                    <listItem>
                      <para>Use the <externalLink><linkText>Get-AadrmConfiguration</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629410.aspx</linkUri></externalLink> cmdlet to display the configuration of your tenant:</para>
                      <code>Get-AadrmConfiguration</code>
                      <para>From the output, save the GUID from the first line (BPOSId). This is your Azure Active Directory tenant ID, which you will need later when you prepare your tenant key for upload.</para>
                    </listItem>
                    <listItem>
                      <para>Use the <externalLink><linkText>Disconnect-AadrmService</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629416.aspx</linkUri></externalLink> cmdlet to disconnect from the Azure RMS service until you are ready to upload your key:</para>
                      <code>Disconnect-AadrmService</code>
                    </listItem>
                  </list>
                  <para>Do not close the Windows PowerShell window.</para>
                </content>
              </section>
              <section address="BKMK_PrepareInternetConnectedWorkstation3">
                <title address="BKMK_PrepareWorkstationInternetKey2">Step 3: Download the BYOK toolset</title>
                <content>
                  <para>Go to the Microsoft Download Center and <externalLink><linkText>download the BYOK toolset</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=335781</linkUri></externalLink> for your region:</para>
                  <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                    <thead>
                      <tr>
                        <TD>
                          <para>Region</para>
                        </TD>
                        <TD>
                          <para>Package name</para>
                        </TD>
                      </tr>
                    </thead>
                    <tbody>
                      <tr>
                        <TD>
                          <para>North America</para>
                          <para/>
                        </TD>
                        <TD>
                          <para>AzureRMS-BYOK-tools-UnitedStates.zip</para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Europe</para>
                          <para/>
                        </TD>
                        <TD>
                          <para>AzureRMS-BYOK-tools-Europe.zip</para>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>Asia</para>
                          <para/>
                        </TD>
                        <TD>
                          <para>AzureRMS-BYOK-tools-AsiaPacific.zip</para>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                  <para>The toolset includes the following :</para>
                  <list class="bullet">
                    <listItem>
                      <para>A Key Exchange Key (KEK) package that has a name beginning with <ui>BYOK-KEK-pkg-</ui>.</para>
                    </listItem>
                    <listItem>
                      <para>A Security World package that has a name beginning with <ui>BYOK-SecurityWorld-pkg-</ui>.</para>
                    </listItem>
                    <listItem>
                      <para>A python script named <ui>verifykeypackage.py</ui>.</para>
                    </listItem>
                    <listItem>
                      <para>A command-line executable file named <ui>KeyTransferRemote.exe</ui>, a metadata file named <ui>KeyTransferRemote.exe.config</ui>, and associated DLLs.</para>
                    </listItem>
                    <listItem>
                      <para>A Visual C++ Redistributable Package, named <ui>vcredist_x64.exe</ui>.</para>
                    </listItem>
                  </list>
                  <para>Copy the package to a USB drive or other portable storage.</para>
                </content>
              </section>
            </sections>
          </section>
          <section address="BKMK_DisconnectedPrepareWorkstation">
            <title>Prepare your disconnected workstation</title>
            <content>
              <para>To prepare your workstation that is not connected to a network (either the Internet or your internal network), follow these 2 steps:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_PrepareDisconnectedWorkstation1">Step 1: Prepare the disconnected workstation with Thales HSM</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_PrepareDisconnectedWorkstation2">Step 2: Install the BYOK toolset on the disconnected workstation</link>
                  </para>
                </listItem>
              </list>
            </content>
            <sections>
              <section address="BKMK_PrepareDisconnectedWorkstation1">
                <title address="BKMK_PrepareWorkstationInternetKey1">Step 1: Prepare the disconnected workstation with Thales HSM</title>
                <content>
                  <para>On the disconnected workstation, install the nCipher (Thales) support software on a Windows computer, and then attach a Thales HSM to that computer. </para>
                  <para>Ensure that the Thales tools are in your path <system>(%nfast_home%\bin</system> and <system>%nfast_home%\python\bin</system>). For example, type the following:</para>
                  <code>set PATH=%PATH%;”%nfast_home%\bin”;”%nfast_home%\python\bin”</code>
                  <para>For more information, see the user guide included with the Thales HSM, or visit the Thales website for Azure RMS at <externalLink><linkText>http://www.thales-esecurity.com/msrms/cloud</linkText><linkUri>http://www.thales-esecurity.com/msrms/cloud</linkUri></externalLink>.</para>
                </content>
              </section>
              <section address="BKMK_PrepareDisconnectedWorkstation2">
                <title>Step 2: Install the BYOK toolset on the disconnected workstation</title>
                <content>
                  <para>Copy the BYOK toolset package from the USB drive or other portable storage, and then do the following:</para>
                  <list class="ordered">
                    <listItem>
                      <para>Extract the files from the downloaded package into any folder.</para>
                    </listItem>
                    <listItem>
                      <para>From that folder, run vcredist_x64.exe.</para>
                    </listItem>
                    <listItem>
                      <para>Follow the instructions to the install the Visual C++ runtime components for Visual Studio 2012.</para>
                    </listItem>
                  </list>
                </content>
              </section>
            </sections>
          </section>
          <section address="BKMK_InternetGenerate">
            <title>Generate your tenant key</title>
            <content>
              <para>On the disconnected workstation, following these 3 steps to generate your own tenant key: </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetGenerate1">Step 1: Create a security world</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetGenerate2">Step 2: Validate the downloaded package</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetGenerate3">Step 3: Create a new key</link>
                  </para>
                </listItem>
              </list>
            </content>
            <sections>
              <section address="BKMK_InternetGenerate1">
                <title>Step 1: Create a security world</title>
                <content>
                  <para>Start a command prompt and run the Thales new-world program.</para>
                  <code>new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
</code>
                  <para>This program creates a <embeddedLabel>Security World</embeddedLabel> file at %NFAST_KMDATA%\local\world, which corresponds to the C:\ProgramData\nCipher\Key Management Data\local folder. You can use different values for the quorum but in our example, you’re prompted to enter three blank cards and pins for each one. Then, any two cards will be required to have administrative access to the security world (your specified quorum).  These cards become the <embeddedLabel>Administrator Card Set</embeddedLabel> for the new security world. At this stage, you can specify the password or PIN for each ACS card, or add it later with a command. </para>
                  <alert class="tip">
                    <para>You can verify the current configuration status of your HSM by using the <codeInline>nkminfo</codeInline> command.</para>
                  </alert>
                  <para>Then do the following:</para>
                  <list class="ordered">
                    <listItem>
                      <para>Install the Thales CNG provider as described in the Thales documentation, and configure it to use the new security world. </para>
                    </listItem>
                    <listItem>
                      <para>Back up the world file in <embeddedLabel>%nfast_kmdata%\local</embeddedLabel>. Secure and protect the world file, the Administrator Cards, and their pins, and make sure that no single person has access to more than one card.</para>
                    </listItem>
                  </list>
                </content>
              </section>
              <section address="BKMK_InternetGenerate2">
                <title>Step 2: Validate the downloaded package</title>
                <content>
                  <para>This step is optional but recommended so that you can validate the following:</para>
                  <list class="bullet">
                    <listItem>
                      <para>The Key Exchange Key that is included in the toolset has been generated from a genuine Thales HSM.</para>
                    </listItem>
                    <listItem>
                      <para>The hash of the Azure RMS Security World that is included in the toolset has been generated in a genuine Thales HSM.</para>
                    </listItem>
                    <listItem>
                      <para>The Key Exchange Key is non-exportable.</para>
                    </listItem>
                  </list>
                  <alert class="note">
                    <?Comment CB: 252036 2015-01-16T09:24:00Z  Id='11?>
                    <para>To validate the downloaded package, the HSM must be connected, powered on, and must have a security world on it (such as the one you’ve just created).<?CommentEnd Id='11'
    ?></para>
                  </alert>
                  <procedure>
                    <title>To validate the downloaded package</title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>Run the verifykeypackage.py script by tying one of the following, depending on your region:</para>
                          <list class="bullet">
                            <listItem>
                              <para>For North America:</para>
                              <code>python verifykeypackage.py -k BYOK-KEK-pkg-NA-1 -w BYOK-SecurityWorld-pkg-NA-1</code>
                            </listItem>
                            <listItem>
                              <para>For Europe:</para>
                              <code>python verifykeypackage.py -k BYOK-KEK-pkg-EU-1 -w BYOK-SecurityWorld-pkg-EU-1</code>
                            </listItem>
                            <listItem>
                              <para>For Asia:</para>
                              <code>python verifykeypackage.py -k BYOK-KEK-pkg-AP-1 -w BYOK-SecurityWorld-pkg-AP-1</code>
                            </listItem>
                          </list>
                          <alert class="tip">
                            <para>The Thales software includes a Python interpreter at %NFAST_HOME%\python\bin</para>
                          </alert>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>Confirm that you see the following, which indicates successful validation: <ui>Result:  SUCCESS</ui></para>
                        </content>
                      </step>
                    </steps>
                    <conclusion>
                      <content>
                        <para>This script validates the signer chain up to the Thales root key. The hash of this root key is embedded in the script and its value should be <ui>59178a47 de508c3f 291277ee 184f46c4 f1d9c639</ui>. You can also confirm this value separately by visiting the <externalLink><linkText>Thales website</linkText><linkUri>http://www.thalesesec.com/</linkUri></externalLink>.</para>
                      </content>
                    </conclusion>
                  </procedure>
                  <para>You’re now ready to create a new key that will be your RMS tenant key.</para>
                </content>
              </section>
              <section address="BKMK_InternetGenerate3">
                <title>Step 3: Create a new key</title>
                <content>
                  <para>Generate a CNG key by using the Thales <userInputLocalizable>generatekey</userInputLocalizable> and <userInputLocalizable>cngimport</userInputLocalizable> programs.</para>
                  <para>Run the following command to generate the key:</para>
                  <code>generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
</code>
                  <para>When you run this command, use these instructions:</para>
                  <list class="bullet">
                    <listItem>
                      <para>For the key size, we recommend 2048 but also support 1024-bit RSA keys for existing AD RMS customers who have such keys and are migrating to Azure RMS.</para>
                    </listItem>
                    <listItem>
                      <para>Replace the value of <placeholder>contosokey</placeholder> for the <ui>ident</ui> and <ui>plainname</ui> with any string value. To minimize administrative overheads and reduce the risk of errors, we recommend that you use the same value for both, and use all lower case characters.</para>
                    </listItem>
                    <listItem>
                      <para>The pubexp is left blank (default) in this example, but you can specify specific values. For more information, see the Thales documentation.</para>
                    </listItem>
                  </list>
                  <para>Then run the following command to import the key to CNG:</para>
                  <code>cngimport --import <?Comment CB: should be hyphen, notemdash 2015-01-16T09:24:00Z  Id='12?>-M<?CommentEnd Id='12'
    ?> --key=contosokey --appname=simple contosokey</code>
                  <para>When you run this command, use these instructions:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Replace <placeholder>contosokey</placeholder> with the same value that you specified in <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetGenerate1">Step 1: Create a security world</link> from the <legacyItalic>Generate your tenant key</legacyItalic> section.</para>
                    </listItem>
                    <listItem>
                      <para>Use the <ui>-M</ui> option so that the key is suitable for this scenario. Without this, the resultant key will be a user-specific key for the current user.</para>
                    </listItem>
                  </list>
                  <para>This command creates a Tokenized Key file in your %NFAST_KMDATA%\local folder with a name starting with <ui>key_caping_</ui> followed by a SID. For example: <system>key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb</system>. This file contains an encrypted key.</para>
                  <alert class="tip">
                    <para>You can see the current configuration status of your keys by using the <codeInline>nkminfo –k</codeInline> command.</para>
                  </alert>
                  <para>Back up this Tokenized Key File in a safe location.</para>
                  <alert class="important">
                    <para>When you later transfer your key to Azure RMS, Microsoft cannot export this key back to you so it becomes extremely important that you back up your key and security world safely. Contact Thales for guidance and best practices for backing up your key.</para>
                  </alert>
                  <para>You are now ready to transfer your tenant key to Azure RMS.</para>
                </content>
              </section>
            </sections>
          </section>
          <section address="BKMK_InternetPrepareTransfer">
            <title>Prepare your tenant key for transfer</title>
            <content>
              <para>On the disconnected workstation, following these 4 steps to prepare your own tenant key:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetPrepareTransfer1">Step 1: Create a copy of your key with reduced permissions</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetPrepareTransfer2">Step 2: Inspect the new copy of the key</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetPrepareTransfer3">Step 3: Encrypt your key by using Microsoft’s Key Exchange Key</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetPrepareTransfer4">Step 4: Copy your key transfer package to the Internet-connected workstation </link>
                  </para>
                </listItem>
              </list>
            </content>
            <sections>
              <section address="BKMK_InternetPrepareTransfer1">
                <title>Step 1: Create a copy of your key with reduced permissions</title>
                <content>
                  <para>To reduce the permissions on your tenant key, do the following: </para>
                  <list class="bullet">
                    <listItem>
                      <para>From a command prompt, run one of the following, depending on your region:</para>
                      <list class="bullet">
                        <listItem>
                          <para>For North America:</para>
                          <code>KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1</code>
                        </listItem>
                        <listItem>
                          <para>For Europe:</para>
                          <code>KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1</code>
                        </listItem>
                        <listItem>
                          <para>For Asia:</para>
                          <code>KeyTransferRemote.exe -ModifyAcls -KeyAppName simple -KeyIdentifier contosokey -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1</code>
                        </listItem>
                      </list>
                    </listItem>
                  </list>
                  <para>When you run this command, replace <placeholder>contosokey</placeholder> with the same value you specified in <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetGenerate1">Step 1: Create a security world</link> from the <legacyItalic>Generate your tenant key</legacyItalic> section.</para>
                  <para>You will be asked to plug in your security world ACS cards, and if specified, their password or PIN..</para>
                  <para>When the command completes, you will see <ui>Result: SUCCESS</ui> and the copy of your tenant key with reduced permissions will be in the file named key_xferacId_<placeholder>&lt;contosokey&gt;</placeholder>.</para>
                </content>
              </section>
              <section address="BKMK_InternetPrepareTransfer2">
                <title>Step 2: Inspect the new copy of the key</title>
                <content>
                  <para>Optionally, run the Thales utilities to confirm the minimal permissions on the new tenant key:</para>
                  <list class="bullet">
                    <listItem>
                      <para>aclprint.py:</para>
                      <code>"%nfast_home%\bin\preload.exe" -m 1 -A xferacld -K contosokey "%nfast_home%\python\bin\python" "%nfast_home%\python\examples\aclprint.py"</code>
                    </listItem>
                    <listItem>
                      <para>kmfile-dump.exe:</para>
                      <code>"%nfast_home%\bin\kmfile-dump.exe" "%NFAST_KMDATA%\local\key_xferacld_contosokey"
</code>
                    </listItem>
                  </list>
                  <para>When you run these command, replace <placeholder>contosokey</placeholder> with the same value you specified in <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetGenerate1">Step 1: Create a security world</link> from the <legacyItalic>Generate your tenant key</legacyItalic> section.</para>
                </content>
              </section>
              <section address="BKMK_InternetPrepareTransfer3">
                <title>Step 3: Encrypt your key by using Microsoft’s Key Exchange Key</title>
                <content>
                  <para>Run one of the following commands, depending on your region:</para>
                  <list class="bullet">
                    <listItem>
                      <para>For North America:</para>
                      <code>KeyTransferRemote.exe -Package -KeyIdentifier <placeholder>contosokey</placeholder> -ExchangeKeyPackage BYOK-KEK-pkg-NA-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-NA-1 -TenantBposId <placeholder>GUID</placeholder> -KeyFriendlyName <placeholder>ContosoFirstkey</placeholder></code>
                    </listItem>
                    <listItem>
                      <para>For Europe:</para>
                      <code>KeyTransferRemote.exe -Package -KeyIdentifier <placeholder>contosokey</placeholder> -ExchangeKeyPackage BYOK-KEK-pkg-EU-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-EU-1 -TenantBposId <placeholder>GUID</placeholder> -KeyFriendlyName <placeholder>ContosoFirstkey</placeholder></code>
                    </listItem>
                    <listItem>
                      <para>For Asia:</para>
                      <code>KeyTransferRemote.exe -Package -KeyIdentifier <placeholder>contosokey</placeholder> -ExchangeKeyPackage BYOK-KEK-pkg-AP-1 -NewSecurityWorldPackage BYOK-SecurityWorld-pkg-AP-1 -TenantBposId <placeholder>GUID</placeholder> -KeyFriendlyName <placeholder>ContosoFirstkey</placeholder></code>
                    </listItem>
                  </list>
                  <para>When you run this command, use these instructions:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Replace <placeholder>contosokey</placeholder> with the identifier that you used to generate the key in <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetGenerate1">Step 1: Create a security world</link> from the <legacyItalic>Generate your tenant key</legacyItalic> section.</para>
                    </listItem>
                    <listItem>
                      <para>Replace <placeholder>GUID</placeholder> with your Azure Active Directory tenant ID that you retrieved in <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_PrepareInternetConnectedWorkstation2">Step 2: Get your Azure Active Directory tenant ID</link> from the <legacyItalic>Prepare your Internet-connected workstation</legacyItalic> section.</para>
                    </listItem>
                    <listItem>
                      <para>Replace <placeholder>ContosoFirstKey</placeholder> with a label that will be used for your output file name.</para>
                    </listItem>
                  </list>
                  <para>When this completes successfully it displays <ui>Result: SUCCESS</ui> and there will be a new file in the current folder that has the following name: TransferPackage-<placeholder>ContosoFirstkey</placeholder>.byok</para>
                </content>
              </section>
              <section address="BKMK_InternetPrepareTransfer4">
                <title>Step 4: Copy your key transfer package to the Internet-connected workstation </title>
                <content>
                  <para>Use a USB drive or other portable storage to copy the output file from the previous step (KeyTransferPackage-<placeholder>ContosoFirstkey</placeholder>.byok) to your Internet-connected workstation.</para>
                  <alert class="security note">
                    <para>Use security practices to protect the file because it includes your private key.</para>
                  </alert>
                </content>
              </section>
            </sections>
          </section>
          <section address="BKMK_InternetTransfer">
            <title>Transfer your tenant key to Azure RMS</title>
            <content>
              <para>On the Internet-connected workstation,  follow these 3 steps To transfer your new tenant key to Azure RMS, :</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetTransfer1">Step 1: Connect to Azure RMS</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetTransfer2">Step 2: Upload the key package</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_InternetTransfer3">Step 3: Enumerate your tenant keys – as needed</link>
                  </para>
                </listItem>
              </list>
            </content>
            <sections>
              <section address="BKMK_InternetTransfer1">
                <title>Step 1: Connect to Azure RMS</title>
                <content>
                  <para>Return to the Windows PowerShell window and type the following: </para>
                  <list class="ordered">
                    <listItem>
                      <para>Reconnect to the <token>aad_rightsmanagement_1</token> service:</para>
                      <code>Connect-AadrmService</code>
                    </listItem>
                    <listItem>
                      <para>Use the <externalLink><linkText>Get-AadrmKeys</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629420.aspx</linkUri></externalLink> cmdlet to see your current tenant key configuration:</para>
                      <code>Get-AadrmKeys</code>
                    </listItem>
                  </list>
                </content>
              </section>
              <section address="BKMK_InternetTransfer2">
                <title>Step 2: Upload the key package</title>
                <content>
                  <para>Use the <externalLink><linkText>Add-AadrmKey</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629418.aspx</linkUri></externalLink> cmdlet to upload the key transfer package that you copied from the disconnected workstation:</para>
                  <code>Add-AadrmKey –KeyFile &lt;PathToPackageFile&gt; -Verbose</code>
                  <alert class="warning">
                    <para>You are prompted to confirm this action. It’s important to understand that this action cannot be undone. When you upload a tenant key, it automatically becomes your organization’s primary tenant key and users will start to use this tenant key when they protect documents and files.</para>
                  </alert>
                  <para/>
                  <para>If the upload is successful, you will see the following message: <ui>The Rights management service successfully added the key.</ui></para>
                  <para>Expect a replication delay for the change to propagate to all <token>aad_rightsmanagement_1</token> data centers.</para>
                </content>
              </section>
              <section address="BKMK_InternetTransfer3">
                <title>Step 3: Enumerate your tenant keys – as needed</title>
                <content>
                  <para>Use the Get-AadrmKeys cmdlet again to see the change in your tenant key, and whenever you want to see a list of your tenant keys. The tenant keys displayed include the initial tenant key that Microsoft generated for you, and any tenant keys that you added:</para>
                  <code>Get-AadrmKeys</code>
                  <para>The tenant key that is marked <ui>Active</ui> is the one that your organization is currently using to protect documents and files.</para>
                  <para>You have now completed all the steps required for bring your own key over the Internet and can go to <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_NextSteps">Next steps</link>.</para>
                </content>
              </section>
            </sections>
          </section>
        </sections>
      </section>
      <section address="BKMK_BYOK_InPerson" expanded="false">
        <title>Generate and transfer your tenant key – in person</title>
        <content>
          <para>Use the following procedures if you do not want to transfer your tenant key over the Internet, but instead, transfer your tenant key in person.</para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_GenerateKey">Generate your tenant key</link>
              </para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_Transfer">Transfer your tenant key to Azure RMS</link>
              </para>
            </listItem>
          </list>
        </content>
        <sections>
          <section address="BKMK_GenerateKey">
            <title>Generate your tenant key</title>
            <content>
              <para>To generate your own tenant key, follow these 3 steps: </para>
              <list class="bullet">
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_GenerateYourKey1">Step 1: Prepare a workstation with Thales HSM</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_GenerateYourKey2">Step 2: Create a security world</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_GenerateYourKey3">Step 3: Create a new key</link>
                  </para>
                </listItem>
              </list>
            </content>
            <sections>
              <section address="BKMK_GenerateYourKey1">
                <title>Step 1: Prepare a workstation with Thales HSM</title>
                <content>
                  <para>Install the nCipher (Thales) support software on a Windows computer. Attach a Thales HSM to that computer. Ensure the Thales tools are in your path. For more information, see the user guide included with the Thales HSM, or visit the Thales website for Azure RMS at <externalLink><linkText>http://www.thales-esecurity.com/msrms/cloud</linkText><linkUri>http://www.thales-esecurity.com/msrms/cloud</linkUri></externalLink>.</para>
                </content>
              </section>
              <section address="BKMK_GenerateYourKey2">
                <title>Step 2: Create a security world</title>
                <content>
                  <para>Start a command prompt and run the Thales new-world program.</para>
                  <code>new-world.exe --initialize --cipher-suite=DLf1024s160mRijndael --module=1 --acs-quorum=2/3
</code>
                  <para>This program creates a <embeddedLabel>Security World</embeddedLabel> file at %NFAST_KMDATA%\local\world, which corresponds to the C:\ProgramData\nCipher\Key Management Data\local folder. You can use different values for the quorum but in our example, you’re prompted to enter three blank cards and pins for each one. Then, any two cards will give full access to the security world.  These cards become the <embeddedLabel>Administrator Card Set</embeddedLabel> for the new security world. </para>
                  <para>Then do the following:</para>
                  <list class="ordered">
                    <listItem>
                      <para>Install the Thales CNG provider as described in the Thales documentation, and configure it to use the new security world. </para>
                    </listItem>
                    <listItem>
                      <para>Back up the world file. Secure and protect the world file, the Administrator Cards, and their pins, and make sure that no single person has access to more than one card.</para>
                    </listItem>
                  </list>
                  <para>You’re now ready to create a new key that will be your RMS tenant key.</para>
                </content>
              </section>
              <section address="BKMK_GenerateYourKey3">
                <title>Step 3: Create a new key</title>
                <content>
                  <para>Generate a CNG key by using the Thales <userInputLocalizable>generatekey</userInputLocalizable> and <userInputLocalizable>cngimport</userInputLocalizable> programs.</para>
                  <para>Run the following command to generate the key:</para>
                  <code>generatekey --generate simple type=RSA size=2048 protect=module ident=contosokey plainname=contosokey nvram=no pubexp=
</code>
                  <para>When you run this command, use these instructions:</para>
                  <list class="bullet">
                    <listItem>
                      <para>For the key size, we recommend 2048 but also support 1024-bit RSA keys for existing AD RMS customers who have such keys and are migrating to Azure RMS.</para>
                    </listItem>
                    <listItem>
                      <para>Replace the value of <placeholder>contosokey</placeholder> for the <ui>ident</ui> and <ui>plainname</ui> with any string value. To minimize administrative overheads and reduce the risk of errors, we recommend that you use the same value for both, and use all lower case characters.</para>
                    </listItem>
                    <listItem>
                      <para>The pubexp is left blank (default) in this example, but you can specify specific values. For more information, see the Thales documentation.</para>
                    </listItem>
                  </list>
                  <para>Then run the following command to import the key to CNG:</para>
                  <code>cngimport --import –M --key=contosokey --appname=simple contosokey</code>
                  <para>When you run this command, use these instructions:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Replace <placeholder>contosokey</placeholder> with the same value that you specified in Step 1.</para>
                    </listItem>
                    <listItem>
                      <para>Use the <ui>-M</ui> option so that the key is suitable for this scenario. Without this, the resultant key will be a user-specific key for the current user.</para>
                    </listItem>
                  </list>
                  <para>This command creates a Tokenized Key file in your %NFAST_KMDATA%\local folder with a name starting with <ui>key_caping_</ui> followed by a SID. For example: <system>key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb</system>. This file contains an encrypted key. </para>
                  <para>Back up this Tokenized Key File in a safe location.</para>
                  <alert class="important">
                    <para>When you later transfer your key to Azure RMS, Microsoft will have a non-recoverable copy of your key. This means that nobody can retrieve your key from the HSMs at Microsoft. This allows you to retain exclusive control over your tenant key. Therefore it becomes extremely important that you back up your key and security world safely. Contact Thales for guidance and best practices for backing up your key.</para>
                  </alert>
                  <para>You are now ready to transfer your tenant key to Azure RMS.</para>
                </content>
              </section>
            </sections>
          </section>
          <section address="BKMK_Transfer">
            <title>Transfer your tenant key to Azure RMS</title>
            <content>
              <para>After you have generated your own key, you must transfer it to Azure RMS before you use it. For the highest level of security, this transfer is a manual process that requires you to fly to the Microsoft office in Redmond, Washington, United States of America. To complete this process, follow these 3 steps:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_TransferYourKey1">Step 1: Bring your key to Microsoft</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_TransferYourKey2">Step 2: Transfer your key to the Window Azure RMS security world</link>
                  </para>
                </listItem>
                <listItem>
                  <para>
                    <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_TransferYourKey3">Step 3: Closing procedures</link>
                  </para>
                </listItem>
              </list>
              <procedure address="BKMK_TransferYourKey1">
                <title>Step 1: Bring your key to Microsoft</title>
                <steps class="bullet">
                  <step>
                    <content>
                      <para>Contact Microsoft Customer Support Services (CSS) to schedule a key transfer appointment for Azure RMS. Bring the following to Microsoft in Redmond:</para>
                      <list class="bullet">
                        <listItem>
                          <para>A quorum of your Administrative Cards. If you followed the previous instructions in <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_GenerateYourKey2">Step 2: Create a security world</link>, these are any two of your three cards.</para>
                        </listItem>
                        <listItem>
                          <para>Personnel authorized to carry your Administrative Cards and pins, typically two (one for each card).</para>
                        </listItem>
                        <listItem>
                          <para>Your Security World file (%NFAST_KMDATA%\local\world) on a USB drive.</para>
                        </listItem>
                        <listItem>
                          <para>Your Tokenized Key File on a USB drive.</para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure address="BKMK_TransferYourKey2">
                <title>Step 2: Transfer your key to the Window Azure RMS security world</title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>When you arrive at Microsoft to transfer your key, the following happens:</para>
                      <list class="bullet">
                        <listItem>
                          <para>Microsoft provides you with an offline workstation that has a Thales HSM attached, Thales software installed, and a Azure RMS Security World file pre-loaded into the folder C:\Temp\Destination.</para>
                        </listItem>
                        <listItem>
                          <para>On this workstation, you load your Security World file and Tokenized Key File from your USB drive into the C:\Temp\Source folder.</para>
                        </listItem>
                        <listItem>
                          <para>Azure RMS operators securely transfer your key to the Azure RMS security world by using Thales utilities. </para>
                        </listItem>
                      </list>
                      <para>This process will look similar to the following, where the last parameter of key-xfer-im in this example is replaced by your Tokenized Key File name:</para>
                      <para>
                        <ui>C:\&gt; mk-reprogram.exe --owner c:\Temp\Destination add c:\Temp\Source</ui>
                      </para>
                      <para>
                        <ui>C:\&gt; key-xfer-im.exe c:\Temp\Source c:\Temp\Destination --module c:\Temp\Source\key_caping_machine--801c1a878c925fd9df4d62ba001b94701c039e2fb</ui>
                      </para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>Mk-reprogram will ask you and the Azure RMS operators to plug in their respective Administrator cards and pins. These commands output a Tokenized Key File in C:\Temp\Destination that contains your key protected by Azure RMS security world. </para>
                    </content>
                  </step>
                </steps>
              </procedure>
              <procedure address="BKMK_TransferYourKey3">
                <title>Step 3: Closing procedures</title>
                <steps class="bullet">
                  <step>
                    <content>
                      <para>In your presence, Azure RMS operators do the following:</para>
                      <list class="bullet">
                        <listItem>
                          <para>Run a tool that Microsoft developed in collaboration with Thales that removes two permissions: The permission to recover the key, and the permission to change permissions. After this is done, this copy of your key is locked to the Azure RMS security world. Thales HSMs will not allow Azure RMs operators with their Administrator cards to recover the plaintext copy of your key.</para>
                        </listItem>
                        <listItem>
                          <para>Copy the resulting key file to a USB drive to later upload to the Azure RMS service.</para>
                        </listItem>
                        <listItem>
                          <para>Factory-reset the HSM, and wipe the workstation clean.</para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                </steps>
              </procedure>
              <para>You have now completed all the steps required for bring your own key in person and can return to your organization for the next steps.</para>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section address="BKMK_NextSteps">
    <title>Next steps</title>
    <content>
      <list class="ordered">
        <listItem>
          <para>Start to use your tenant key:</para>
          <list class="bullet">
            <listItem>
              <para>If you haven’t already done so, you must now activate Rights Management so that your organization can start to use RMS. Users immediately start to use your tenant key (managed by Microsoft or managed by you).</para>
              <para>For more information about activation, see <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214">Activating Azure Rights Management</link>.</para>
            </listItem>
            <listItem>
              <para>If you had already activated Rights Management and then decided to manage your own tenant key, users gradually transition from the old tenant key to the new tenant key, and this staggered transition can take a few weeks to complete. Documents and files that were protected with the old tenant key remains accessible to authorized users.</para>
            </listItem>
          </list>
        </listItem>
        <listItem>
          <para>Consider enabling usage logging, which logs every transaction that RMS performs. </para>
          <para>If you decided to manage your own tenant key, logging includes information about using your tenant key. See the following example of a log file displayed in Excel where the <ui>Decrypt</ui> and <ui>SignDigest</ui> Request Types show that the tenant key is being used.</para>
          <mediaLink>
            <image xlink:href="6b958831-fba1-46b6-81c5-f20cf645927a"/>
          </mediaLink>
          <para/>
          <para>For more information about usage logging, see <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e">Log and analyze rights management usage</link>.</para>
        </listItem>
        <listItem>
          <para>Maintain your tenant key.</para>
          <para>For more information, see <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d">Operations for your Rights Management Tenant Key</link>.</para>
        </listItem>
      </list>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring rights management</link>
  </relatedTopics>
</developerConceptualDocument>
