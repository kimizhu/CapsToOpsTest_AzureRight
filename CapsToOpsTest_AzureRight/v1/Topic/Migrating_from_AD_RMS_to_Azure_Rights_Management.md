---
description: na
keywords: na
pagetitle: Migrating from AD RMS to Azure Rights Management
search: na
ms.date: 2015-12-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828cf1f7-d0e7-4edf-8525-91896dbe3172
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# Migrating from AD RMS to Azure Rights Management
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the following set of instructions to  migrate your Active Directory Rights Management Services (AD RMS) deployment to Azure Rights Management (Azure RMS). After the migration, users will still have access to documents and email messages that your organization protected by using AD RMS, and newly protected content will use Azure RMS.</para>
    <para>Not sure whether this AD RMS migration is right for your organization? </para>
  <list class="bullet"><listItem><para>For an introduction to Azure RMS,  the business problems that it can solve, what it looks like to administrators and users, and how it works, see <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link></para></listItem><listItem><para>For a comparison of Azure RMS with AD RMS, see <link xlink:href="8123bd62-1814-4d79-b306-e20c1a00e264">Comparing Azure Rights Management and AD RMS</link>.</para></listItem></list></introduction>
  <section>
    <title>Prerequisites for migrating AD RMS to Azure RMS</title>
    <content>
      <para>Before you start the migration to Azure RMS, make sure that the following prerequisites are in place and that you understand any limitations.</para>
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
              <para>A supported RMS deployment</para>
            </TD>
            <TD>
              <para>All releases of AD RMS from Windows Server 2008 through Windows Server 2012 R2 support a migration to Azure RMS:</para>
              <list class="bullet">
                <listItem>
                  <para>Windows Server 2008 (x86 or x64)</para>
                </listItem>
                <listItem>
                  <para>Windows Server 2008 R2 (x64)</para>
                </listItem>
                <listItem>
                  <para>Windows Server 2012 (x64)</para>
                </listItem>
                <listItem>
                  <para>Windows Server 2012 R2 (x64)</para>
                </listItem>
              </list>
              <alert class="note">
                <para>If you are running Windows RMS on Windows Server 2003, this version of the operating system will be out of support during 2015. You can migrate this version of RMS to Azure RMS, but this process is supported only if the operating system is still supported. As a workaround, you could import your trusted publishing domain (TPD) to a version of AD RMS that is supported, and then re-import the TPD without the RMS 1.0 compatibility option. For more information about TPDs, see <externalLink><linkText>Trusted Publishing Domain</linkText><linkUri>http://technet.microsoft.com/library/dd996639(v=ws.10).aspx</linkUri></externalLink></para>
              </alert>
              <para>All valid AD RMS topologies are supported:</para>
              <list class="bullet">
                <listItem>
                  <para>Single forest, single RMS cluster</para>
                </listItem>
                <listItem>
                  <para>Single forest, multiple licensing-only RMS clusters</para>
                </listItem>
                <listItem>
                  <para>Multiple forests, multiple RMS clusters</para>
                </listItem>
              </list>
              <alert class="note">
                <para>By default, multiple RMS clusters migrate to a single Azure RMS tenant. If you want different RMS tenants, you must treat them as different migrations. A key from one RMS cluster cannot be imported to more than one Azure RMS tenant.</para>
              </alert>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>All requirements to run Azure RMS, including an Azure RMS tenant (not activated)</para>
            </TD>
            <TD>
              <para>See <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link>.</para>
              <para>Although you must have an Azure RMS tenant before you can migrate from AD RMS, we recommend that you do not activate the Rights Management service before the migration. The migration process includes this step after you have exported keys and templates from AD RMS and imported them to Azure RMS. However, if Azure RMS is already activated, you can still migrate from AD RMS.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Preparation for Azure RMS:</para>
              <list class="bullet">
                <listItem>
                  <para>Directory synchronization between your on-premises directory and Azure Active Directory</para>
                </listItem>
                <listItem>
                  <para>Mail-enabled groups in Azure Active Directory</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <para>See <link xlink:href="afbca2d6-32a7-4bda-8aaf-9f93f5da5abc">Preparing for Azure Rights Management</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>If you have used the Information Rights Management (IRM) functionality of Exchange Server (for example, transport rules and Outlook Web Access) or SharePoint Server with AD RMS:</para>
              <list class="bullet">
                <listItem>
                  <para>Plan for a short period of time when IRM will not be available on these servers</para>
                </listItem>
              </list>
            </TD>
            <TD>
              <para>You can continue to use IRM on these servers with Azure RMS after the migration. However, one of the migration steps is to temporarily disable the IRM service, install and configure a connector, reconfigure the servers, and then re-enable IRM. </para>
              <para>This is the only interruption to service during the migration process.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Limitations:</para>
      <list class="bullet">
        <listItem>
          <para>Although the migration process supports migrating your server licensing certificate (SLC) key to a hardware security module (HSM) for Azure RMS, Exchange Online does not currently support this configuration. If you want full IRM functionality with Exchange Online after you migrate to Azure RMS, your Azure RMS tenant key must be <externalLink><linkText>managed by Microsoft</linkText><linkUri>http://technet.microsoft.com/library/dn440580.aspx</linkUri></externalLink>. Alternatively, you can run IRM with reduced functionality in Exchange Online  when your Azure RMS tenant is managed by you (BYOK). For more information about using Exchange Online with Azure RMS, see <link xlink:href="#BKMK_Step6Migration">Step 6. Configure IRM integration for Exchange Online</link> in these instructions.</para>
        </listItem>
        <listItem>
          <para>If you have software and clients that are not supported with Azure RMS, they will not be able to protect or consume content that is protected by Azure RMS. Be sure to check the supported applications and clients section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic.</para>
        </listItem>
        <listItem>
          <para>If you import your on-premises key to Azure RMS as archived (you do not set the TPD to be the active during the import process) and you migrate users in batches for a phased migration, content that is newly protected by the migrated users will not be accessible to users who remain on AD RMS. In this scenario, whenever  possible, keep the migration time short and migrate users in logical batches such that if they collaborate with one another, they are migrated together. </para>
          <para>This limitation does not apply when you set the TPD to active during the import process, because all users will protect content by using the same key. We recommend this configuration because it lets you migrate all users independently and at your own pace.</para>
        </listItem>
        <listItem>
          <para>If you collaborate with external partners (for example, by using trusted user domains or federation), they must also migrate to Azure RMS either at the same time as your migration, or as soon as possible afterwards. To continue to access content that your organization previously protected by using AD RMS, they must make client configuration changes that are similar to those that you make, and included in this document. </para>
          <para>Because of the possible configuration variations that your partners might have, exact instructions for this reconfiguration are out of scope for this document. For help, contact Microsoft Customer Support Services (CSS).</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Steps for migrating AD RMS to Azure RMS</title>
    <content>
      <para/>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Migration step</para>
            </TD>
            <TD>
              <para>More information</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>
                <embeddedLabel>1. Download the Azure RMS Management Administration Tools</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>For instructions, see <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172#BKMK_Step1Migration">Step 1: Download the Azure Rights Management Administration Tool</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>2. Export configuration data from AD RMS and import it to Azure RMS</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>You export the configuration data (keys, templates, URLs) from AD RMS to an XML file, and then upload that file to Azure RMS by using the Import-AadrmTpd Windows PowerShell cmdlet. Additional steps might be needed, depending your on AD RMS key configuration:</para>
              <list class="bullet">
                <listItem>
                  <para>Software-protected key to software-protected key migration: Centrally managed, password-based keys in AD RMS to Microsoft-managed Azure RMS tenant key. This is the simplest migration path and no additional steps are required.</para>
                </listItem>
                <listItem>
                  <para>HSM-protected  key to HSM-protected key migration: Keys that are stored by an HSM for AD RMS to customer-managed Azure RMS tenant key (the “bring your own key” or BYOK scenario). This requires additional steps to transfer the key from your on-premises Thales HSM to the Azure RMS HSM.</para>
                </listItem>
                <listItem>
                  <para>Software-protected key to HSM-protected key migration: Centrally managed, password-based keys in AD RMS to customer-managed Azure RMS tenant key (the “bring your own key” or BYOK scenario). This requires the most configuration because you must first extract your software key and import it to an on-premises HSM, and then do the additional steps to transfer the key from your on-premises Thales HSM to the Azure RMS HSM.</para>
                </listItem>
              </list>
              <para>For instructions, see <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172#BKMK_Step2Migration">Step 2. Export configuration data from AD RMS and import it to Azure RMS</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>3. Activate your RMS tenant</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>If possible, do this step after the import process and not before.</para>
              <para>For more information and instructions, see <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172#BKMK_Step3Migration">Step 3. Activate your RMS tenant</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>4. Configure imported templates</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>When you import your rights policy templates, their status is archived. If you want users to be able to see and use them, you must change the template status to published in the Azure classic portal.</para>
              <para>For instructions, see <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172#BKMK_Step4Migration">Step 4. Configure imported templates</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>5. Reconfigure clients to use Azure RMS</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>Existing Windows computers must be reconfigured to use the Azure RMS service instead of AD RMS. This step applies to computers in your organization, and to computers in partner organizations if you have collaborated with them while you were running AD RMS.</para>
              <para>In addition, if you have deployed the <externalLink><linkText>mobile device extensions</linkText><linkUri>http://technet.microsoft.com/library/dn673574.aspx</linkUri></externalLink> to support mobile devices such as iOS phones and iPads, Android phones and tablets, Windows phone, and Mac computers, you must remove the SRV records in DNS that redirected these clients to use AD RMS.</para>
              <para>For instructions, see <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172#BKMK_Step5Migration">Step 5. Reconfigure clients to use Azure RMS</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>6. Configure IRM integration with Exchange Online</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>This step is required if you want to use Exchange Online with Azure RMS.</para>
              
              <para>For instructions, see <link xlink:href="#BKMK_Step6Migration">Step 6. Configure IRM integration for Exchange Online</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>7. Deploy the RMS connector</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>This step is required if you want to use any of the following on-premises services with Azure RMS:</para>
              <list class="bullet">
                <listItem>
                  <para>Exchange Server (for example, transport rules and Outlook Web Access)</para>
                </listItem>
                <listItem>
                  <para>SharePoint Server </para>
                </listItem>
                <listItem>
                  <para>Windows Server that runs File Classification Infrastructure</para>
                </listItem>
              </list>
              <para>For instructions, see <link xlink:href="#BKMK_Step7Migration">Step 7. Deploy the RMS connector</link>.</para>
            </TD>
          </tr><tr>
            <TD>
              <para>
                <embeddedLabel>8. Decommission AD RMS</embeddedLabel> </para>
            </TD>
            <TD>
              <para>When you have confirmed that all clients are using Azure RMS and no longer accessing the AD RMS servers, you can decommission your AD RMS deployment.</para>
              <para>For instructions, see <link xlink:href="#BKMK_Step8Migration">Step 8. Decommission AD RMS</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>
                <embeddedLabel>9. Re-key your Azure RMS tenant key</embeddedLabel>
              </para>
            </TD>
            <TD>
              <para>This step is required if you were not running in Cryptographic Mode 2 before the migration, and optional but recommended for all migrations to help safeguard the security of your Azure RMS tenant key.</para>
              <para>For instructions, see <link xlink:href="#BKMK_Step9Migration">Step 9. Re-key your Azure RMS tenant key</link>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
    <sections>
      <section address="BKMK_Step1Migration">
        <title>Step 1: Download the Azure Rights Management Administration Tool</title>
        <content>
          <para>Go to the Microsoft Download Center and download the <externalLink><linkText>Azure Rights Management Administration Tool</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=257721</linkUri></externalLink>, which contains the Azure RMS administration module for Windows PowerShell. </para>
        </content>
      </section>
      <section address="BKMK_Step2Migration">
        <title>Step 2. Export configuration data from AD RMS and import it to Azure RMS</title>
        <content>
          <para>This step is a two-part process:</para>
          <list class="ordered">
            <listItem>
              <para>Export the configuration data from AD RMS by exporting the trusted publishing domains (TPDs) to an .xml file. This process is the same for all migrations.</para>
            </listItem>
            <listItem>
              <para>Import the configuration data to Azure RMS. There are different processes for this step, depending on your current AD RMS deployment configuration and your preferred topology for your Azure RMS tenant key.</para>
            </listItem>
          </list>
        </content>
        <sections>
          <section>
            <title>Export the configuration data from AD RMS</title>
            <content>
              <para>Do the following procedure on all AD RMS clusters, for all trusted publishing domains that have protected content for your organization. You do not need to run this on licensing-only clusters.</para>
              <alert class="note">
                <para>If you are using Windows Server 2003 Rights Management, instead of these instructions, follow the procedure <externalLink><linkText>Export SLC, TUD, TPD and RMS private key</linkText><linkUri>http://technet.microsoft.com/library/jj835767(v=ws.10).aspx</linkUri></externalLink> from the <externalLink><linkText>Migrating from Windows RMS to AD RMS in a Different Infrastructure</linkText><linkUri>http://technet.microsoft.com/library/jj835767(v=ws.10).aspx</linkUri></externalLink> topic.</para>
              </alert>
              <procedure>
                <title>To export the configuration data (trusted publishing domain information)</title>
                <steps class="ordered">
                  <step>
                    <content>
                      <para>Log on the AD RMS cluster as a user with AD RMS administration permissions.</para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>From the AD RMS management console (<ui>Active Directory Rights Management Services</ui>), expand the AD RMS cluster name, expand <ui>Trust Policies</ui>, and then click <ui>Trusted Publishing Domains</ui>.</para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>In the results pane, select the trusted publishing domain, and then, from the Actions pane, click <ui>Export Trusted Publishing Domain</ui>.</para>
                    </content>
                  </step>
                  <step>
                    <content>
                      <para>In the <ui>Export Trusted Publishing Domain</ui> dialog box: </para>
                      <list class="bullet">
                        <listItem>
                          <para>Click <ui>Save As</ui> and save to path and a file name of your choice. Make sure to specify <userInput>.xml</userInput> as the file name extension (this is not appended automatically).</para>
                        </listItem>
                        <listItem>
                          <para>Specify and confirm a strong password. Remember this password, because you will need it later, when you import the configuration data to Azure RMS.</para>
                        </listItem>
                        <listItem>
                          <para>Do not select the checkbox to save the trusted domain file in RMS version 1.0.</para>
                        </listItem>
                      </list>
                    </content>
                  </step>
                </steps>
                <conclusion>
                  <content>
                    <para>When you have exported all the trusted publishing domains, you’re ready to start the procedure to import this data to Azure RMS.</para>
                  </content>
                </conclusion>
              </procedure>
            </content>
          </section>
          <section>
            <title>Import the configuration data to Azure RMS</title>
            <content>
              <para>The exact procedures for this step depend on your current AD RMS deployment configuration, and your preferred topology for your Azure RMS tenant key. </para>
              <para>Your current AD RMS deployment will be using one of the following configurations for your server licensor certificate (SLC) key:</para>
              <list class="bullet">
                <listItem>
                  <para>Password protection in the AD RMS database. This is the default configuration.</para>
                </listItem>
                <listItem>
                  <para>HSM protection by using a Thales hardware security module (HSM).</para>
                </listItem>
                <listItem>
                  <para>HSM protection by using a hardware security module (HSM) from a supplier other than Thales.</para>
                </listItem>
                <listItem>
                  <para>Password protected by using an external cryptographic provider.</para>
                </listItem>
              </list>
              <alert class="note">
                <para>For more information about using hardware security modules with AD RMS, see <externalLink><linkText>Using AD RMS with Hardware Security Modules</linkText><linkUri>http://technet.microsoft.com/library/jj651024.aspx</linkUri></externalLink>.</para>
              </alert>
              <para>The two Azure RMS tenant key topology options are: Microsoft manages your tenant key (<embeddedLabel>Microsoft-managed</embeddedLabel>) or you manage your tenant key (<embeddedLabel>customer-managed</embeddedLabel>). When you manage your own Azure RMS tenant key, it’s sometimes referred to as “bring your own key” (BYOK) and requires a hardware security module (HSM) from Thales. For more information, see the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_ChooseTenantKey">Choose your tenant key topology: Managed by Microsoft (the default) or managed by you (BYOK)</link> section in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and Implementing Your Azure Rights Management Tenant Key</link> topic.</para>
              <alert class="important">
 <para> Exchange Online is not currently  compatible with Azure RMS BYOK.  If you want to use BYOK after your migration and plan to use Exchange Online, make sure that you understand how this configuration reduces IRM functionality for Exchange Online. Review  the information in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_Pricing">BYOK pricing and restrictions</link> section in the  <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and Implementing Your Azure Rights Management Tenant Key</link> topic to help you choose the best Azure RMS tenant key topology for your migration.</para>
</alert><para>Use the following table to identify which procedure to use for your migration. Combinations that are not listed are not supported.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Current AD RMS deployment</para>
                    </TD>
                    <TD>
                      <para>Chosen Azure RMS tenant key topology</para>
                    </TD>
                    <TD>
                      <para>Migration instructions</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>Password protection in the AD RMS database</para>
                    </TD>
                    <TD>
                      <para>Microsoft-managed</para>
                    </TD>
                    <TD>
                      <para>See the <embeddedLabel>Software-protected key to software-protected key migration</embeddedLabel> procedure after this table.</para>
                      <para>This is the simplest migration path and requires only that you transfer your configuration data to Azure RMS.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>HSM protection by using a Thales nShield hardware security module (HSM)</para>
                    </TD>
                    <TD>
                      <para>Customer-managed (BYOK)</para>
                    </TD>
                    <TD>
                      <para>See the <embeddedLabel>HSM-protected key to HSM-protected key migration</embeddedLabel> procedure after this table.</para>
                      <para>This requires the BYOK toolset and two set of steps to transfer the key from your on-premises HSM to the Azure RMS HSMs and then transfer your configuration data to Azure RMS.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Password protection in the AD RMS database</para>
                    </TD>
                    <TD>
                      <para>Customer-managed (BYOK)</para>
                    </TD>
                    <TD>
                      <para>See the <embeddedLabel>Software-protected key to HSM-protected key migration</embeddedLabel> procedure after this table.</para>
                      <para>This requires the BYOK toolset and three sets of steps to first extract your software key and import it to an on-premises HSM, then transfer the key from your on-premises HSM to the Azure RMS HSMs, and finally transfer your configuration data to Azure RMS.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>HSM protection by using a hardware security module (HSM) from a supplier other than Thales</para>
                    </TD>
                    <TD>
                      <para>Customer-managed (BYOK)</para>
                    </TD>
                    <TD>
                      <para>Contact the supplier for you HSM for instructions how to transfer your key from this HSM to a Thales nShield Hardware Security Module (HSM). Then follow the instructions for the <embeddedLabel>HSM-protected key to HSM-protected key migration</embeddedLabel> procedure after this table.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>Password protected by using an external cryptographic provider</para>
                    </TD>
                    <TD>
                      <para>Customer-managed (BYOK)</para>
                    </TD>
                    <TD>
                      <para>Contact the supplier for you cryptographic provider for instructions how to transfer your key to a Thales nShield hardware security module (HSM). Then follow the instructions for the <embeddedLabel>HSM-protected key to HSM-protected key migration</embeddedLabel> procedure after this table.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <para>Before you start these procedures, make sure that you can access the .xml files that you created earlier when you exported the trusted publishing domains. For example, these might be saved to a USB thumb drive that you move from the AD RMS server to the Internet-connected workstation.</para>
              <alert class="security note">
                <para>However you store these files, use security best practices to protect them because this data includes your private key.</para>
              </alert>
            </content>
            <sections>
              <section expanded="false">
                <title>Software-protected key to software-protected key migration</title>
                <content>
                  <para>Use this procedure to import the AD RMS configuration to Azure RMS, to result in your Azure RMS tenant key that is managed by Microsoft.  </para>
                  <procedure>
                    <title>To import the configuration data to Azure RMS</title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>On an Internet-connected workstation, download and install the Windows PowerShell module for Azure RMS (minimum version 2.1.0.0), which includes the <externalLink><linkText>Import-AadrmTpd</linkText><linkUri>http://msdn.microsoft.com/library/azure/dn857523.aspx</linkUri></externalLink> cmdlet. </para>
                          <alert class="tip">
                            <para>If you have previously downloaded and installed the module, check the version number by running: <codeInline>(Get-Module aadrm -ListAvailable).Version</codeInline></para>
                          </alert>
                          <para>For installation instructions, see <link xlink:href="0d665ed6-b1de-4d63-854a-bc57c1c49844">Installing Windows PowerShell for Azure Rights Management</link>.</para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>Start Windows PowerShell with the <ui>Run as administrator</ui> option and use the <externalLink><linkText>Connect-AadrmService</linkText><linkUri>http://msdn.microsoft.com/library/azure/dn629415.aspx</linkUri></externalLink> cmdlet to connect to the Azure RMS service:</para>
                          <code>Connect-AadrmService</code>
                          <para>When prompted, enter your <token>aad_rightsmanagement_1</token> tenant administrator credentials (typically, you will use an account that is a global administrator for Azure Active Directory or Office 365).</para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>Use the <externalLink><linkText>Import-AadrmTpd</linkText><linkUri>http://msdn.microsoft.com/library/azure/dn857523.aspx</linkUri></externalLink> cmdlet to upload the first exported trusted publishing domain (.xml) file. If you have more than one .xml file because you had multiple trusted publishing domains, choose the file that contains the exported trusted publishing domain that you want to use in Azure RMS to protect content after the migration. Use the following command:</para>
                          <code>Import-AadrmTpd -TpdFile &lt;PathToTpdPackageFile&gt; -ProtectionPassword -Active $True -Verbose 
</code>
                          <para>For example: <userInput>Import-AadrmTpd -TpdFile E:\contosokey1.xml -ProtectionPassword -Active $true -Verbose</userInput></para>
                          <para>When prompted, enter the password that you specified earlier, and confirm that you want to perform this action.</para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>When the command completes, repeat step 3 for each remaining  .xml file that you created by exporting your trusted publishing domains. But for these files, set <userInput>-Active</userInput> to <userInput>false</userInput> when you run the Import command. For example: <userInput>Import-AadrmTpd -TpdFile E:\contosokey2.xml -ProtectionPassword -Active $false -Verbose</userInput></para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>Use the <externalLink><linkText>Disconnect-AadrmService</linkText><linkUri>http://msdn.microsoft.com/library/azure/dn629416.aspx</linkUri></externalLink> cmdlet to disconnect from the Azure RMS service:</para>
                          <code>Disconnect-AadrmService</code>
                        </content>
                      </step>
                    </steps>
                    <conclusion>
                      <content>
                        <para>You’re now ready to go to <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172#BKMK_Step3Migration">Step 3. Activate your RMS tenant</link>.</para>
                      </content>
                    </conclusion>
                  </procedure>
                </content>
              </section>
              <section expanded="false">
                <title>HSM-protected key to HSM-protected key migration</title>
                <content>
                  <para>It’s a two-part procedure to import your HSM key and AD RMS configuration to Azure RMS, to result in your Azure RMS tenant key that is managed by you (BYOK).</para>
                  <para>You must first package your HSM key so it's ready to transfer to Azure RMS, and then import it with the configuration data.</para>
                  <procedure>
                    <title>Part 1: Package your HSM key so it's ready to transfer to Azure RMS</title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>Follow the steps in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_ImplementBYOK">Implementing bring your own key (BYOK)</link> section of the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and Implementing Your Azure Rights Management Tenant Key</link>, using the procedure <embeddedLabel>Generate and transfer your tenant key – over the Internet</embeddedLabel> with the following exceptions:</para>
                          <list class="bullet">
                            <listItem>
                              <para>Do not follow the steps for <embeddedLabel>Generate your tenant key</embeddedLabel>, because you already have the equivalent from your AD RMS deployment. You must identify the key used by your AD RMS server from the Thales installation and use this key during the migration. Thales encrypted key files are usually named <ui>key_(keyAppName)_(keyIdentifier)</ui> locally on the server.</para>
                            </listItem>
                          <listItem><para>Do not follow the steps for <embeddedLabel>Transfer your tenant key to Azure RMS</embeddedLabel>, which uses the  Add-AadrmKey command.  Instead, you will transfer your prepared HSM key when you upload your exported trusted publishing domain, by using the Import-AadrmTpd command.</para></listItem></list>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>On the Internet-connected workstation, in Windows PowerShell session, reconnect to the Azure RMS service.</para>
                        </content>
                      </step>
                    </steps>
                    <conclusion>
                      <content>
                        <para>Now that you’ve prepared your HSM key for Azure RMS, you’re ready to import your HSM key file and AD RMS configuration data. </para>
                      </content>
                    </conclusion>
                  </procedure>
                  <procedure>
                    <title>Part 2: Import the HSM key and configuration data to Azure RMS</title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>Still on the Internet-connect workstation and in the Windows PowerShell session, upload the first exported trusted publishing domain (.xml) file. If you have more than one .xml file because you had multiple trusted publishing domains, choose the file that contains the exported trusted publishing domain that corresponds to the HSM key you want to use in Azure RMS to protect content after the migration. Use the following command:</para>
                          <code>Import-AadrmTpd -TpdFile &lt;PathToTpdPackageFile&gt; -ProtectionPassword -HsmKeyFile &lt;PathToBYOKPackage&gt; -Active $True -Verbose</code>
                          <para>For example: <userInput>Import -TpdFile E:\no_key_tpd_contosokey1.xml  -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $true -Verbose</userInput></para>
                          <para>When prompted, enter the password that you specified earlier, and confirm that you want to perform this action. </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>When the command completes, repeat step 1 for each remaining  .xml file that you created by exporting your trusted publishing domains. But for these files, set <userInput>-Active</userInput> to <userInput>false</userInput> when you run the Import command.  For example: <userInput>Import -TpdFile E:\contosokey2.xml -HsmKeyFile E:\KeyTransferPackage-contosokey.byok -ProtectionPassword -Active $false -Verbose</userInput></para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>Use the <externalLink><linkText>Disconnect-AadrmService</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629416.aspx</linkUri></externalLink> cmdlet to disconnect from the Azure RMS service:</para>
                          <code>Disconnect-AadrmService</code>
                        </content>
                      </step>
                    </steps>
                    <conclusion>
                      <content>
                        <para>You’re now ready to go to <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172#BKMK_Step3Migration">Step 3. Activate your RMS tenant</link>.</para>
                      </content>
                    </conclusion>
                  </procedure>
                </content>
              </section>
              <section expanded="false">
                <title>Software-protected key to HSM-protected key migration</title>
                <content>
                  <para>It’s a three-part procedure to import the AD RMS configuration to Azure RMS, to result in your Azure RMS tenant key that is managed by you (BYOK).</para>
                  <para>You must first extract your server licensor certificate (SLC) key from the configuration data and transfer the key to an on-premises Thales HSM, then package and transfer your HSM key to Azure RMS, and then import the configuration data.</para>
                  <procedure>
                    <title>Part 1: Extract your SLC from the configuration data and import the key to your on-premises HSM</title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>Use the following steps in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_ImplementBYOK">Implementing bring your own key (BYOK)</link> section of the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and Implementing Your Azure Rights Management Tenant Key</link> topic:</para>
                          <list class="bullet">
                            <listItem>
                              <para>
                                <embeddedLabel>Generate and transfer your tenant key – over the Internet</embeddedLabel>: <embeddedLabel>Prepare your Internet-connected workstation</embeddedLabel></para>
                            </listItem>
                            <listItem>
                              <para>
                                <embeddedLabel>Generate and transfer your tenant key – over the Internet</embeddedLabel>: <embeddedLabel>Prepare your disconnected workstation</embeddedLabel></para>
                            </listItem>
                          </list>
                          <para>Do not follow the steps to generate your tenant key, because you already have the equivalent in the exported configuration data (.xml) file. Instead, you will run a command to extract this key from the file and import it to your on-premises HSM. </para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>On the disconnected workstation, run the following command:</para>
                          <code>KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath &lt;TPD&gt; -ProtectionPassword -KeyIdentifier &lt;KeyID&gt; -ExchangeKeyPackage &lt;BYOK-KEK-pka-Region&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-Region&gt;</code>
                          <para>For example, for North America: <userInput>KeyTransferRemote.exe -ImportRmsCentrallyManagedKey -TpdFilePath E:\contosokey1.xml -ProtectionPassword -KeyIdentifier contosorms1key –- -ExchangeKeyPackage &lt;BYOK-KEK-pka-NA-1&gt; -NewSecurityWorldPackage &lt;BYOK-SecurityWorld-pkg-NA-1&gt;</userInput></para>
                          <para>Additional information:</para>
                          <list class="bullet">
                            <listItem>
                              <para>The ImportRmsCentrallyManagedKey parameter indicates that the operation is to import the SLC key.</para>
                            </listItem>
                            <listItem>
                              <para>If you don’t specify the password in the command, you will be prompted to specify it.</para>
                            </listItem>
                            <listItem>
                              <para>The KeyIdentifier parameter is for a key friendly name that creates the key file name. You must use only lower-case ASCII characters.</para>
                            </listItem>
                            <listItem>
                              <para>The ExchangeKeyPackage parameter specifies a region-specific key exchange key (KEK) package that has a name beginning with BYOK-KEK-pkg-.</para>
                            </listItem>
                            <listItem>
                              <para>The NewSecurityWorldPackage parameter specifies a region-specific security world package that has a name beginning with BYOK-SecurityWorld-pkg-.</para>
                            </listItem>
                          </list>
                          <para>This command results in the following:</para>
                          <list class="bullet">
                            <listItem>
                              <para>An HSM key file: %NFAST_KMDATA%\local\key_mscapi_&lt;KeyID&gt;</para>
                            </listItem>
                            <listItem>
                              <para>RMS configuration data file with the SLC removed: %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml</para>
                            </listItem>
                          </list>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>If you have more than one RMS configuration data files, repeat step 2 for the remainder of these files.</para>
                        </content>
                      </step>
                    </steps>
                    <conclusion>
                      <content>
                        <para>Now that your SLC has been extracted so that it’s an HSM-based key, you’re ready to package and transfer it to Azure RMS.</para>
                      </content>
                    </conclusion>
                  </procedure>
                  <procedure>
                    <title>Part 2: Package and transfer your HSM key to Azure RMS</title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>Use the following steps from the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_ImplementBYOK">Implementing bring your own key (BYOK)</link> section of the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and Implementing Your Azure Rights Management Tenant Key</link>:</para>
                          <list class="bullet">
                            <listItem>
                              <para>
                                <embeddedLabel>Generate and transfer your tenant key – over the Internet</embeddedLabel>: <embeddedLabel>Prepare your tenant key for transfer</embeddedLabel></para>
                            </listItem>
                            <listItem>
                              <para>
                                <embeddedLabel>Generate and transfer your tenant key – over the Internet</embeddedLabel>: <embeddedLabel>Transfer your tenant key to Azure RMS</embeddedLabel></para>
                            </listItem>
                          </list>
                        </content>
                      </step>
                    </steps>
                    <conclusion>
                      <content>
                        <para>Now that you’ve transferred your HSM key to Azure RMS, you’re ready to import your AD RMS configuration data, which contains only a pointer to the newly transferred tenant key.</para>
                      </content>
                    </conclusion>
                  </procedure>
                  <procedure>
                    <title>Part 3: Import the configuration data to Azure RMS</title>
                    <steps class="ordered">
                      <step>
                        <content>
                          <para>Still on the Internet-connected workstation and in the Windows PowerShell session, copy over the RMS configuration files with the SLC removed (from the disconnected workstation, %NFAST_KMDATA%\local\no_key_tpd_&lt;KeyID&gt;.xml)</para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>Upload the first file. If you have more than one .xml file because you had multiple trusted publishing domains, choose the file that contains the exported trusted publishing domain that corresponds to the HSM key you want to use in Azure RMS to protect content after the migration. Use the following command:</para>
                          <code>Import-AadrmTpd -TpdFile &lt;PathToNoKeyTpdPackageFile&gt; -ProtectionPassword -HsmKeyFile &lt;PathToKeyTransferPackage&gt; -Active $true -Verbose </code>
                          <para>For example: <userInput>Import -TpdFile E:\no_key_tpd_contosorms1key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $true -Verbose </userInput></para>
                          <para>When prompted, enter the password that you specified earlier, and confirm that you want to perform this action.</para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>When the command completes, repeat step 2 for each remaining  .xml file that you created by exporting your trusted publishing domains. But for these files, set <userInput>-Active</userInput> to <userInput>false</userInput> when you run the Import command. For example: <userInput>Import -TpdFile E:\no_key_tpd_contosorms2key.xml -ProtectionPassword -HsmKeyFile E:\KeyTransferPackage-contosorms1key.byok -Active $false -Verbose </userInput></para>
                        </content>
                      </step>
                      <step>
                        <content>
                          <para>Use the <externalLink><linkText>Disconnect-AadrmService</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629416.aspx</linkUri></externalLink> cmdlet to disconnect from the Azure RMS service:</para>
                          <code>Disconnect-AadrmService</code>
                        </content>
                      </step>
                    </steps>
                    <conclusion>
                      <content>
                        <para>You’re now ready to go to <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172#BKMK_Step3Migration">Step 3. Activate your RMS tenant</link>.</para>
                      </content>
                    </conclusion>
                  </procedure>
                </content>
              </section>
            </sections>
          </section>
        </sections>
      </section>
      <section address="BKMK_Step3Migration">
        <title>Step 3. Activate your RMS tenant</title>
        <content>
          <para>Instructions  for this step are fully covered in the <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214">Activating Azure Rights Management</link> topic.</para>
          <alert class="tip">
            <para>If you have an Office 365 subscription, you can activate Azure RMS from the Office 365 admin center or the Azure classic portal. We recommend that you use the Azure classic portal because you will use this management portal to complete the next step.</para>
          </alert>
          <para>
            <embeddedLabel>What if your Azure RMS tenant is already activated?</embeddedLabel> If the Azure RMS service is already activated for your organization, users might have already used Azure RMS to protect content with an automatically generated tenant key (and the default templates) rather than your existing keys (and templates) from AD RMS. This is unlikely to happen on computers that are well-managed on your intranet, because they will be automatically configured for your AD RMS infrastructure. But it can happen on workgroup computers or computers that infrequently connect to your intranet. Unfortunately, it’s also difficult to identify these computers, which is why we recommend you do not activate the service before you import the configuration data from AD RMS. </para>
          <para>If your Azure RMS tenant is already activated and you can identify these computers, make sure that you run the CleanUpRMS_RUN_Elevated.cmd script on these computers, as described in Step 5. Running this script forces them to reinitialize the user environment, so that they download the updated tenant key and imported templates.</para>
        </content>
      </section>
      <section address="BKMK_Step4Migration">
        <title>Step 4. Configure imported templates</title>
        <content>
          <para>Because the templates that you imported have a default state of <ui>Archived</ui>, you must change this state to be <ui>Published</ui> if you want users to be able to use these templates with Azure RMS. </para>
          <para>In addition, if your templates in AD RMS used the <ui>ANYONE</ui> group, this group is automatically removed  when you import the templates to Azure RMS; you must manually add the equivalent group or users and the same rights to the imported templates. The equivalent group for Azure RMS is named <system>AllStaff-&lt;tenant_GUID&gt;@&lt;tenant_name&gt;.onmicrosoft.com</system>. For example, this group might look like the following for Contoso: <system>AllStaff-9c11c87a-ac8b-46a3-8d5c-f4d0b72ee29a@contoso.onmicrosoft.com</system>. </para><para>If  you're not sure whether your AD RMS templates include the ANYONE group, expand the  <link xlink:href="#BKMK_ScriptForANYONE">PowerShell script to identify AD RMS templates that include the ANYONE group</link> section in this step to copy and use the sample PowerShell script to identify these templates. For more information about using Windows PowerShell with AD RMS, see  <externalLink><linkText>Using Windows PowerShell to Administer AD RMS</linkText><linkUri>https://technet.microsoft.com/library/ee221079(v=ws.10).aspx</linkUri></externalLink>.</para><para>You can see your organization's automatically created group if you copy one of the default rights policy templates in the Azure classic portal, and then identify the <ui>USER NAME</ui> on the <ui>RIGHTS</ui> page. However, you cannot use the classic portal to add this group to a template that was manually created or imported and instead must use one of the following Azure RMS PowerShell options:  </para><list class="bullet"><listItem><para>Use the <externalLink><linkText>New-AadrmRightsDefinition</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727080.aspx</linkUri></externalLink> PowerShell cmdlet to define the  "AllStaff" group and rights as a rights definition object, and run this command again for each of the other groups or users already granted rights in the original template in addition to the ANYONE group. Then add all these rights definition objects to the templates by using the  <externalLink><linkText>Set-AadrmTemplateProperty</linkText><linkUri>https://msdn.microsoft.com/en-us/library/azure/dn727076.aspx</linkUri></externalLink> cmdlet.</para></listItem><listItem><para>Use the <externalLink><linkText>Export-AadrmTemplate</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727078.aspx</linkUri></externalLink> cmdlet to export the template to a .XML file that you can edit to add the "AllStaff" group and rights to the existing groups and rights, and then use the <externalLink><linkText>Import-AadrmTemplate</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn727077.aspx</linkUri></externalLink> cmdlet to import this change back into Azure RMS.</para></listItem></list><alert class="note">
 <para>This "AllStaff" equivalent group isn't exactly the same as the ANYONE group in AD RMS:  The "AllStaff" group includes all users in your Azure tenant, whereas the ANYONE group includes all authenticated users, who could be outside your organization. </para>
<para>Because of this difference between the two groups, you might need to also add external users in addition to the "AllStaff" group. External email addresses for groups are not currently supported.</para></alert><para>Templates that you import from AD RMS look and behave just like custom templates that you can create in the Azure classic portal. To change imported templates to be published so that users can see them and select them from applications, or to make other changes to the templates, see <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c">Configuring Custom Templates for Azure Rights Management</link>.</para>
          <alert class="tip">
            <para>For a more consistent experience for users during the migration process, do not make changes to the imported templates other than these two changes; and do not publish the two default templates that come with Azure RMS, or create new templates at this time. Instead, wait until the migration process is complete and you have decommissioned the AD RMS servers.</para>
          </alert>
        </content>
      <sections><section expanded="false" address="BKMK_ScriptForANYONE">
<title>Sample Windows PowerShell script to identify AD RMS templates that include the ANYONE group</title><content><para>This section contains the sample script to help you identify AD RMS templates that have the ANYONE group defined, as described in the preceding section.</para><para><legacyItalic><embeddedLabel>Disclaimer:</embeddedLabel> This sample script is not supported under any Microsoft standard support program or service. This sample script is provided AS IS without warranty of any kind.</legacyItalic></para><code>import-module adrmsadmin 

New-PSDrive -Name MyRmsAdmin -PsProvider AdRmsAdmin -Root https://localhost -Force 

$ListofTemplates=dir MyRmsAdmin:\RightsPolicyTemplate

foreach($Template in $ListofTemplates) 
{ 
                $templateID=$Template.id
  
                $rights = dir MyRmsAdmin:\RightsPolicyTemplate\$Templateid\userright
   
     $templateName=$Template.DefaultDisplayName 
 
        if ($rights.usergroupname -eq "anyone")

                         {
                           $templateName = $Template.defaultdisplayname

                           write-host "Template " -NoNewline
                
                           write-host -NoNewline $templateName -ForegroundColor Red

                           write-host " contains rights for " -NoNewline

                           write-host ANYONE  -ForegroundColor Red
                         }
 } 
Remove-PSDrive MyRmsAdmin -force
</code></content>
</section></sections></section>
      <section address="BKMK_Step5Migration">
        <title>Step 5. Reconfigure clients to use Azure RMS</title>
        <content>
          <para>For Windows clients:</para>
          <list class="ordered">
            <listItem>
              <para>
                <externalLink>
                  <linkText>Download the migration scripts</linkText>
                  <linkUri>http://go.microsoft.com/fwlink/?LinkId=524619</linkUri>
                </externalLink>: </para>
              <list class="bullet">
                <listItem>
                  <para>CleanUpRMS_RUN_Elevated.cmd</para>
                </listItem>
                <listItem>
                  <para>Redirect_OnPrem.cmd</para>
                </listItem>
              </list>
              <para>These scripts reset the configuration on Windows computers so that they will use the Azure RMS service rather than AD RMS. </para>
            </listItem>
            <listItem>
              <para>Follow the instructions in the redirection script (Redirect_OnPrem.cmd) to modify the script to point to your new Azure RMS tenant. </para>
            </listItem>
            <listItem>
              <para>On the Windows computers, run these scripts with elevated privileges in the user’s context.</para>
            </listItem>
          </list>
          <para>For mobile device clients and Mac computers:</para>
          <list class="bullet">
            <listItem>
              <para>Remove the DNS SRV records that you created when you deployed the <externalLink><linkText>AD RMS mobile device extension</linkText><linkUri>http://technet.microsoft.com/library/dn673574.aspx</linkUri></externalLink>.</para>
            </listItem>
          </list>
        </content>
        <sections>
          <section expanded="false">
            <title>Changes made by the migration scripts</title>
            <content>
              <para>This section documents the changes that the migration scripts make. You can use this information for reference purposes only, or for troubleshooting, or if you prefer to make these changes yourself.</para>
              <para>CleanUpRMS_RUN_Elevated.cmd:</para>
              <list class="bullet">
                <listItem>
                  <para>Delete the contents of the %userprofile%\AppData\Local\Microsoft\DRM and %userprofile%\AppData\Local\Microsoft\MSIPC folders, including any subfolders and any files with long file names.</para>
                </listItem>
                <listItem>
                  <para>Delete the contents of the following registry keys:</para>
                  <list class="bullet">
                    <listItem>
                      <para>HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSIPC\ServiceLocation</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_LOCAL_MACHINE\SOFTWARE\WoW6432Node\Microsoft\MSIPC\ServiceLocation</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_LOCAL_MACHINE\Software\Microsoft\MSDRM\ServiceLocation</para>
                    </listItem>
                  </list>
                </listItem>
                <listItem>
                  <para>Delete the following registry values:</para>
                  <list class="bullet">
                    <listItem>
                      <para>HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServerURL</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_CURRENT_USER\Software\Microsoft\Office\15.0\Common\DRM\DefaultServer</para>
                    </listItem>
                  </list>
                </listItem>
              </list>
              <para>Redirect_OnPrem.cmd:</para>
              <list class="bullet">
                <listItem>
                  <para>Create the following registry values for each URL supplied as a parameter under each of the following locations:</para>
                  <list class="bullet">
                    <listItem>
                      <para>HKEY_CURRENT_USER\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_CURRENT_USER\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_LOCAL_MACHINE\Software\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_LOCAL_MACHINE\Software\WoW6432Node\Microsoft\Office\(11.0|12.0|14.0)\Common\DRM\LicenseServerRedirection</para>
                    </listItem>
                    <listItem>
                      <para>HKEY_CURRENT_USER\Software\Classes\Local Settings\Software\Microsoft\MSIPC\LicensingRedirection</para>
                    </listItem>
                  </list>
                  <para>Each entry has a REG_SZ value of <ui>https://OldRMSserverURL/_wmcs/licensing</ui> with the data in the following format: <ui>https://&lt;YourTenantURL&gt;/_wmcs/licensing</ui>.</para>
                  <alert class="note">
                    <para>
                      <placeholder>&lt;YourTenantURL&gt;</placeholder> has the following format: <ui>{GUID}.rms.[Region].aadrm.com</ui>. </para>
                    <para>For example:  5c6bb73b-1038-4eec-863d-49bded473437.rms.na.aadrm.com</para>
                    <para>You can find this value by identifying the <ui>RightsManagementServiceId</ui> value when you run the <externalLink><linkText>Get-AadrmConfiguration</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629410.aspx</linkUri></externalLink> cmdlet for Azure RMS.</para>
                  </alert>
                </listItem>
              </list>
            </content>
          </section>
        </sections>
      </section>
      <section address="BKMK_Step6Migration">
        <title>Step 6. Configure IRM integration for Exchange Online</title>
        <content>
          <para>If you have previously imported your TDP from AD RMS to Exchange Online, you must remove this TDP to avoid conflicting templates and policies after you have migrated to Azure RMS. To do this, use the <externalLink><linkText>Remove-RMSTrustedPublishingDomain</linkText><linkUri>https://technet.microsoft.com/en-us/library/jj200720(v=exchg.150).aspx</linkUri></externalLink> cmdlet from Exchange Online.</para><para>If you chose an Azure RMS tenant key topology of <embeddedLabel>Microsoft managed</embeddedLabel>:</para><list class="bullet"><listItem><para>See the <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_ExchangeOnline">Exchange Online: IRM Configuration</link> section in the <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36">Configuring Applications for Azure Rights Management</link> topic. This section includes typical commands to run that connects to the Exchange Online service, imports the tenant key from Azure RMS,  and enables IRM functionality for Exchange Online. After you complete these steps, you will have full RMS functionality with Exchange Online.</para></listItem></list><para>If you chose an Azure RMS tenant key topology of <embeddedLabel>customer-managed (BYOK)</embeddedLabel>:</para>
          <list class="bullet"><listItem><para> You will  have reduced RMS functionality with Exchange Online, as described in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14#BKMK_Pricing">BYOK pricing and restrictions</link> section in the <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and Implementing Your Azure Rights Management Tenant Key</link> topic.</para></listItem></list>
          
          
          
          
          
          
        </content>
      </section><section address="BKMK_Step7Migration">
        <title>Step 7. Deploy the RMS connector</title>
        <content>
          <para>If you have used the Information Rights Management (IRM) functionality of Exchange Server or SharePoint Server with AD RMS, you must first disable IRM on these servers and remove AD RMS configuration. Then, deploy the Rights Management (RMS) connector, which acts as a communications interface (a relay) between the on-premises servers and Azure RMS. </para>
          <para>Finally for this step, if you have imported multiple TPDs into Azure RMS that were used to protect email messages, you must manually edit the registry on the Exchange Server computers to redirect all TPDs URLs to the RMS connector.</para>
          <alert class="note">
            <para>Before you start, check the supported versions of the on-premises servers that the RMS connector supports in “On-premises servers that support Azure RMS” in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedApplications">Applications that support Azure RMS</link> section of the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic.</para>
          </alert>
          <procedure>
            <title>Disable IRM on Exchange Servers and remove AD RMS configuration</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>On each Exchange server, locate the following folder and delete all the entries in that folder: \ProgramData\Microsoft\DRM\Server\S-1-5-18</para>
                </content>
              </step>
              <step>
                <content>
                  <para>From one of the Exchange servers, use the Exchange <externalLink><linkText>Set_IRMConfiguration</linkText><linkUri>http://technet.microsoft.com/library/dd979792.aspx</linkUri></externalLink> cmdlet to first disable IRM features for messages that are sent to internal recipients: </para>
                  <code>Set-IRMConfiguration -InternalLicensingEnabled $false</code>
                </content>
              </step>
              <step>
                <content>
                  <para>Then use the same cmdlet to disable IRM features for messages that are sent to external recipients:</para>
                  <code>Set-IRMConfiguration -ExternalLicensingEnabled $false</code>
                </content>
              </step>
              <step>
                <content>
                  <para>Next, use the same cmdlet to disable IRM in Microsoft Office Outlook Web App and in Microsoft Exchange ActiveSync:</para>
                  <code>Set-IRMConfiguration -ClientAccessServerEnabled $false</code>
                </content>
              </step>
              <step>
                <content>
                  <para>Finally, use the same cmdlet to clear any cached certificates:</para>
                  <code>Set-IRMConfiguration -RefreshServerCertificates</code>
                </content>
              </step>
              <step>
                <content>
                  <para>On each Exchange Server, now reset IIS, for example, by running a command prompt as an administrator and typing <userInput>iisreset</userInput>.</para>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>Disable IRM on SharePoint Servers and remove AD RMS configuration</title>
            <steps class="ordered">
              <step>
                <content>
                  <para>Make sure that there are no documents checked out from RMS-protected libraries. If there are, they will be become inaccessible at the end of this procedure.</para>
                </content>
              </step>
              <step>
                <content>
                  <para>On the SharePoint Central Administration Web site, in the <ui>Quick Launch</ui> section, click <ui>Security</ui>.</para>
                </content>
              </step>
              <step>
                <content>
                  <para>On the <ui>Security</ui> page, in the <ui>Information Policy</ui> section, click <ui>Configure information rights management</ui>.</para>
                </content>
              </step>
              <step>
                <content>
                  <para>On the <ui>Information Rights Management</ui> page, in the <ui>Information Rights Management</ui> section, select <ui>Do not use IRM on this server</ui>, then click <ui>OK</ui>.</para>
                </content>
              </step>
              <step>
                <content>
                  <para>On each of the SharePoint Server computers, delete the contents of the folder \ProgramData\Microsoft\MSIPC\Server\<placeholder>&lt;SID of the account running SharePoint Server&gt;</placeholder>.</para>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>Install and configure the RMS connector</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>Use the instructions in the <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066">Deploying the Azure Rights Management Connector</link> topic.</para>
                </content>
              </step>
            </steps>
          </procedure>
          <procedure>
            <title>For Exchange only and multiple TPDs: Edit the registry</title>
            <steps class="bullet">
              <step>
                <content>
                  <para>On each Exchange Server, manually add the following registry keys for each additional TPD that you imported, to redirect the TPD URLs to the RMS connector. These registry entries are specific to migration and are not added by the server configuration tool for Microsoft RMS connector. </para>
                  <para>When you make these registry edits, use the following instructions:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Replace <placeholder>ConnectorFQDN</placeholder> with the name that you defined in DNS for the connector. For example, <ui>rmsconnector.contoso.com</ui>.</para>
                    </listItem>
                    <listItem>
                      <para>Use the HTTP or HTTPS prefix for the connector URL, depending on whether you have configured the connector to use HTTP or HTTPS to communicate with your on-premises servers. </para>
                    </listItem>
                  </list>
                  <para> </para>
                  <para>
                    <embeddedLabel>For Exchange 2013:</embeddedLabel>
                  </para>
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
                          <para>HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection</para>
                        </TD>
                        <TD>
                          <para>Reg_SZ</para>
                        </TD>
                        <TD>
                          <para>https://&lt;AD RMS Intranet Licensing URL&gt;/_wmcs/licensing</para>
                        </TD>
                        <TD>
                          <para>One of the following, depending on whether you are using HTTP or HTTPS from your Exchange server to the RMS connector:</para>
                          <list class="bullet">
                            <listItem>
                              <para>http://&lt;connectorFQDN&gt;/_wmcs/licensing</para>
                            </listItem>
                            <listItem>
                              <para>https://&lt;connectorName&gt;/_wmcs/licensing</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>HKLM\SOFTWARE\Microsoft\ExchangeServer\v15\IRM\LicenseServerRedirection </para>
                        </TD>
                        <TD>
                          <para>Reg_SZ</para>
                        </TD>
                        <TD>
                          <para>https://&lt;AD RMS Extranet Licensing URL&gt;/_wmcs/licensing</para>
                        </TD>
                        <TD>
                          <para>One of the following, depending on whether you are using HTTP or HTTPS from your Exchange server to the RMS connector:</para>
                          <list class="bullet">
                            <listItem>
                              <para>http://&lt;connectorFQDN&gt;/_wmcs/licensing</para>
                            </listItem>
                            <listItem>
                              <para>https://&lt;connectorFQDN&gt;/_wmcs/licensing</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                  <para>
                    <embeddedLabel>For Exchange Server 2010:</embeddedLabel>
                  </para>
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
                          <para>HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection</para>
                        </TD>
                        <TD>
                          <para>Reg_SZ</para>
                        </TD>
                        <TD>
                          <para>https://&lt;AD RMS Intranet Licensing URL&gt;/_wmcs/licensing</para>
                        </TD>
                        <TD>
                          <para>One of the following, depending on whether you are using HTTP or HTTPS from your Exchange server to the RMS connector:</para>
                          <list class="bullet">
                            <listItem>
                              <para>http://&lt;connectorName&gt;/_wmcs/licensing</para>
                            </listItem>
                            <listItem>
                              <para>https://&lt;connectorName&gt;/_wmcs/licensing</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                      <tr>
                        <TD>
                          <para>HKLM\SOFTWARE\Microsoft\ExchangeServer\v14\IRM\LicenseServerRedirection </para>
                        </TD>
                        <TD>
                          <para>Reg_SZ</para>
                        </TD>
                        <TD>
                          <para>https://&lt;AD RMS Extranet Licensing URL&gt;/_wmcs/licensing</para>
                        </TD>
                        <TD>
                          <para>One of the following, depending on whether you are using HTTP or HTTPS from your Exchange server to the RMS connector:</para>
                          <list class="bullet">
                            <listItem>
                              <para>http://&lt;connectorName&gt;/_wmcs/licensing</para>
                            </listItem>
                            <listItem>
                              <para>https://&lt;connectorName&gt;/_wmcs/licensing</para>
                            </listItem>
                          </list>
                        </TD>
                      </tr>
                    </tbody>
                  </table>
                </content>
              </step>
            </steps>
          </procedure>
          <para>After you have completed these procedures, be sure to read the <embeddedLabel>Next steps</embeddedLabel> section in the <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066">Deploying the Azure Rights Management Connector</link> topic.</para>
        </content>
      </section>
      <section address="BKMK_Step8Migration">
        <title>Step 8. Decommission AD RMS</title>
        <content>
          <para>Optional: Remove the Service Connection Point (SCP) from Active Directory to prevent computers from discovering your on-premises Rights Management infrastructure. This is optional because of the redirection that you configured in the registry (for example, by running the migration script). To remove the Service Connection Point, use the AD SCP Register tool from the <externalLink><linkText>Rights Management Services Administration Toolkit</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=1479</linkUri></externalLink>.</para>
          <para>Monitor your AD RMS servers for activity, for example, by checking the <externalLink><linkText>requests in the System Health report</linkText><linkUri>https://technet.microsoft.com/library/ee221012(v=ws.10).aspx</linkUri></externalLink>, the <externalLink><linkText>ServiceRequest table</linkText><linkUri>http://technet.microsoft.com/library/dd772686(v=ws.10).aspx</linkUri></externalLink> or <externalLink><linkText>auditing of user access to protected content</linkText><linkUri>http://social.technet.microsoft.com/wiki/contents/articles/3440.ad-rms-frequently-asked-questions-faq.aspx</linkUri></externalLink>. When you have confirmed that RMS clients are no longer communicating with these servers and that clients are successfully using Azure RMS, you can remove the AD RMS server role from these server. If you’re using dedicated servers, you might prefer the cautionary step of first shutting down the servers for a period of time to make sure that there are no reported problems that might require restarting these servers to ensure service continuity while you investigate why clients are not using Azure RMS. </para>
          <para>After decommissioning your AD RMS servers, you might want to take the opportunity to review your templates in the Azure classic portal and consolidate them so that users have fewer to choose between, or reconfigure them, or even add new templates. This would be also a good time to publish the default templates. For more information, see <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c">Configuring Custom Templates for Azure Rights Management</link>.</para>
        </content>
      </section>
      <section address="BKMK_Step9Migration">
        <title>Step 9. Re-key your Azure RMS tenant key</title>
        <content>
          <para>This step is required when migration is complete if your AD RMS deployment was using RMS Cryptographic Mode 1, because re-keying creates a new tenant key that uses RMS Cryptographic Mode 2. Using Azure RMS with Cryptographic Mode 1 is supported only during the migration process.</para>
          <para>This step is optional but recommended when migration is complete even if you were running in RMS Cryptographic Mode 2, because it helps to secure your Azure RMS tenant key from potential security breaches to your AD RMS key. When you re-key your Azure RMS tenant key (also known as “rolling your key”), a new key is created and the original key is archived. However, because moving from one key to another doesn’t happen immediately but over a few weeks, do not wait until you suspect a breach to your original key but re-key your RMS tenant key as soon as the migration is complete. </para>
          <para>To re-key your Azure RMS tenant key:</para>
          <list class="bullet">
            <listItem>
              <para>If your RMS tenant key is managed by Microsoft: Call Microsoft Customer Support Services (CSS) and prove that you are the RMS tenant administrator.</para>
            </listItem><listItem>
              <para>If your RMS tenant key is managed by you (BYOK): Repeat the BYOK procedure to generate and create a new key over the Internet or in person.</para>
            </listItem>
          
            
          </list>
          <para>For more information about managing your RMS tenant key, see <link xlink:href="1284d0ee-0a72-45ba-a64c-3dcb25846c3d">Operations for Your Azure Rights Management Tenant Key</link>.</para>
        </content>
      </section>
    </sections>
  </section>
  <relatedTopics>
    <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
