---
description: na
search: na
title: What is Azure Rights Management?
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 2015-12-01
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# What is Azure Rights Management?
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Azure Rights Management (Azure RMS) is an information protection solution for organizations that want to protect their data in today's challenging working environment. </para><para>These challenges include the need to be Internet-connected, with users bringing personal device to work, accessing company data on the road and home, and sharing sensitive information with important business partners. As part of their daily work, users share information by using email, file-sharing sites, and cloud services. In these scenarios, traditional security controls (such as access control lists and NTFS permissions) and firewalls have limited effectiveness if you want to protect your company data while still empowering your users to work efficiently.</para>
    <para>In comparison, Azure RMS can protect your company’s sensitive information in all these scenarios. It uses encryption, identity, and authorization policies to help secure your files and email, and it works across multiple devices—phones, tablets, and PCs. Information can be protected both within your organization and outside your organization because that protection remains with the data, even when it leaves your organization’s boundaries. As an example, employees might email a document to a partner company, or they save a document to their cloud drive. The persistent protection that Azure RMS provides not only helps to secure your company data, but might also be legally mandated for compliance, legal discovery requirements, or simply good information management practices.</para>
    <para>But very importantly, authorized people and services (such as search and indexing) can continue to read and inspect the data that Azure RMS protects, which is not easily accomplished with other information protection solutions that use peer-to-peer encryption. This ability is sometimes referred to as “reasoning over data” and is a crucial element in maintaining control of your organization’s data.</para>
    <para>The following picture shows how Azure RMS works as a Rights Management solution for Office 365 as well as for on-premises servers and services. You'll also see that it supports the popular end user devices that run Windows, Mac OS, iOS, Android, and Windows Phone. </para>
    <mediaLink>
      <image xlink:href="b5567e9d-98ee-4c9c-ae37-46207e2e53da"/>
    </mediaLink>
    <para> </para>
    <alert class="tip">
      <para>At this point, you might find the additional resources useful:</para>
      <list class="bullet">
        <listItem>
          <para>Two minute video: <externalLink><linkText>What is Microsoft Azure Rights Management</linkText><linkUri>http://technet.microsoft.com/dn833005.aspx</linkUri></externalLink></para>
        </listItem>
        <listItem>
          <para>Five-step tutorial: <link xlink:href="1db923bf-7d19-4fdd-a413-bfeb58af5e03">Quick Start Tutorial for Azure Rights Management</link></para>
        </listItem>
        <listItem>
          <para>Azure RMS requirements, including subscription options to purchase or evaluate: <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link></para>
        </listItem>
      </list>
    </alert>
    <para>Use the following sections to learn more about Azure RMS:</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_RMSrequirements">What problems does Azure RMS solve?</link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_RMScompliance">Security, compliance, and regulatory requirements</link>
            </para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_RMSpictures">Azure RMS in action: What administrators and users see</link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Example_ManagementPortal">Activating and configuring Rights Management</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Example_FCI">Automatically protecting files on file servers running Windows Server and File Classification Infrastructure</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Example_DLP">Automatically protecting emails with Exchange Online and data loss prevention policies</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Example_SharePoint">Automatically protecting files with SharePoint Online and protected libraries</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Example_SharingApp">Users safely share attachments with mobile users</link>
            </para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_HowRMSworks">How does Azure RMS work? Under the hood</link>
        </para>
        <list class="bullet">
          <listItem>
            <para>
              <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_RMScrytographics">Cryptographic controls used by Azure RMS: Algorithms and key lengths</link>
            </para>
          </listItem>
          <listItem>
            <para>
              <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Walthrough">Walkthrough of how Azure RMS works: First use, content protection, content consumption</link>
            </para>
          </listItem>
        </list>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_NextSteps">Next steps</link>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMK_RMSrequirements">
    <title>What problems does Azure RMS solve?</title>
    <content>
      <para>Use the following table to identify business requirements or problems that your organization might have, and how Azure RMS can address these.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Requirement or problem</para>
            </TD>
            <TD>
              <para>Solved by Azure RMS</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Protect all file types</para>
            </TD>
            <TD>
              <para>√ In previous implementation of Rights Management, only Office files could be protected, using native protection. Now, <externalLink><linkText>generic protection</linkText><linkUri>https://technet.microsoft.com/library/dn574738(v=ws.10).aspx#BKMK_GenericNative</linkUri></externalLink> means that all file types are supported. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Protect files anywhere</para>
            </TD>
            <TD>
              <para>√ When a file is saved to a location (<externalLink><linkText>protect in-place</linkText><linkUri>https://technet.microsoft.com/library/dn574733(v=ws.10).aspx</linkUri></externalLink>), the protection stays with the file, even if it is copied to storage that is not under the control of IT, such as a cloud storage service. </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Share files securely by email</para>
            </TD>
            <TD>
              <para>√ When a file is shared by email (<externalLink><linkText>share protected</linkText><linkUri>https://technet.microsoft.com/library/dn574735(v=ws.10).aspx</linkUri></externalLink>), the file is protected as an attachment to an email message, with instructions how to open the protected attachment. The email text is not encrypted, so the recipient can always read these instructions. However, because the attached document is protected, only authorized users will be able to open it, even if the email or document is forwarded to other people.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Auditing and monitoring</para>
            </TD>
            <TD>
              <para>√ You can <externalLink><linkText>audit and monitor usage</linkText><linkUri>https://technet.microsoft.com/library/dn529121.aspx</linkUri></externalLink> of your protected files, even after these files leave your organization’s boundaries. </para>
              <para>For example, you work for Contoso, Ltd. You are working on a joint project with 3 people from Fabrikam, Inc. You email these 3 people a document that you protect and restrict to read-only. Azure RMS auditing can provide the following information:</para>
              <list class="bullet">
                <listItem>
                  <para>Whether the people you specified in Fabrikam opened the document, and when.</para>
                </listItem>
                <listItem>
                  <para>Whether other people that you didn’t specify attempted (and failed) to open the document—perhaps because it was forwarded or saved to a shared location that others could access.</para>
                </listItem>
                <listItem>
                  <para>Whether any of the specified people tried (and failed) to print or change the document.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Support for all commonly used devices, not just Windows computers</para>
            </TD>
            <TD>
              <para>√ <externalLink><linkText>Supported devices</linkText><linkUri>https://technet.microsoft.com/library/dn655136.aspx</linkUri></externalLink> include: </para>
              <list class="bullet">
                <listItem>
                  <para>Windows computers and phones</para>
                </listItem>
                <listItem>
                  <para>Mac computers</para>
                </listItem>
                <listItem>
                  <para>iOS tablets and phones</para>
                </listItem>
                <listItem>
                  <para>Android tablets and phones</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Support for business-to-business collaboration </para>
            </TD>
            <TD>
              <para>√ Because Azure RMS is a cloud service, there’s no need to explicitly configure trusts with other organizations before you can share protected content with them. If they already have an Office 365 or an Azure AD directory, collaboration across organizations is automatically supported. If they do not, users can sign up for the free <externalLink><linkText>RMS for individuals</linkText><linkUri>https://technet.microsoft.com/library/dn592127.aspx</linkUri></externalLink> subscription.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Support for on-premises services, as well as Office 365</para>
            </TD>
            <TD>
              <para>√  In addition to working <externalLink><linkText>seamlessly with Office 365</linkText><linkUri>https://technet.microsoft.com/library/jj585004.aspx</linkUri></externalLink>, you can also use Azure RMS with the following on-premises services when you deploy the <externalLink><linkText>RMS connector</linkText><linkUri>https://technet.microsoft.com/library/dn375964.aspx</linkUri></externalLink>:</para>
              <list class="bullet">
                <listItem>
                  <para>Exchange Server</para>
                </listItem>
                <listItem>
                  <para>SharePoint Server</para>
                </listItem>
                <listItem>
                  <para>Windows Server running File Classification Infrastructure</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Easy activation</para>
            </TD>
            <TD>
              <para>√ <externalLink><linkText>Activating the Rights Management service</linkText><linkUri>https://technet.microsoft.com/library/jj658941.aspx</linkUri></externalLink> for users requires just a couple of clicks in the Azure classic portal.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Ability to scale across your organization, as needed</para>
            </TD>
            <TD>
              <para>√ Because Azure RMS runs as a cloud service with the Azure elasticity to scale up and out, you don’t have to provision or deploy additional on-premises servers.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Ability to create simple and flexible policies</para>
            </TD>
            <TD>
              <para>√ <externalLink><linkText>Customized rights policy templates</linkText><linkUri>https://technet.microsoft.com/library/dn642472.aspx</linkUri></externalLink> provide a quick and easy solution for administrators to apply policies, and for users to apply the correct level of protection for each document and restrict access to people inside your organization.</para>
              <para>For example, for a company-wide strategy paper to be shared with all employees, you could apply a read-only policy to all internal employees. Then, for a more sensitive document, such as a financial report, you could restrict access to executives only.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Broad application support</para>
            </TD>
            <TD>
              <para>√ Azure RMS has tight integration with Microsoft Office applications and services, and extends support for other applications by using the RMS sharing application. </para>
              <para>√ The   <externalLink><linkText>Microsoft Rights Management SDK</linkText><linkUri>https://msdn.microsoft.com/library/hh552972(v=vs.85).aspx</linkUri></externalLink> provides your internal developers and software vendors with APIs to write custom applications that support Azure RMS.</para>
              <para>For more information, see <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link>.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>IT must maintain control of data</para>
            </TD>
            <TD>
              <para>√ Organizations can choose to manage their own tenant key and use the “<externalLink><linkText>Bring Your Own Key</linkText><linkUri>https://technet.microsoft.com/library/dn440580.aspx</linkUri></externalLink>” (BYOK) solution and store their tenant key in Hardware Security Modules (HSMs). </para>
              <para>√ Support for auditing and <externalLink><linkText>usage logging</linkText><linkUri>https://technet.microsoft.com/library/dn529121.aspx</linkUri></externalLink> so that you can analyze for business insights, monitor for abuse, and (if you have an information leak) perform forensic analysis.</para>
              <para>√ Delegated access by using the <externalLink><linkText>super user feature</linkText><linkUri>https://technet.microsoft.com/library/mt147272.aspx</linkUri></externalLink> ensures that IT can always access protected content, even if a document was protected by an employee who then leaves the organization. In comparison, peer-to-peer encryption solutions risk losing access to company data.</para>
              <para>√ Synchronize <externalLink><linkText>just the directory attributes that Azure RMS needs</linkText><linkUri>https://azure.microsoft.com/documentation/articles/active-directory-aadconnectsync-attributes-synchronized/#azure-rms</linkUri></externalLink> to support a common identity for your on-premises Active Directory accounts, by using a <externalLink><linkText>directory synchronization tool</linkText><linkUri>https://azure.microsoft.com/documentation/articles/active-directory-aadconnect-get-started-tools-comparison/</linkUri></externalLink>, such as Azure AD Connect.</para>
              <para>√ Enable single-sign on without replicating passwords to the cloud, by using AD FS.</para>
              <para>√ Organizations always have the choice to stop using Azure RMS without losing access to content that was previously protected by Azure RMS. For information about decommissioning options, see <link xlink:href="0b1c2064-0d01-45ae-a541-cebd7fd762ad">Decommissioning and Deactivating Azure Rights Management</link>. In addition, organizations who have deployed Active Directory Rights Management Services (AD RMS) can <externalLink><linkText>migrate to Azure RMS</linkText><linkUri>https://technet.microsoft.com/library/dn858447.aspx</linkUri></externalLink> without losing access to data that was previously protected by AD RMS.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para/>
      <alert class="tip">
        <para>If you are familiar with the on-premises version of Rights Management, Active Directory Rights Management Services (AD RMS), you might be interested in the comparison table from <link xlink:href="8123bd62-1814-4d79-b306-e20c1a00e264">Comparing Azure Rights Management and AD RMS</link>.</para>
      </alert>
    </content>
    <sections>
      <section address="BKMK_RMScompliance">
        <title>Security, compliance, and regulatory requirements</title>
        <content>
          <para>Azure RMS supports the following security, compliance and regulatory requirements: </para>
          <para>√ Use of industry-standard cryptography and supports FIPS 140-2. For more information, see the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_RMScrytographics">Cryptographic controls used by Azure RMS: Algorithms and key lengths</link> section in this topic.</para>
          <para>√ Support for Thales Hardware Security Modules (HSMs) to store your tenant key in Microsoft Azure data centers. Azure RMS uses separate security worlds for its data centers in North America, EMEA (Europe, Middle East and Africa), and Asia, so your keys can be used only in your region.</para>
          <para>√ Certified for the following: </para>
          <list class="bullet">
            <listItem>
              <para>ISO/IEC 27001:2013 (includes <externalLink><linkText>ISO/IEC 27018</linkText><linkUri>http://azure.microsoft.com/blog/2015/02/16/azure-first-cloud-computing-platform-to-conform-to-isoiec-27018-only-international-set-of-privacy-controls-in-the-cloud/</linkUri></externalLink>)</para>
            </listItem>
            <listItem>
              <para>SOC 2 SSAE 16/ISAE 3402 attestations</para>
            </listItem>
            <listItem>
              <para>HIPAA BAA</para>
            </listItem>
            <listItem>
              <para>EU Model Clause</para>
            </listItem>
            <listItem>
              <para>FedRAMP as part of Azure Active Directory in Office 365 certification, issued FedRAMP Agency Authority to Operate by HHS</para>
            </listItem>
            <listItem>
              <para>PCI DSS Level 1</para>
            </listItem>
          </list>
          <para>For more information about these external certifications, see the <externalLink><linkText>Azure Trust Center</linkText><linkUri>http://azure.microsoft.com/support/trust-center/compliance/</linkUri></externalLink>.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_RMSpictures">
    <title>Azure RMS in action: What administrators and users see</title>
    <content>
      <para>The pictures in this section show some typical examples of how administrators and users see and can use Azure RMS to help protect sensitive or confidential information. </para>
      <alert class="note">
        <para>In all these examples where Azure RMS protects data, the content owner continues to have full access to the data (file or email), even if the applied protection grants permissions to a group that the owner wasn’t a member of, or even if the applied protection includes an expiration date.</para>
        <para>Similarly, IT can always access the protected data without restrictions, by using the super user feature of Rights Management that grants delegated access to authorized users or services that you specify. In addition, IT can track and monitor usage for data that has been protected—for example, who is accessing the data and when.</para>
      </alert>
      <para>For other screenshots and videos that show RMS in action, check the <externalLink><linkText>Microsoft Rights Management services portal</linkText><linkUri>http://www.microsoft.com/rms</linkUri></externalLink>, the <externalLink><linkText>Microsoft Rights Management (RMS) Team Blog</linkText><linkUri>http://blogs.technet.com/b/rms</linkUri></externalLink>, and <externalLink><linkText>curated content for Azure RMS on the Curah! site</linkText><linkUri>http://curah.microsoft.com/Search?query="Azure RMS"</linkUri></externalLink>.</para>
    </content>
    <sections>
      <section address="BKMK_Example_ManagementPortal" expanded="true">
        <title>Activating and configuring Rights Management</title>
        <content>
          <para>Although you can use Windows PowerShell to activate and configure Azure RMS, it’s easiest from the management portal. As soon as the service is activated, you have two default templates that administrators and users can select to quickly and easily apply information protection to files. But you can also create your own custom templates for additional options and settings.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <tbody>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="c6f05fce-3764-46ee-a39d-0f59175de8f0"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink target="_blank">
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/98d53a12-3b19-4622-bb1e-75ef56df5438</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>You can use either the Office 365 admin center (first picture) or the Azure classic portal (second picture) to activate RMS. </para>
                  <para>Just one click to activate and another click to confirm, then information protection is enabled for administrators and users in your organization.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="9c82ebfa-9eb8-46bc-9f21-bfd5524a50e9"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/596e4fec-124c-41b1-8efd-63d5179193fb</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>After activation, two rights policy templates are automatically available for your organization. One template is for read-only (<ui>Confidential View Only</ui> is included in the name), the other for read and modify access (<ui>Confidential</ui>). </para>
                  <para>When these templates are applied to files or emails, they restrict access to users in your organization. This is a very quick and easy way to help prevent your company data leaking to people outside your organization.</para>
                  <alert class="tip">
                    <para>You can easily recognize these default templates, because they are automatically prefixed by your organization name. In our example, <ui>VanArsdel, Ltd</ui>.</para>
                  </alert>
                  <para>If you do not want users to see these templates or if you want to create your own templates, you can do this from the Azure classic portal. As this picture shows, a wizard takes you through the custom template creation process.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="56ea12de-6f16-4fad-b2c5-18b6d4f6b312"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/f5df80e5-efc9-4c0f-91be-060225977356</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>Offline access, expiration settings, and whether to publish the template immediately (make it visible in applications that support Rights Management) are some of the configuration settings available if you decide to create your own templates.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="540b00f9-817c-40bc-bf4a-580dab02077c"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/597a3402-fd5a-4bcf-b5e6-5c983dbde697</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>As a result of publishing these templates, users can now select them in applications such as  File Explorer and Microsoft Word: </para>
                  <list class="bullet">
                    <listItem>
                      <para>A user could choose the default template, <ui>VanArsdel, Ltd – Confidential</ui>. Then, only employees from the VanArsdel organization can open and use this document, even if it’s later emailed to somebody outside the organization or saved to a public location.</para>
                    </listItem>
                    <listItem>
                      <para>A user could choose the custom template that the administrator created, <ui>Sales and Marketing – Read and Print Only</ui>. Then, not only is the file protected from people outside the organization, but it’s also restricted to employees from the Sales and Marketing department. Further, these employees do not have full rights to the document, only read and print. For example, they cannot modify it or copy from it.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>For more information, see <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214">Activating Azure Rights Management</link> and <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c">Configuring Custom Templates for Azure Rights Management</link>.</para>
          <para>To help users protect important company files, see <link xlink:href="58f9a6ff-4121-4c8c-9865-1bb290604ad2">Helping Users to Protect Files by Using Azure Rights Management</link>.</para>
          <para>Next, see some examples of how administrators can apply the templates to automatically configure information protection for files and emails.</para>
        </content>
      </section>
      <section address="BKMK_Example_FCI" expanded="true">
        <title>Automatically protecting files on file servers running Windows Server and File Classification Infrastructure</title>
        <content>
          <para>This example shows how you can use Azure RMS to automatically protect files on file servers that run at least Windows Server 2012 and are configured to use File Classification Infrastructure. </para>
          <para>There are many ways to apply classification values to files. For example, you can inspect the contents of files and accordingly apply built-in classifications such as Confidentiality and Personally Identifiable Information. However, in this example, an administrator creates a custom classification of <ui>Marketing</ui> that is automatically applied to all user documents that are saved in the <ui>Marketing Promotions</ui> folder. Although this folder is protected with NTFS permissions that restricts access to members of the Marketing group, the administrator knows that these permissions can be lost if somebody from that group moves or emails the files. Then, the information in the files could be accessed by unauthorized users.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <tbody>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="53a0818d-a1d9-49a2-9371-0d3fe4a2458c"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/cf18c56b-c301-4640-8d9e-9e677e494091</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>The administrators installs and configures the Rights Management (RMS) connector, which acts as a relay between on-premises servers and Azure RMS. </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="3f2f40a3-b657-4a06-9a43-0f0a55bcee65"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/ba3e247d-ea5e-4009-8eac-74f70270ece0</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>On the file server, the administrator configures the classification rules and tasks so that all user files in the <ui>Marketing Promotions</ui> folder are automatically classified as <ui>Marketing</ui> and protected with RMS encryption. </para>
                  <para>She selects the custom RMS template that was created in our first example, which restricts access to members of the Sales and Marketing departments: <ui>Sales and Marketing – Read and Print Only</ui>.</para>
                  <para>As a result, all documents in that folder are automatically configured with the Marketing classification and protected by the Sales and Marketing RMS template.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="9c3a9711-de51-4ef1-aa9b-650a12e2932a"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/ad666594-68df-4289-835a-235b2af9bf4b</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>How RMS helps to prevent data leaking to people who should not have access to sensitive or confidential information:</para>
                  <list class="bullet">
                    <listItem>
                      <para>Janet, from Marketing, emails a confidential report from the Marketing Promotions folder. This report contains new product features and advertising plans and is requested by a co-worker who is currently traveling on business. However, Janet mistakenly emails it to the wrong person—she didn’t notice that she accidentally selected a recipient with a similar name, in another company. </para>
                      <para>The recipient cannot read the confidential report because he is not a member of the Sales and Marketing group.</para>
                    </listItem>
                  </list>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>For more information, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066">Deploying the Azure Rights Management Connector</link>.</para>
        </content>
      </section>
      <section address="BKMK_Example_DLP" expanded="true">
        <title>Automatically protecting emails with Exchange Online and data loss prevention policies</title>
        <content>
          <para>The previous example showed how you could automatically protect files that contain sensitive or confidential information, but what if the information is not in a file, but in an email message? This is where Exchange Online data loss prevention (DLP) policies comes in, either prompting users to apply information protection (by using Policy Tips) or automatically applying it for them (by using transport rules). </para>
          <para>In this example, the administrator configures a policy to help keep the organization in compliance with US regulations for protecting personally identifiable information data, but rules can also be configured for other compliance regulations, or custom rules that you define.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <tbody>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="8f330a01-3a6e-4635-8d6f-51e6be78e6f0"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/58461319-3981-4b7f-a195-956a1778e907</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>The Exchange template named <ui>U.S. Personally Identifiable Information (PII) Data</ui> is used by the administrator to create and configure a new DLP policy. This template looks for information such as social security numbers and driver license numbers in email messages.</para>
                  <para>The rules are configured so that email messages that contain this information and that are sent outside the organization automatically have rights protection applied by using an RMS template that restricts access to company employees only. </para>
                  <para>Here, the rule is configured to use one of the default templates, <ui>VanArsdel, Ltd – Confidential</ui>, from our first example. But you can also see how the choice of templates includes any custom templates you’ve created, and a <ui>No Do Forward</ui> option that is specific to Exchange.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="fd9d96eb-493f-4ca6-9857-4e3aa531f7ca"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/bfb0762d-06fb-42e4-beff-eb391f4bedf0</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>The hiring manager writes an email message that contains the social security number of a recently hired employee. He sends this email message to Sherrie in the Human Resources department.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="43a9487e-8aae-47fe-ac7f-53996527ccc7"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/59e3b68e-4bed-4962-bb1e-e82d82f8000a</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>If this email message is sent or forwarded to somebody outside the organization, the DLP rule automatically applies rights protection. </para>
                  <para>The email is encrypted when it leaves the organization’s infrastructure, so that the social security number in the email message cannot be read while in transit, or in the recipient’s inbox. The recipient will not be able to read the message unless he or she is a VanArsdel employee.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>For more information, see the following sections: </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9#BKMK_ExchangeIntro">Exchange Online and Exchange Server</link> in the <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link> topic.</para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_ExchangeOnline">Exchange Online: IRM Configuration</link> in the <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36">Configuring Applications for Azure Rights Management</link> topic.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_Example_SharePoint" expanded="true">
        <title>Automatically protecting files with SharePoint Online and protected libraries</title>
        <content>
          <para>This shows how you can easily protect documents when you use SharePoint Online and protected libraries.</para>
          <para>In this example, the SharePoint administrator for Contoso has created a library for each department that they use to centrally store and check out documents for editing and version control. For example, there is a library for Sales, one for Marketing, one for Human Resources, and so on. When a new document is uploaded or created in one of these protected libraries, that document inherits the protection of the library (no need to select a rights policy template) and that document is automatically protected and remains protected, even if it’s moved outside the SharePoint library.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <tbody>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="b445e934-e018-4c6c-912b-3d8633f12764"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/2fc90989-9289-4431-9e6a-07740b7f6e5a</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>The administrator enables Information Rights Management for the SharePoint site. </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="43989403-68d8-4e99-a464-42875af775a7"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/a18f2e99-5ac4-4103-a88c-527846374091</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>Then, she enables Rights Management for a library. Although there are additional options, this simple setting is often all that’s needed.</para>
                  <para>When documents are now downloaded from this library, they  are automatically protected by Rights Management, inheriting the protection that’s configured for the library.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="e51f1c83-60ad-4747-a204-37b8c80b38d8"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/0ebd6806-0190-441e-84db-72ac4b97e4a2</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>When somebody from the sales department checks out this sales report from the library, they can clearly see from the information banner at the top that it’s a protected document with restricted access. </para>
                  <para>The document remains protected even if the user renames it, saves it to another location, or shares it by email. No matter what the file is named, where it’s stored, or whether it’s shared by email, only members of the sales department can read it.</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>For more information, see the following sections: </para>
          <list class="bullet">
            <listItem>
              <para>
                <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9#BKMK_SharePointIntro">SharePoint Online and SharePoint Server</link> in the <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link> topic.</para>
            </listItem>
            <listItem>
              <para>
                <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36#BKMK_SharePointOnline">SharePoint Online: IRM Configuration</link> in the <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36">Configuring Applications for Azure Rights Management</link> topic.</para>
            </listItem>
          </list>
        </content>
      </section>
      <section address="BKMK_Example_SharingApp" expanded="true">
        <title>Users safely share attachments with mobile users</title>
        <content>
          <para>The previous examples showed how administrators can automatically apply information protection to sensitive and confidential data. But there will be some occasions when users might need to apply this protection themselves. For example, they are collaborating with partners in another organization, they need custom permissions or settings that are not defined in templates, for or ad-hoc situations that are not covered by the previous examples. In these situations, users can apply the RMS templates themselves or configure custom permissions.</para>
          <para>This example shows how users can easily share a document with somebody they’re collaborating with from another company, but still be able to protect the document and be confident that the recipient can read it, even from a popular mobile device. This scenario uses the Rights Management sharing application, which you can automatically deploy to Windows computers in your organization. Or, users can install it themselves.</para>
          <para>In this example, Alice from Contoso, emails a confidential Word document that she sends to Bob, at Fabrikam. He reads the document on his iPad, but he could just as easily read it on an iPhone, an Android tablet or phone, a Mac computer, or a Windows phone or computer.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <tbody>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="713ce496-0c24-48e9-95bb-74e6f9823e86"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/feeef78d-3c2e-432b-817d-d06f784be226</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>From her Windows PC, Alice creates a standard email message and attaches a document.</para>
                  <para>She clicks <ui>Share Protected</ui> on the ribbon, which loads the <ui>share protected</ui> dialog box from the RMS sharing application.</para>
                  <para>Alice wants to restrict Bob to viewing and editing the document, and doesn’t want him to copy or print it, so she selects <ui>REVIEWER – View and Edit</ui>. She also wants to be emailed when somebody tries to open the document, and have the ability to revoke the document later if necessary and know that revocation will take effect immediately. </para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="768dafd7-b231-4d5e-b200-ab15ab665a97"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/e748fd78-8bba-4168-96cf-f96def078283</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>Bob sees the email on his iPad.</para>
                  <para>In addition to Alice’s message and attachment, there are instructions that he follows to sign up and install the RMS sharing app on his iPad.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="a40120ff-9de9-44ed-9fd3-1fb7a509a564"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/7dba5ff9-a61d-4a83-8adc-d6ffb0e85df6</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>Bob can now open the attachment. He is first asked to sign in to confirm that he is the intended recipient.  </para>
                  <para>When Bob views the document, he also sees the restricted access information that tells him he can view and edit the document, but not copy or print.</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>
                    <mediaLinkInline>
                      <image xlink:href="dd175b7d-102d-4787-9b4e-684565cf416f"/>
                    </mediaLinkInline>
                  </para>
                  <para>
                    <externalLink>
                      <linkText>Bigger picture</linkText>
                      <linkUri>http://technet.microsoft.com/9f642a2e-58ad-44ab-9f81-f890d15380f9</linkUri>
                    </externalLink> (by default, in same browser window)</para>
                </TD>
                <TD>
                  <para>Alice receives an email message that tells her Bob successfully opened the document that she sent, and when he accessed the document.</para>
                  <para>If Bob forwards his email with the attachment, or saves it where others can access it, or it is intercepted on the network, other people will not be able to read the document. </para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>For more information, see <externalLink><linkText>Protect a file that you share by email</linkText><linkUri>https://technet.microsoft.com/library/dn574735.aspx</linkUri></externalLink> and <externalLink><linkText>View and use files that have been protected</linkText><linkUri>https://technet.microsoft.com/library/dn574741.aspx</linkUri></externalLink> from the <externalLink><linkText>Rights Management sharing application user guide</linkText><linkUri>https://technet.microsoft.com/library/dn339006.aspx</linkUri></externalLink>. </para>
          <para>In addition, the <link xlink:href="1db923bf-7d19-4fdd-a413-bfeb58af5e03">Quick Start Tutorial for Azure Rights Management</link> includes step-by-step instructions for this scenario.</para><para>Now you’ve seen some examples of what Azure RMS can do, you might be interested in how it does it. For technical information about how Azure RMS works, see the next section.</para>
        </content>
      </section>
    </sections>
  </section>
  <section address="BKMK_HowRMSworks">
    <title>How does Azure RMS work? Under the hood</title>
    <content>
      <para>One important thing to understand about how Azure RMS works is that the Rights Management service (and Microsoft) do not see or store your data as part of the information protection process. Information that you protect is never sent to or stored in Azure unless you explicitly store it in Azure or use another cloud service that stores it in Azure. Azure RMS simply makes the data in a document unreadable to anyone other than authorized users and services:</para>
      <list class="bullet">
        <listItem>
          <para>The data is encrypted at the application level and includes a policy that defines the authorized use for that document. </para>
        </listItem>
        <listItem>
          <para>When a protected document is used by a legitimate user or it is processed by an authorized service, the data in the document is decrypted and the rights that are defined in the policy are enforced.</para>
        </listItem>
      </list>
      <para>At a high level, you can see how this process works in the following picture. A document containing the secret formula is protected, and then successfully opened by an authorized user or service. The document is protected by a content key (the green key in this picture). It is unique for each document and is placed in the file header where it is protected by your RMS tenant root key (the red key in this picture). Your tenant key can be generated and managed by Microsoft, or you can generate and manage your own tenant key. </para>
      <para>Throughout the protection process when Azure RMS is encrypting and decrypting, authorizing, and enforcing restrictions, the secret formula is never sent to Azure. </para>
      <mediaLink>
        <image xlink:href="41972473-f0f4-4725-8435-91dc038f7f52"/>
      </mediaLink>
      <para>For a detailed description of what’s happening, see the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df#BKMK_Walthrough">Walkthrough of how Azure RMS works: First use, content protection, content consumption</link> section in this topic.</para>
      <para>For technical details about the algorithms and key lengths that Azure RMS uses, see the next section.  </para>
    </content>
    <sections>
      <section address="BKMK_RMScrytographics">
        <title>Cryptographic controls used by Azure RMS: Algorithms and key lengths</title>
        <content>
          <para>Even if you don't need to know yourself how RMS works, you might be asked about the cryptographic controls that it uses, to make sure that the security protection is industry-standard.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <tbody>
              <tr>
                <TD>
                  <para>Documentation protection method:</para>
                </TD>
                <TD>
                  <para>Algorithm: AES</para>
                  <para>Key length: 128 bits and 256 bits <superscript>1</superscript></para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Key protection method:</para>
                </TD>
                <TD>
                  <para>Algorithm: RSA</para>
                  <para>Key length: 2048 bits</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>Certificate signing:</para>
                </TD>
                <TD>
                  <para>Algorithm: SHA-256</para>
                </TD>
              </tr>
            </tbody>
          </table>
          <para>
            <superscript>1</superscript> 256 bits is used by the Rights Management sharing application for generic protection and native protection when the file has a .ppdf file name extension or is a protected text or image file (such as .ptxt or .pjpg).</para>
        </content>
      </section>
      <section address="BKMK_Walthrough">
        <title>Walkthrough of how Azure RMS works: First use, content protection, content consumption</title>
        <content>
          <para>To understand in more detail how Azure RMS works, let's walk through a typical flow after the <externalLink><linkText>Azure RMS service is activated</linkText><linkUri>https://technet.microsoft.com/library/jj658941.aspx</linkUri></externalLink> and when a user first uses RMS on their Windows computer (a process sometimes known as <embeddedLabel>initializing the user environment</embeddedLabel> or bootstrapping), <embeddedLabel>protects content</embeddedLabel> (a document or email), and then <embeddedLabel>consumes </embeddedLabel> (opens and uses) content that has been protected by somebody else.</para>
          <para>After the user environment is initialized, that user can then protect documents or consume protected documents on that computer.</para>
          <alert class="note">
            <para>If this user moves to another Windows computer, or another user uses this same Windows computer, the initialization process is repeated.</para>
          </alert>
        </content>
        <sections>
          <section>
            <title>Initializing the user environment</title>
            <content>
              <para>Before a user can protect content or consume protected content on a Windows computer, the user environment must be prepared on the device. This is a one-time process and happens automatically without user intervention when a user tries to protect or consume protected content: </para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <mediaLink>
                        <image xlink:href="528204ba-1623-4a91-a3b6-be90c309f865"/>
                      </mediaLink>
                    </TD>
                    <TD>
                      <para>The RMS client on the computer first connects to Azure RMS, and authenticates the user by using their Azure Active Directory account. </para>
                      <para>
                        <?Comment CB: Feedback from Mark Parris, MVP 2014-10-20T08:50:00Z  Id='228?>When the user’s account is federated with Azure Active Directory<?CommentEnd Id='228'
    ?>, this authentication is automatic and the user is not prompted for credentials.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <mediaLink>
                        <image xlink:href="8bb6409f-c518-4a04-955c-5db9324ed862"/>
                      </mediaLink>
                    </TD>
                    <TD>
                      <para>After the user is authenticated, the connection is automatically redirected to the organization’s RMS tenant, which issues certificates that let the user authenticate to Azure RMS in order to consume protected content and to protect content offline.</para>
                      <para>A copy of the user’s certificate is stored in Azure RMS so that if the user moves to another device, the certificates are created by using the same keys. </para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
          <section>
            <title>Content protection</title>
            <content>
              <para>When a user protects a document, the RMS client takes the following actions on an unprotected document:</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <mediaLink>
                        <image xlink:href="6a239cf9-7c3a-4e18-95e5-3a95fd5621a5"/>
                      </mediaLink>
                    </TD>
                    <TD>
                      <para>The RMS client creates a random key (the content key) and encrypts the document using this key with the AES symmetric encryption algorithm.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <mediaLink>
                        <image xlink:href="e38c07b3-4dfa-4857-b5fc-cce791c65d94"/>
                      </mediaLink>
                    </TD>
                    <TD>
                      <para>The RMS client then creates a certificate that includes a policy for the document, either based on a template or by specifying specific rights for the document. This policy includes the rights for different users or groups and other restrictions, such as an expiration date. </para>
                      <para>The RMS client then uses the organization’s key that was obtained when the user environment was initialized and uses this key to encrypt the policy and the symmetric content key. The RMS client also signs the policy with the user’s certificate that was obtained when the user environment was initialized.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <mediaLink>
                        <image xlink:href="fc8be085-1527-4621-821e-c6dc2891229e"/>
                      </mediaLink>
                    </TD>
                    <TD>
                      <para>Finally, the RMs client embeds the policy into a file with the body of the document encrypted previously, which together comprise a protected document. </para>
                      <para>This document can be stored anywhere or shared by using any method, and the policy always stays with the encrypted document.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
          <section>
            <title>Content consumption</title>
            <content>
              <para>When a user wants to consume a protected document, the RMS client starts by requesting access to the Azure RMS service:</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <mediaLink>
                        <image xlink:href="04998d5a-3ee6-4004-b3df-60655392b703"/>
                      </mediaLink>
                    </TD>
                    <TD>
                      <para>The authenticated user sends the document policy and the user’s certificates to Azure RMS. The service decrypts and evaluates the policy, and builds a list of rights (if any) the user has for the document.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <mediaLink>
                        <image xlink:href="7d2b52e2-5a4e-4849-bc94-940c65f67d9b"/>
                      </mediaLink>
                    </TD>
                    <TD>
                      <para>The service then extracts the AES content key from the decrypted policy. This key is then encrypted with the user’s public RSA key that was obtained with the request. </para>
                      <para>The re-encrypted content key is then embedded into an encrypted use license with the list of user rights, which is then returned to the RMS client.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <tbody>
                  <tr>
                    <TD>
                      <mediaLink>
                        <image xlink:href="f31f6895-a7b6-4ffa-8db2-21774b08f88d"/>
                      </mediaLink>
                    </TD>
                    <TD>
                      <para>Finally, the RMS client takes the encrypted use license and decrypts it with its own user private key. This lets the RMS client decrypt the document’s body as it is needed and render it on the screen. </para>
                      <para>The client also decrypts the rights list and passes them to the application, which enforces those rights in the application’s user interface.</para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
          <section>
            <title>Variations</title>
            <content>
              <para>The preceding walkthroughs cover the standard scenarios but there are some variations:</para>
              <list class="bullet">
                <listItem>
                  <para>
                    <embeddedLabel>Mobile devices</embeddedLabel>: When mobile devices protect or consume files with Azure RMS, the process flows are much simpler. Mobile devices don’t first go through the user initialization process because instead, each transaction (to protect or consume content) is independent. As with Windows computers, mobile devices connect to the Azure RMS service and authenticate. To protect content, mobile devices submit a policy and Azure RMS sends them a publishing license and symmetric key to protect the document. To consume content, when mobile devices connect to the Azure RMS service and authenticate, they send the document policy to Azure RMS and request a use license to consume the document. In response, Azure RMS sends the necessary keys and restrictions to the mobile devices. Both processes use TLS to protect the key exchange and other communications.</para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>RMS connector</embeddedLabel>: When Azure RMS is used with the RMS connector, the process flows remain the same. The only difference is that the connector acts as a relay between the on-premises services (such as Exchange Server and SharePoint Server) and Azure RMS. The connector itself does not perform any operations, such as the initialization of the user environment, or encryption or decryption. It simply relays the communication that would usually go to an AD RMS server, handling the translation between the protocols that are used on each side. This scenario lets you use Azure RMS with on-premises services.</para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Generic protection (.pfile)</embeddedLabel>: When Azure RMS generically protects a file, the flow is basically the same for content protection except that the RMS client creates a policy that grants all rights. When the file is consumed, it is decrypted before it is passed to the target application. This scenario lets you protect all files, even if they don’t natively support RMS.</para>
                </listItem>
                <listItem>
                  <para>
                    <embeddedLabel>Protected PDF (.ppdf)</embeddedLabel>: When Azure RMS natively protects an Office file, it also creates a copy of that file and protects it in the same way. The only difference is that the file copy is in PPDF file format, which the RMS sharing application knows how to open for viewing only. This scenario lets you send protected attachments via email, knowing that the recipient on a mobile device will always be able to read them even if the mobile device doesn’t have an app that natively supports protected Office files.</para>
                </listItem>
              </list>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section address="BKMK_NextSteps">
    <title>Next steps</title>
    <content>
      <para>To learn more about Azure RMS, use the other topics in the <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting Started with Azure Rights Management</link> section, such as <link xlink:href="2cdc7bde-4044-4021-b887-11476f99afd9">How Applications Support Azure Rights Management</link> to learn how your existing applications can integrate with Azure RMS to provide an information protection solution. Review <link xlink:href="742877bf-26f5-40e3-b1f7-8475e7c3ce11">Terminology for Azure Rights Management</link> so that you’re familiar with the terms that you might come across as you’re configuring and using Azure RMS, and be sure to also check <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> before you start your deployment. If you want to dive right in and try it out for yourself, use the <link xlink:href="1db923bf-7d19-4fdd-a413-bfeb58af5e03">Quick Start Tutorial for Azure Rights Management</link>.</para>
      <para>If you’re ready to start deploying Azure RMS for your organization, use the <link xlink:href="086600c2-c5d8-47ec-a4c0-c782e1797486">Azure Rights Management Deployment Roadmap</link> for your deployment steps and links for how-to instructions.</para>
      <alert class="tip">
        <para>For additional information and help, use the resources and links in <link xlink:href="7cc73d92-27d6-49ff-a8ab-2fae73519b4b">Information and Support for Azure Rights Management</link>.</para>
      </alert>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting started with Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
