<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use this tutorial to quickly try out Microsoft Azure Rights Management (also known as Azure RMS) for your organization with just 5 steps that should take you less than 15 minutes. You’ll activate the service, securely send a confidential document by email to somebody in another organization, and then be able to track when that document is opened. When the confidential document is emailed, it is encrypted while in transit and can be read only by the person it is sent to, using the permissions that are set by the sender. </para>
    <para>
      <mediaLinkInline>
        <image xlink:href="3c893b16-6b7c-44e5-91e2-057ef42a9932"/>
      </mediaLinkInline>
    </para>
    <para>This tutorial is aimed at IT administrators and consultants, to help them evaluate Azure Rights Management as an information protection solution for an organization. In a production environment, the instructions to activate the service would be done by an administrator and the instructions to send the document would be done by end users. Both sets of instructions are included in this tutorial, to demonstrate the end-to-end scenario of securely sending a confidential document to somebody in another organization. If you have any problems completing this tutorial, send an email message to <externalLink><linkText>AskIPTeam</linkText><linkUri>mailto:askipteam@microsoft.com?subject=Having%20problems%20with%20the%20Quick%20Start%20tutorial</linkUri></externalLink> and we will help you out.</para>
    <para>To complete this tutorial, you will need the following:</para>
    <list class="bullet">
      <listItem>
        <para>A subscription that supports Azure Rights Management . This can be a paid subscription or a trial subscription. If you want to use document tracking, which is required for step 5 in this tutorial, your subscription must support document tracking. For more information about the subscription options and links to free trials, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedSubscriptions">Cloud subscriptions that support Azure RMS</link> section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic.</para>
        <para><?xm-insertion_mark_start author="" time="20150601T172029-0800"?>Tip: <?xm-insertion_mark_end?>If you need to get a subscription, do this in advance because this process can sometimes take a while to complete. </para>
      </listItem>
      <listItem>
        <para>An administrator account to sign in to the Office 365 admin center or the Azure classic portal, so that you can activate the Rights Management service. This account must also have an email address and a working email service (for example, Exchange Online or Exchange Server).</para>
      </listItem>
      <listItem>
        <para>A computer running Windows (minimum of Windows 7 SP1), and which has installed either Office 2016, Office 2013, or Office 2010.</para>
      </listItem>
    </list>
    <para>Let’s get started.</para>
  </introduction>
  <section>
    <title>Step 1: Activate the Rights Management service</title>
    <content>
      <para>
        <mediaLinkInline>
          <image xlink:href="6b066564-3b43-43eb-999a-ce0c0cf7d25b"/>
        </mediaLinkInline>
      </para>
      <para>Even though you might have a subscription that supports Azure Rights Management, the service is disabled by default. To activate it, you can use either the Office 365 admin center, or the Azure classic portal:</para>
      <list class="bullet">
        <listItem>
          <para>If you have an Office 365 subscription that includes Azure Rights Management, or an Office 365 subscription that excludes Azure Rights Management but you have a subscription for Azure RMS Premium: <embeddedLabel>Use the Office 365 admin center</embeddedLabel>.</para>
        </listItem>
        <listItem>
          <para>If you do not have an Office 365 subscription: <embeddedLabel>Use the Azure classic portal</embeddedLabel>.</para>
        </listItem>
      </list>
      <mediaLink>
<image xlink:href="4c4e5cad-e22a-4bcb-81b8-4048187357f1"/>
</mediaLink><procedure>
        <title>To activate Rights Management from the Office 365 admin center</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Go to the <externalLink><linkText>Office 365 portal</linkText><linkUri>https://portal.office.com/</linkUri></externalLink> and sign in with your work or school account.</para>
            </content>
          </step>
          <step>
            <content>
              <para>If the Office 365 admin center does not automatically display, select the app launcher icon in the upper-left and choose <ui>Admin</ui>. The <ui>Admin</ui> tile appears only to Office 365 administrators.</para>
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
            <para>You should now see <ui>Rights management is activated</ui> and the option to deactivate (you might need to manually refresh the page)</para>
            <para>At this time, do not click <ui>advanced features</ui>. This takes you to the Azure classic portal where you can configure templates, which are not needed for this tutorial. Instead, you can close the Office 365 admin center.</para>
          </content>
        </conclusion>
      </procedure>
      <procedure>
        <title>To activate Rights Management from the Azure portal</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Go to the <externalLink><linkText>Azure classic portal</linkText><linkUri>http://go.microsoft.com/fwlink/p/?LinkID=275081</linkUri></externalLink> and sign in.</para>
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
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>The <ui>RIGHTS MANAGEMENT STATUS</ui> should now display <ui>Active</ui> and the <ui>ACTIVATE</ui> option is replaced with <ui>DEACTIVATE</ui>. </para>
            <para>Although you can configure other options for Rights Management in the portal, these are not needed for this tutorial, so you can close the Azure classic portal.</para>
          </content>
        </conclusion>
      </procedure>
      <para>That’s all you need to do for this first step. The service is activated so all users in your organization can now start to protect important and sensitive documents. In a production environment, you might want to restrict who can do this initially, for a phased rollout. But it’s not necessary for this tutorial.</para>
      <para>Although not included here, for a production deployment, you probably will also probably want to configure custom templates. Templates make it easier for users to quickly apply the right settings when they need to protect files. When you activate Rights Management, you automatically get 2 default templates and it’s likely you will want to supplement these with your own custom templates in a production environment. But templates are not needed for this tutorial, so you’re ready to go to the next step.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>If you want more information</para>
            </TD>
            <TD>
              <para>Additional information</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>About activating Rights Management and controlling who can protect files and email when the service is activated   →</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214">Activating Azure Rights Management</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>About the default templates and how to create new, custom templates   →</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c">Configuring Custom Templates for Azure Rights Management</link>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Step 2: Install the Rights Management sharing application</title>
    <content>
      <para>
        <mediaLinkInline>
          <image xlink:href="56ac1537-75ba-453b-b65a-ff12ebe1f468"/>
        </mediaLinkInline>
      </para>
      <para>The Rights Management sharing application (also known as the “RMS sharing app”) isn’t a requirement for Azure Rights Management, but we recommend it for all computers and mobile devices that support Azure Rights Management. The RMS sharing application integrates with Office applications by installing an Office add-in so that users can easily protect files directly from the ribbon. It also makes it possible to protect all files types by applying generic protection for files that are not natively supported by Azure Rights Management, and a document tracking site for users to track and revoke files that they have protected. We’ll be using the document tracking site later in this tutorial.</para>
      <para>This application is free to download and offers a scripted install for production environments. But for this tutorial, we’ll install it locally.</para>
      <mediaLink>
<image xlink:href="01e1ff01-4bca-4690-b8f1-9e8fe2a784b1"/>
</mediaLink><procedure>
        <title>To download and install the Rights Management sharing application</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Go to the <externalLink><linkText>Microsoft Rights Management</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=303970</linkUri></externalLink> page on the Microsoft website. </para>
            </content>
          </step>
          <step>
            <content>
              <para>In the <ui>Computers</ui> section, click the icon for the <ui>RMS app for Windows</ui> and save the <ui>Setup.exe</ui> file to install the Microsoft Rights Management sharing application.</para>
            </content>
          </step>
          <step>
            <content>
              <para>For a local install, you must use an administrator account to run the Setup.exe file that was downloaded. If you are prompted to continue, click <ui>Yes</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>On the <ui>Setup Microsoft RMS</ui> page, click <ui>Next</ui>, and wait for the installation to finish. </para>
            </content>
          </step>
          <step>
            <content>
              <para>When the installation finishes, click <ui>Restart</ui> if prompted to restart your computer, or click  <ui>Close</ui> to complete the installation. </para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>You’re now ready to start protecting files that contain information that you want to share but only with the people that you specify.</para>
          </content>
        </conclusion>
      </procedure>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>If you want more information</para>
            </TD>
            <TD>
              <para>Additional information</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>About a local installation of the Rights Management sharing application for Windows and user instructions   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Rights Management sharing application user guide</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn339006.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>About the scripted installation of the Rights Management sharing application for Windows and more technical information   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Rights Management sharing application administrator guide</linkText>
                  <linkUri>http://technet.microsoft.com/library/dn339003.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>To understand the difference between native protection and generic protection   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>What’s the difference between generic protection and built-in (native) protection?</linkText>
                  <linkUri>https://technet.microsoft.com/library/dn574738.aspx</linkUri>
                </externalLink> </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Step 3: Email your document that you want to protect</title>
    <content>
      <para>
        <mediaLinkInline>
          <image xlink:href="5faba8d1-045d-4caa-b34d-b408a61e6a3b"/>
        </mediaLinkInline>
      </para>
      <para>For this step, first create and save a document using Word that will represent your document that you want to protect, and name it <system>Confidential.docx</system>. For this tutorial, it doesn’t matter what text it actually contains, but you will want it to contain some text so you can more easily confirm that the authorized recipient could read it. For example, you might type: <userInputLocalizable>If you can read this from your email attachment, the sender has successfully shared a file that was protected with Azure RMS.</userInputLocalizable> </para>
      <para>You’re then ready to safely share this document by email.</para>
      <mediaLink>
<image xlink:href="4243c4fb-517d-4f4a-a80a-c0ff470947aa"/>
</mediaLink><procedure>
        <title>To safely share your document by email</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Using Outlook, create a new message and attach the file that you just created. </para>
            </content>
          </step>
          <step>
            <content>
              <para>In the <ui>To</ui> box, type one or more business email addresses. Make sure you specify a business email address, such as <userInput>janetm@contoso.com</userInput> or <userInput>p.dover@fabrikam.com</userInput> because currently, Azure Rights Management doesn’t support personal email addresses that you might use at home from your Internet provider. Don’t worry about whether the person you’re sending it to also has Azure Rights Management or not. </para>
            </content>
          </step>
          <step>
            <content>
              <para>Type a subject, such as  <userInputLocalizable>Confidential document</userInputLocalizable> and then type a short message for the email, such as <userInputLocalizable>Please read this confidential document and do not share it with others.</userInputLocalizable></para>
            </content>
          </step>
          <step>
            <content>
              <para>Then, on the <ui>Message</ui> tab, in the <ui>RMS</ui> group, click <ui>Share Protected</ui> and then click <ui>Share Protected</ui> again:</para>
            </content>
          </step>
          <step>
            <content>
              <para>In the <ui>share protected</ui> dialog box:</para>
              <list class="ordered">
                <listItem>
                  <para>Select <ui>Viewer – View Only</ui>.</para>
                  <para>This means our recipients will be able to view the document but not edit or print it. </para>
                </listItem>
                <listItem>
                  <para>Select <ui>Email me when somebody tries to open these documents</ui>.</para>
                  <para>You’ll get an email notification each time the recipients try to open the attachment, and also if somebody else tries to open it—for example, your recipient forwards the email to co-worker. In this last scenario, you’ll see that access was denied and from the user details, you can decide whether to send that person a copy of the document that they can open.</para>
                </listItem><listItem>
                  <para>Select <ui>Allow me to instantly revoke access to these documents</ui>.</para>
                  <para>This option requires the recipients to have an Internet connection each time they open the attachment but with the benefit that if you later revoke the document, the next time they try to open it, they will not be able to. If you do not select this option, the recipients might be able to open it even without an Internet connection but with the disadvantage that if you later revoke the document, there might be a delay for when that takes effect.</para>
                </listItem>
                
                <listItem>
                  <para>Click <ui>Send Now</ui>.</para>
                  <para>The email with attachment is sent to the email addresses that you specified. In addition to your email message, they will see instructions how to read the attached document that is protected by Azure Rights Management.</para>
                </listItem>
              </list>
            </content>
          </step>
        </steps>
      </procedure>
      <para>Now you’ve sent your protected document, you’re ready to ask your recipients to wait for it to arrive and then open it. But don’t close Outlook, because we’ll use it again in our final step to track the attachment.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>If you want more information</para>
            </TD>
            <TD>
              <para>Additional information</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Full instructions and alternative methods for protecting files that you share by email   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Protect a file that you share by email by using the Rights Management sharing application</linkText>
                  <linkUri>https://technet.microsoft.com/library/dn574735.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>About the options in the <ui>share protected</ui> dialog box   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Dialog box options for the Rights Management sharing application</linkText>
                  <linkUri>https://technet.microsoft.com/library/dn574738.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Step 4: Ask your recipients to open the emailed document</title>
    <content>
      <para>
        <mediaLinkInline>
          <image xlink:href="a0705091-4f9d-4d41-897b-b99e6000e006"/>
        </mediaLinkInline>
      </para>
      <para>Your recipients can use many devices to read the protected document that you sent as an email attachment. The devices include iPads, iPhones, Android tablets and phones, Mac computers, as well as Windows computers.</para>
      <para>Ask them to read the email message that you sent. They will see your email message and before that, the following text: </para>
      <para>
        <ui>The sender has protected the attachments with Microsoft RMS. You must</ui> <externalLink><linkText>sign in</linkText><linkUri>http://aka.ms/rms</linkUri></externalLink> <ui>to open them.</ui> </para>
      <para>When they click the link, it takes them to instructions to install the RMS sharing app and if necessary, sign up for a free account. The free account grants them a subscription for RMS for individuals, which ensures that authorized users can always read a protected document, even if their organization does not have Azure RMS. They are then ready to read the protected attachment by using the following instructions.</para>
      <mediaLink>
<image xlink:href="f370d881-a296-417a-8905-c32a8d8ac9bb"/>
</mediaLink><procedure>
        <title>To view the protected document attachment</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Because Azure Rights Management protected a Word document, there are two attachments for the email message. These are actually two versions of the same file but with different file name extensions. Open the version that has the <system>.ppdf</system> file name extension (<system>Confidential.ppdf</system>). </para>
              <para>If you have a version of <externalLink><linkText>Office on your device that supports Rights Management</linkText><linkUri>https://technet.microsoft.com/library/dn655136.aspx#BKMK_SupportedApplications</linkUri></externalLink>, you can open the other version of the file (<system>Confidential.docx</system>), so that it opens in Word.</para>
            </content>
          </step>
          <step>
            <content>
              <para>If you are prompted for your user name and password, enter your user name in the same format as the email address that was used to send you the email and attachment. For example, <userInput>janetm@contoso.com</userInput> or <userInput>p.dover@fabrikam.com</userInput>. For your password, type the password that you supplied when you signed up for RMS for individuals. Or, if your organization has Azure RMS, enter your usual work password.</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>The document opens and you can now read the contents. For example, it might say <userInputLocalizable>If you can read this from your email attachment, the sender has successfully shared a file that was protected with Azure RMS.</userInputLocalizable> Because it’s read-only, you cannot change the contents.</para>
          </content>
        </conclusion>
      </procedure>
      <para>As an optional step, you could ask your recipient to forward the email to other people that you didn’t include in your original email. Even if those other people work for an organization that has Azure Rights Management or they apply for their own RMS for individuals subscription, they won’t be able to open the attachment. When they are promoted for their user name, access to the document will be denied.</para>
      <para>Now that the recipient has opened the attachment and optionally, forwarded it to somebody else, expect to get an email notification that reports this activity. But email messages are easy to lose over time, so a better way to track who accessed your document is to use the document tracking site, which is covered in the final step.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>If you want more information</para>
            </TD>
            <TD>
              <para>Additional information</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Full instructions for viewing files that are protected by Azure Rights Management   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>View and use files that have been protected by Rights Management</linkText>
                  <linkUri>https://technet.microsoft.com/library/dn574741.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>About the free subscription, RMS for individuals   →</para>
            </TD>
            <TD>
              <para>
                <link xlink:href="2efcb440-fefd-45e9-872b-f471573aadf2">RMS for Individuals and Azure Rights Management</link>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>About the two versions of the file that you see attached to the email message   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>What’s the .ppdf file that’s automatically created?</linkText>
                  <linkUri>https://technet.microsoft.com/library/dn574738.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Step 5: Track your protected document</title>
    <content>
      <para>
        <mediaLinkInline>
          <image xlink:href="3d1ce494-490f-4493-8158-523ecda40fae"/>
        </mediaLinkInline>
      </para>
      <alert class="note">
        <para>For this step, you must have a subscription that supports document tracking. To check whether your subscription includes document tracking, see <externalLink><linkText>Comparison of Rights Management Services (RMS) Offerings</linkText><linkUri>https://technet.microsoft.com/dn858608.aspx</linkUri></externalLink>. </para>
      </alert>
      <para>This step is optional, but most people like to know if the attachment they sent to people has been opened, when, and even from where. For example:</para>
      <list class="bullet">
        <listItem>
          <para>You’re expecting a response from somebody by a specified time and you can see from the document tracking site that she hasn’t opened the document even though the deadline is approaching. You send her a follow-up email or telephone her as a timely reminder.</para>
        </listItem>
        <listItem>
          <para>After seeing that somebody has opened the document, you follow up to ask her if she has any questions or requires additional information.</para>
        </listItem>
      </list>
      <mediaLink>
<image xlink:href="5b799166-171f-45dc-91b8-3f4c3c2992a8"/>
</mediaLink><procedure>
        <title>To track your protected document</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Using Outlook, on the <ui>Home</ui> tab, in the <ui>RMS</ui> group, click <ui>Track Usage</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>If you see the <ui>Protect and share on your terms</ui> page, click <ui>Sign in</ui> and supply your user name and password again. </para>
            </content>
          </step>
          <step>
            <content>
              <para>On the <ui>Your shared documents</ui> page, you’ll see the document that you attached to the email, <system>Confidential.docx</system>. At this point, it’s the only file displayed but as you share additional protected documents, the list will grow.</para>
              <para>From this page, you’ll see when you shared the document (when you sent the email with the protected attachment), the date of the last activity, and the name of the recipient you sent the email to. Click the document name for additional details.</para>
            </content>
          </step>
          <step>
            <content>
              <para>On the new page, which has the name of the file that you clicked, you’ll see summary details for that document only, and a list of other options that are available for the document (<ui>List</ui>, <ui>Timeline</ui>, <ui>Map</ui>, <ui>Settings</ui>).</para>
              <para>Click each option to explore different ways to track your protected document. Or, still on the <ui>Summary</ui> page, click <ui>Open in Excel</ui> to export the information to a spreadsheet, or click <ui>Revoke access</ui> to stop sharing the document.</para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>You can return to this site to track further activity for your protected document, or revoke access if necessary. You can even access the site from your mobile device or tablet, by using a browser with this link: <externalLink><linkText>document tracking</linkText><linkUri>http://go.microsoft.com/fwlink/?LinkId=529562</linkUri></externalLink></para>
          </content>
        </conclusion>
      </procedure>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>If you want more information</para>
            </TD>
            <TD>
              <para>Additional information</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Full instructions for tracking your documents   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Track and revoke your documents when you use the RMS sharing application</linkText>
                  <linkUri>https://technet.microsoft.com/library/dn986611.aspx</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Two minute video that explains and shows document tracking   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>Azure RMS Document Tracking and Revocation</linkText>
                  <linkUri>http://channel9.msdn.com/Series/Information-Protection/Azure-RMS-Document-Tracking-and-Revocation</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>For troubleshooting and customer questions   →</para>
            </TD>
            <TD>
              <para>
                <externalLink>
                  <linkText>FAQ for Document Tracking</linkText>
                  <linkUri>https://technet.microsoft.com/dn947488</linkUri>
                </externalLink>
              </para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
    <title>Next Steps</title>
    <content>
      <para>This tutorial stepped you through just one scenario for how Azure RMS can help protect your data. To see other common uses, see the <externalLink><linkText>Azure RMS in action</linkText><linkUri>https://technet.microsoft.com/library/jj585026.aspx#BKMK_RMSpictures</linkUri></externalLink> section from the <link xlink:href="aeeebcd7-6646-4405-addf-ee1cc74df5df">What is Azure Rights Management?</link> article. There are other sections in this article that you might also find useful, such as how Azure RMS works and what business problems it can solve.</para>
      <para>If you’re ready to start deploying Azure RMS, use the <link xlink:href="086600c2-c5d8-47ec-a4c0-c782e1797486">Azure Rights Management Deployment Roadmap</link> for your deployment steps and links for how-to instructions.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="5214667c-ec69-42ca-8bbf-8cb22da8c62e">Getting Started with Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
