---
description: na
keywords: na
pagetitle: Activating Azure Rights Management
search: na
ms.date: 2015-12-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f8707e01-b239-4d1a-a1ea-0d1cf9a8d214
ms.author: e8f708ba3bce4153b61467184c747c7g
---
# Activating Azure Rights Management
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When you activate <token>aad_rightsmanagement_1</token> (Azure RMS), your organization can start to protect important data by using applications and services that support this information protection solution. Administrators can also manage and monitor protected files and emails that your organization owns. You must enable <token>aad_rightsmanagement_2</token> before you can begin to use the information rights management (IRM) features within Office, SharePoint, and Exchange, and protect any sensitive or confidential file. </para>
    <para>If you want to learn more about Azure Rights Management before you activate the service—for example, what business problems it solves, some typical use cases, and how it works—see <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link></para>
    <alert class="important">
      <para>Before you activate <token>aad_rightsmanagement_2</token>, make sure that your organization has a service plan that includes <token>aad_rightsmanagement_2</token> services. If not, you will not be able to activate Azure RMS. </para>
      <para>For more information, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedSubscriptions">Cloud subscriptions that support Azure RMS</link> section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic.</para>
    </alert>
    <para>After you have activated Azure RMS, all users in your organization can apply information protection to their files, and all users can open (consume) files that have been protected by Azure RMS. However, if you prefer, you can restrict who can apply information protection, by using onboarding controls for a phased deployment. For more information, see the <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214#BKMK_OnboardingControls">Configuring onboarding controls for a phased deployment</link> section in this topic. </para>
  </introduction>
  <section>
    <title>Activating Rights Management </title>
    <content>
      <para>Use one of the following procedures to activate <token>aad_rightsmanagement_2</token>.</para>
      <alert class="tip">
        <para>You can also use the Windows PowerShell cmdlet, <externalLink><linkText>Enable-Aadrm</linkText><linkUri>http://msdn.microsoft.com/library/windowsazure/dn629412.aspx</linkUri></externalLink>, to activate <token>aad_rightsmanagement_2</token>. </para>
      </alert>
      <procedure>
        <title>To activate Rights Management from the Office 365 admin center</title>
        <steps class="ordered">
          <step>
            <content>
              <para>After you have signed up for an Office 365 plan that includes Rights Management, <externalLink><linkText>sign in to Office 365 with your work or school account</linkText><linkUri>https://portal.office.com/</linkUri></externalLink> that is an administrator for your Office 365 deployment.</para>
            </content>
          </step>
          <step>
            <content>
              <para>If the Office 365 admin center does not automatically display, select the app launcher icon in the upper-left and choose <ui>Admin</ui>. The <ui>Admin</ui> tile appears only to Office 365 administrators.</para>
              <alert class="tip">
                <para>For admin center help, see <externalLink><linkText>About the Office 365 admin center - Admin Help</linkText><linkUri>https://support.office.com/article/About-the-Office-365-admin-center-Admin-Help-58537702-d421-4d02-8141-e128e3703547</linkUri></externalLink>.</para>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>In the left pane, expand <ui>SERVICE SETTINGS</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click <ui>Rights Management</ui>.</para>
              <alert class="note">
                <para>If you do not see this option, it might be because your service plan or product version cannot support Rights Management, or it has not yet been upgraded to support Rights Management.</para>
                <para>Use the information in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedSubscriptions">Cloud subscriptions that support Azure RMS</link> section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic to confirm support. If your service plan or product version is supported but you do not see the Rights Management option, it might be because the service is not yet upgraded. For help with this issue, send an email message to <externalLink><linkText>askipteam</linkText><linkUri>mailto:askipteam@microsoft.com?subject=I%20cannot%20activate%20RMS</linkUri></externalLink>.</para>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>On the <ui>RIGHTS MANAGEMENT</ui> page, click <ui>Manage</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>On the <ui>rights management</ui> page, click <ui>activate</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>When prompted <ui>Do you want to activate Rights Management?</ui>, click <ui>activate</ui>.</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>You should now see <ui>Rights management is activated</ui> and the option to deactivate.</para>
          </content>
        </conclusion>
      </procedure>
      <procedure>
        <title>To activate Rights Management from the Azure classic portal</title>
        <steps class="ordered">
          <step>
            <content>
              <para>After you have signed up for your Azure account, <externalLink><linkText>sign in to the Azure classic portal</linkText><linkUri>http://go.microsoft.com/fwlink/p/?LinkID=275081</linkUri></externalLink>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>In the left pane, click <ui>ACTIVE DIRECTORY</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>From the <ui>active directory</ui> page, click <ui>RIGHTS MANAGEMENT</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select the directory to manage for <token>aad_rightsmanagement_2</token>, click <ui>ACTIVATE</ui>, and then confirm your action.</para>
              <alert class="note">
                <para>If you see an activation error, it might be because your service plan or product version cannot support <token>aad_rightsmanagement_2</token>.</para>
                <para>Use the information in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedSubscriptions">Cloud subscriptions that support Azure RMS</link> section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic to confirm RMS support. For help with this issue, send an email message to <externalLink><linkText>askipteam</linkText><linkUri>mailto:askipteam?subject=I%20cannot%20activate%20RMS</linkUri></externalLink>.</para>
              </alert>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>The <ui>RIGHTS MANAGEMENT STATUS</ui> should now display <ui>Active</ui> and the <ui>ACTIVATE</ui> option is replaced with <ui>DEACTIVATE</ui>. </para>
          </content>
        </conclusion>
      </procedure>
    </content>
    <sections>
      <section>
        <title>Rights Management status values and descriptions in the Azure classic portal</title>
        <content>
          <para>In addition to the <ui>Active</ui> status, which indicates that the Rights Management service is enabled and ready to use, you might also see <ui>Inactive</ui>, <ui>Unavailable</ui>, or <ui>Unauthorized</ui>. </para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Status value</para>
                </TD>
                <TD>
                  <para>Description</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>
                    <ui>Active</ui>
                  </para>
                </TD>
                <TD>
                  <para>
                    <token>aad_rightsmanagement_2</token> is enabled and ready for use.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <ui>Inactive</ui>
                  </para>
                </TD>
                <TD>
                  <para>
                    <token>aad_rightsmanagement_2</token> is disabled and must be activated before your organization can protect files.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <ui>Unavailable</ui>
                  </para>
                </TD>
                <TD>
                  <para>The <token>aad_rightsmanagement_2</token> service is down. Try again later.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <ui>Unauthorized</ui>
                  </para>
                </TD>
                <TD>
                  <para>You do not have permissions to view the status of the <token>aad_rightsmanagement_2</token> service. For example, your account is locked out or you are not the global administrator for the selected tenant.</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_OnboardingControls">
    <title>Configuring onboarding controls for a phased deployment</title>
    <content>
      <para>If you don’t want all users to be able to protect files immediately by using Azure RMS, you can configure user onboarding controls by using the <externalLink><linkText>Set-AadrmOnboardingControlPolicy</linkText><linkUri>http://msdn.microsoft.com/library/azure/dn857521.aspx</linkUri></externalLink> Windows PowerShell command. You can run this command before or after you activate Azure RMS.</para>
      <alert class="important">
        <para>To use this command, you must have at least version <embeddedLabel>2.1.0.0</embeddedLabel> of the <externalLink><linkText>Azure RMS Windows PowerShell module</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=257721</linkUri></externalLink>.</para>
        <para>To check the version you have installed, run: <userInput>(Get-Module aadrm –ListAvailable).Version</userInput></para>
      </alert>
      <para>For example, if you initially want only administrators in the “IT department” group (that has an object ID of fbb99ded-32a0-45f1-b038-38b519009503) to be able to protect content for testing purposes, use the following command:</para>
      <code>Set-AadrmOnboardingControlPolicy – SecurityGroupObjectId fbb99ded-32a0-45f1-b038-38b519009503</code>
      <para>Note that for this configuration option, you must specify a group; you cannot specify individual users.</para><para>Or, if you want to ensure that only users who are correctly licensed to use Azure RMS can protect content:</para>
      <code>Set-AadrmOnboardingControlPolicy -UseRmsUserLicense $true</code>
      <para>When you use these onboarding controls, all users in the organization can always consume protected content that has been protected by your subset of users, but they won’t be able to apply information protection themselves from client applications. For example, they won’t see in their Office clients the default templates that are automatically published when Azure RMS is activated, or custom templates that you might configure.  Server-side applications, such as Exchange, can implement their own per-user controls for RMS-integration to achieve the same result.</para>
    </content>
  </section>
  <section>
    <title>Next steps</title>
    <content>
      <para>Now that you’ve activated <token>aad_rightsmanagement_1</token> for your organization, use the <link xlink:href="086600c2-c5d8-47ec-a4c0-c782e1797486">Azure Rights Management Deployment Roadmap</link> to check whether there are other configuration steps that you might need to do before you roll out <token>aad_rightsmanagement_1</token> to users and administrators. For example, you might want to use <externalLink><linkText>custom templates</linkText><linkUri>http://technet.microsoft.com/library/dn642472.aspx</linkUri></externalLink> to make it easier for users to apply information protection to files, connect your on-premises servers to use <token>aad_rightsmanagement_1</token> by installing the <externalLink><linkText>RMS connector</linkText><linkUri>http://technet.microsoft.com/library/dn375964.aspx</linkUri></externalLink>, and deploy the <externalLink><linkText>Rights Management sharing application</linkText><linkUri>http://technet.microsoft.com/library/jj585031.aspx</linkUri></externalLink> that supports protecting all file types on all devices. Office services,  such as Exchange Online and SharePoint Online require additional configuration before you can use their Information Rights Management (IRM) features. However, if there are no other configuration steps that you need to do, see <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using Azure Rights Management</link> for operational guidance to support a successful deployment for your organization.</para>
      <para>For information about how your applications work with <token>aad_rightsmanagement_1</token>, see <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link>.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring rights management</link>
  </relatedTopics>
</developerConceptualDocument>
