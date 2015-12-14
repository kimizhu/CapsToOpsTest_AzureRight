---
description: na
keywords: na
pagetitle: Rights Management sharing application: Version release history
search: na
ms.author: e8f708ba3bce4153b61467184c747c7f
ms.date: 2015-12-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6751bd90-959f-4eba-91ed-6588ac983762
---
# Rights Management sharing application: Version release history
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>The Rights Management team regularly updates the Rights Management sharing application for fixes and new functionality. Use the following information to see what’s new or changed in a release. The most current release is listed first.</para>
    <para>Versions before January 1, 2015 are not listed.</para>
    <alert class="note">
      <para>If you have feedback or a question about the RMS sharing application, send an email message to <externalLink><linkText>AskIPTeam</linkText><linkUri>mailto:AskIPTeam@microsoft.com?subject=RMS%20sharing%20app:%20Feedback%20or%20question</linkUri></externalLink>.</para>
    </alert>
  </introduction>
  <section>
    <title>Version 1.0.xxxx.0</title>
    <content>
      <table>
        <tbody>
          <tr>
            <TD>
              <para>Released</para>
            </TD>
            <TD>
              <para>12/02/2015</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixes</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Support for non-administrator installation, so that standard users can install the RMS sharing application.</para>
                <para>There are some restrictions for standard users who run Office 2010. For more information, see the  <link xlink:href="2bf09690-9dba-43b7-9e0a-0110915d4081#BKMK_SetupOffice2010">If you are not a local administrator and use Office 2010</link> section in the <link xlink:href="2bf09690-9dba-43b7-9e0a-0110915d4081">Download and install the Rights Management sharing application</link>  user instructions.</para></listItem>
                
              </list>
            </TD>
          </tr>
          
        </tbody>
      </table>
    </content>
    <sections/>
  </section><section>
    <title>Version 1.0.1908.0</title>
    <content>
      <table>
        <tbody>
          <tr>
            <TD>
              <para>Released</para>
            </TD>
            <TD>
              <para>9/16/2015</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixes</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Support for multi-factor authentication (MFA) for Azure RMS, which also removes the dependency on the Microsoft Sign-in Assistant for applications that use modern authentication.</para>
                <para>For more information, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_MFA">Multi-factor authentication (MFA) and Azure RMS</link>   section in  <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link>.</para></listItem>
                
              </list>
            </TD>
          </tr>
          
        </tbody>
      </table>
    </content>
    <sections/>
  </section><section>
    <title>Version 1.0.1784.0</title>
    <content>
      <table>
        <tbody>
          <tr>
            <TD>
              <para>Released</para>
            </TD>
            <TD>
              <para>7/30/2015</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixes</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>The default refresh interval for rights policy templates is reduced from 7 days to 1 day.</para>
                </listItem><listItem>
                  <para>Small number of regressions and minor bugs.</para>
                </listItem>
                
              </list>
            </TD>
          </tr>
          
        </tbody>
      </table>
    </content>
    <sections/>
  </section><section>
    <title>Version 1.0.1770.0</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>Released</para>
            </TD>
            <TD>
              <para>4/25/2015</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixes</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Now, only owner and co-owners can remove protection. Co-authors cannot.</para>
                </listItem>
                <listItem>
                  <para>Files that are on a network share can now be protected.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>New features</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Support for document tracking and revocation. For more information, see <link xlink:href="61f349ce-bdd2-45c1-acc5-bc83937fb187">Track and revoke your documents when you use the RMS sharing application</link></para>
                </listItem>
                <listItem>
                  <para>Template support when you choose <ui>Share Protected</ui>:</para>
                  <list class="bullet">
                    <listItem>
                      <para>You can now select templates.</para>
                    </listItem>
                    <listItem>
                      <para>Instead of the slider, you will see a list box that includes templates and custom permissions.</para>
                    </listItem>
                    <listItem>
                      <para>You no longer see options for <ui>Allow consumption on all devices</ui> and <ui>Enforce usage restrictions</ui>. Instead, <ui>Generic Protection</ui> is automatically selected, depending on the file type.</para>
                    </listItem>
                  </list>
                  <para>For more information, see <link xlink:href="7b91ab30-6363-4929-bcbd-4dfbd05f644a">Dialog box options for the Rights Management sharing application</link>.</para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
    <sections/>
  </section>
  <section>
    <title>Version 1.0.1667.0</title>
    <content>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <tbody>
          <tr>
            <TD>
              <para>Released</para>
            </TD>
            <TD>
              <para>1/19/2015</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Fixes</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>Support for Chinese language fonts in the RMS sharing app PPDF viewer.</para>
                </listItem>
                <listItem>
                  <para>Improved error handling and messaging.</para>
                </listItem>
                <listItem>
                  <para>Fix to an issue with the automatic update notification when a newer version of the app is available for download.</para>
                </listItem>
              </list>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>New features</para>
            </TD>
            <TD>
              <list class="bullet">
                <listItem>
                  <para>
                    <embeddedLabel>Support for multiple email domains within your organization</embeddedLabel>: If you use AD RMS and users in your organization have multiple email domains, this update lets your users consume content that has been protected by users in your organization in other domains. For more information, see the <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25#BKMK_FederatedDomains">AD RMS only: Support for multiple email domains within your organization</link> section in the <link xlink:href="d9992e30-f3d1-48d5-aedc-4e721f7d7c25">Rights Management sharing application administrator guide</link>.</para>
                </listItem>
              </list>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
    <sections/>
  </section>
  <relatedTopics/>
</developerConceptualDocument>
