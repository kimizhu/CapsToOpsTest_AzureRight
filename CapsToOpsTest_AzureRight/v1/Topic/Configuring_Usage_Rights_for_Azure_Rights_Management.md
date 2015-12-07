<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>When you set protection on files or emails by using Azure Rights Management (Azure RMS) and you do not use a template, you must configure the usage rights yourself. In addition, when you configure custom templates for Azure RMS, you select the usage rights that will then be automatically applied when the template is selected by users, administrators, or configured services. For example, in the Azure  classic portal you can select roles that configure a logical grouping of usage rights, or you can configure the individual rights.</para>
    <para>Use this topic to help you configure the usage rights you want for the application you’re using and understand how these rights are interpreted by applications.</para>
  </introduction>
  <section>
    <title>Usage Rights and Descriptions</title>
    <content>
      <para>The following table lists and describes the usage rights that Rights Management supports, and how they are used and interpreted. In this table, the <embeddedLabel>Common name</embeddedLabel> is typically how you might see the usage right displayed or referenced, as a more friendly version of the single-word value that is used in the code (the <embeddedLabel>Encoding in policy</embeddedLabel> value). The <embeddedLabel>API Constant or Value</embeddedLabel> is the SDK name for an MSIPC API call, used when you write an RMS-enlightened application that checks for a usage right, or adds a usage right to a policy.</para>
      <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
        <thead>
          <tr>
            <TD>
              <para>Common name</para>
            </TD>
            <TD>
              <para>Encoding in policy</para>
            </TD>
            <TD>
              <para>Description</para>
            </TD>
            <TD>
              <para>Implementation in Office custom rights</para>
            </TD>
            <TD>
              <para>Name in the Azure  classic portal</para>
            </TD>
            <TD>
              <para>Name in AD RMS templates</para>
            </TD>
            <TD>
              <para>API constant or value</para>
            </TD>
            <TD>
              <para>Additional information</para>
            </TD>
          </tr>
        </thead>
        <tbody>
          <tr>
            <TD>
              <para>Edit Content, Edit</para>
            </TD>
            <TD>
              <para>DOCEDIT</para>
            </TD>
            <TD>
              <para>Allows the user to modify, rearrange, format or filter the content inside the application. It does not grant the right to save the edited copy.</para>
            </TD>
            <TD>
              <para>As part of the <ui>Change</ui> and <ui>Full Control</ui> options.</para>
            </TD>
            <TD>
              <para><ui>Edit Content</ui></para>
            <?xm-deletion_mark author="" time="20151117T114940-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Reviewer&lt;/maml:ui&gt;, &lt;maml:ui&gt;Co-Author&lt;/maml:ui&gt;, and &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; roles.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Edit</ui></para>
            </TD>
            <TD>
              <para>Not applicable</para>
            </TD>
            <TD>
              <para>In Office applications, this right also allows the user to save the document.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Save</para>
            </TD>
            <TD>
              <para>EDIT</para>
            </TD>
            <TD>
              <para>Allows the user to save the document in its current location.</para>
            </TD>
            <TD>
              <para>As part of the <ui>Change</ui> and <ui>Full Control</ui> options.</para>
            </TD>
            <TD>
              <para><ui>Save File</ui></para>
            <?xm-deletion_mark author="" time="20151117T114953-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Reviewer&lt;/maml:ui&gt;, &lt;maml:ui&gt;Co-Author&lt;/maml:ui&gt;, and &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; roles.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Save</ui></para>
            </TD>
            <TD>
              <para>IPC_GENERIC_WRITEL"EDIT"</para>
            </TD>
            <TD>
              <para>In Office applications, this right also allows the user to modify the document.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Comment</para>
            </TD>
            <TD>
              <para>COMMENT</para>
            </TD>
            <TD>
              <para>Enables the option to add annotations or comments to the content.</para>
            </TD>
            <TD>
              <para>Not implemented</para>
            </TD>
            <TD>
              <para>Not implemented</para>
            </TD>
            <TD>
              <para>Not implemented</para>
            </TD>
            <TD>
              <para>IPC_GENERIC_COMMENTL"COMMENT"</para>
            </TD>
            <TD>
              <para>This right is available in the SDK, is available as an ad-hoc policy in the RMS Protection module for Windows PowerShell, and has been implemented in some software vendor applications. However, it is not widely used and is not currently supported by Office applications.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Save As, Export</para>
            </TD>
            <TD>
              <para>EXPORT</para>
            </TD>
            <TD>
              <para>Enables the option to save the content to a different file name (Save As). Depending on the application, the file might be saved without protection.</para>
            </TD>
            <TD>
              <para>As part of the <ui>Change</ui> and<ui> Full Control</ui> options.</para>
            </TD>
            <TD>
              <para><ui>Export Content (Save As)</ui></para>
            <?xm-deletion_mark author="" time="20151117T115001-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Co-Author&lt;/maml:ui&gt; and &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; roles.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Export (Save As)</ui></para>
            </TD>
            <TD>
              <para>IPC_GENERIC_EXPORTL"EXPORT"</para>
            </TD>
            <TD>
              <para>This right also allows the user to perform other export options in applications, such as <ui>Send to OneNote</ui>.</para>
            </TD>
          </tr><tr>
            <TD>
              <para>Forward</para>
            </TD>
            <TD>
              <para>FORWARD</para>
            </TD>
            <TD>
              <para>Enables the option to forward an email message and to add recipients to the <ui>To</ui> and <ui>Cc</ui> lines.</para>
            </TD>
            <TD>
              <para>Denied when using the <ui>Do Not Forward</ui> standard policy.</para>
            </TD>
            <TD>
              <para><ui>Forward</ui></para>
            <?xm-deletion_mark author="" time="20151117T115005-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Reviewer&lt;/maml:ui&gt;, &lt;maml:ui&gt;Co-Author&lt;/maml:ui&gt;, and &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; roles.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Forward</ui></para>
            </TD>
            <TD>
              <para>IPC_EMAIL_FORWARDL"FORWARD"</para>
            </TD>
            <TD>
              <para>Does not allow the forwarder to grant rights to other users as part of the forward action.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Full Control</para>
            </TD>
            <TD>
              <para>OWNER</para>
            </TD>
            <TD>
              <para>Grants all rights to the document and all available actions can be performed.</para>
            </TD>
            <TD>
              <para>As the <ui>Full Control</ui> custom option.</para>
            </TD>
            <TD>
              <para><ui>Full Control</ui></para>
            <?xm-deletion_mark author="" time="20151117T115006-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; role.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Full Control</ui></para>
            </TD>
            <TD>
              <para>IPC_GENERIC_ALLL"OWNER"</para>
            </TD>
            <TD>
              <para>Includes the ability to remove protection.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Print</para>
            </TD>
            <TD>
              <para>PRINT</para>
            </TD>
            <TD>
              <para>Enables the options to print the content.</para>
            </TD>
            <TD>
              <para>As the <ui>Print Content </ui>option in custom permissions. Not a per-recipient setting.</para>
            </TD>
            <TD>
              <para><ui>Print</ui></para>
            <?xm-deletion_mark author="" time="20151117T115009-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Co-Author&lt;/maml:ui&gt; and &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; roles.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Print</ui></para>
            </TD>
            <TD>
              <para>IPC_GENERIC_PRINTL"PRINT</para>
            </TD>
            <TD>
              <para>No additional information</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Reply</para>
            </TD>
            <TD>
              <para>REPLY</para>
            </TD>
            <TD>
              <para>Enables the Reply option in an email client, without allowing changes in the <ui>To</ui> or<ui> Cc</ui> lines.</para>
            </TD>
            <TD>
              <para>Not applicable</para>
            </TD>
            <TD>
              <para><ui>Reply</ui></para>
            <?xm-deletion_mark author="" time="20151117T115011-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Viewer,&lt;/maml:ui&gt;&lt;maml:ui&gt;Reviewer&lt;/maml:ui&gt;, &lt;maml:ui&gt;Co-Author&lt;/maml:ui&gt;, and &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; roles.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Reply</ui></para>
            </TD>
            <TD>
              <para>IPC_EMAIL_REPLY</para>
            </TD>
            <TD>
              <para>No additional information</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Reply All</para>
            </TD>
            <TD>
              <para>REPLYALL</para>
            </TD>
            <TD>
              <para>Enables the <ui>Reply All</ui> option in an email client, but doesn’t allow the user to add recipients to the <ui>To</ui> or <ui>Cc</ui> lines.</para>
            </TD>
            <TD>
              <para>Not applicable</para>
            </TD>
            <TD>
              <para><ui>Reply All</ui></para>
            <?xm-deletion_mark author="" time="20151117T115014-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Viewer,&lt;/maml:ui&gt;&lt;maml:ui&gt;Reviewer&lt;/maml:ui&gt;, &lt;maml:ui&gt;Co-Author&lt;/maml:ui&gt;, and &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; roles.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Reply All</ui></para>
            </TD>
            <TD>
              <para>IPC_EMAIL_REPLYALLL"REPLYALL"</para>
            </TD>
            <TD>
              <para>No additional information</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>View, Open, Read</para>
            </TD>
            <TD>
              <para>VIEW</para>
            </TD>
            <TD>
              <para>Allows the user to open the document and see the content.</para>
            </TD>
            <TD>
              <para>As the <ui>Read</ui> custom policy, <ui>View</ui> option.</para>
            </TD>
            <TD>
              <para><ui>View Content</ui></para>
            <?xm-deletion_mark author="" time="20151117T115015-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Viewer,&lt;/maml:ui&gt;&lt;maml:ui&gt;Reviewer&lt;/maml:ui&gt;, &lt;maml:ui&gt;Co-Author&lt;/maml:ui&gt;, and &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; roles.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>View</ui></para>
            </TD>
            <TD>
              <para>IPC_GENERIC_READL"VIEW"</para>
            </TD>
            <TD>
              <para>No additional information</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Copy</para>
            </TD>
            <TD>
              <para>EXTRACT</para>
            </TD>
            <TD>
              <para>Enables options to copy data from the document into the same or another document.</para>
            </TD>
            <TD>
              <para>As the <ui>Allow users with Read access to copy content</ui> custom policy option.</para>
            </TD>
            <TD>
              <para><ui>Copy and Extract content</ui></para>
            <?xm-deletion_mark author="" time="20151117T115018-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the &lt;maml:ui&gt;Co-Author&lt;/maml:ui&gt; and &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; roles.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Extract</ui></para>
            </TD>
            <TD>
              <para>IPC_GENERIC_EXTRACTL"EXTRACT"</para>
            </TD>
            <TD>
              <para>In some applications it also allows the whole document to be saved in unprotected form.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>View Rights</para>
            </TD>
            <TD>
              <para>VIEWRIGHTSDATA</para>
            </TD>
            <TD>
              <para>Allows the user to see the policy that is applied to the document.</para>
            </TD>
            <TD>
              <para>Not implemented</para>
            </TD>
            <TD>
              <para><ui>View Assigned Rights</ui></para>
            <?xm-deletion_mark author="" time="20151117T115020-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the  &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; role.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>View Rights</ui></para>
            </TD>
            <TD>
              <para>IPC_READ_RIGHTSL"VIEWRIGHTSDATA"</para>
            </TD>
            <TD>
              <para>Ignored by some applications.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Change Rights</para>
            </TD>
            <TD>
              <para>EDITRIGHTSDATA</para>
            </TD>
            <TD>
              <para>Allows the user to change the policy that is applied to the document. Includes including removing protection.</para>
            </TD>
            <TD>
              <para>Not implemented</para>
            </TD>
            <TD>
              <para><ui>Change Rights</ui></para>
            <?xm-deletion_mark author="" time="20151117T115023-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the  &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; role.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Edit Rights</ui></para>
            </TD>
            <TD>
              <para>IPC_WRITE_RIGHTSL"EDITRIGHTSDATA"</para>
            </TD>
            <TD>
              <para>No additional information</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Allow Macros</para>
            </TD>
            <TD>
              <para>OBJMODEL</para>
            </TD>
            <TD>
              <para>Enables the option to run macros or perform other programmatic or remote access to the content in a document.</para>
            </TD>
            <TD>
              <para>As the <ui>Allow Programmatic Access</ui> custom policy option. Not a per-recipient setting.</para>
            </TD>
            <TD>
              <para><ui>Allow Macros</ui></para>
            <?xm-deletion_mark author="" time="20151117T115024-0800" data="&lt;maml:para xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;Included in the  &lt;maml:ui&gt;Co-Owner&lt;/maml:ui&gt; role.&lt;/maml:para&gt;"?></TD>
            <TD>
              <para><ui>Allow Macros</ui></para>
            </TD>
            <TD>
              <para>Not applicable</para>
            </TD>
            <TD>
              <para>No additional information</para>
            </TD>
          </tr>
        </tbody>
      </table>
    </content>
  </section>
  <section>
<title>Rights included in permissions  levels</title><content><para>Some applications group usage rights together into permissions levels, to make it easier to select usage rights that are typically used together. These permisisons levels help to abstract a level of complexity from users, so they can choose options that are role-based.  For example, <embeddedLabel>Reviewer</embeddedLabel> and <embeddedLabel>Co-Author</embeddedLabel>. Although these options often show users a summary of the rights, they might not include every right that is listed in the previous table.   </para><para>Use the following table for a list of these permissions levels and a complete list of the rights that they contain.</para><table border="1"><thead><tr><TD><para>Permissions Level</para></TD><TD><para>Applications</para></TD><TD><para>Rights <?xm-deletion_mark author="" time="20151117T115252-0800" data="I"?><?xm-insertion_mark_start author="" time="20151117T115252-0800"?>i<?xm-insertion_mark_end?>ncluded (common name)</para></TD></tr></thead><tbody><tr><TD><para>Viewer</para></TD><TD><para>Azure classic portal</para><para>Rights Management sharing application for Windows</para></TD><TD><para>View, Open, Read</para><para>Reply</para><para>Reply All</para></TD></tr><tr><TD><para>Reviewer</para></TD><TD><para>Azure classic portal</para><para>Rights Management sharing application for Windows</para></TD><TD><para>View, Open, Read</para><para>Save</para><para>Edit Content, Edit</para><para>Reply<superscript>*</superscript></para><para>Reply All<superscript>*</superscript></para><para>Forward<superscript>*</superscript></para></TD></tr><tr><TD><para>Co-Author</para></TD><TD><para>Azure classic portal</para><para>Rights Management sharing application for Windows</para></TD><TD><para>View, Open, Read</para><para>Save</para><para>Edit Content, Edit
</para><para>Copy</para><para>View Rights</para><para>Change Rights</para><para>Allow Macros</para><para>Save As, Export</para><para>Print</para><para>Reply<superscript>*</superscript></para><para>Reply All<superscript>*</superscript></para><para>Forward<superscript>*</superscript></para></TD></tr><tr><TD><para>Co-Owner</para></TD><TD><para>Azure classic portal</para><para>Rights Management sharing application for Windows</para></TD><TD><para>View, Open, Read</para><para>Save</para><para>Edit Content, Edit
</para><para>Copy</para><para>View Rights</para><para>Change Rights</para><para>Allow Macros</para><para>Save As, Export</para><para>Print</para><para>Reply<superscript>*</superscript></para><para>Reply All<superscript>*</superscript></para><para>Forward<superscript>*</superscript></para><para>Full Control</para></TD></tr></tbody></table><para><superscript>*</superscript> Not applicable to the Rights Management sharing application for Windows</para></content>
</section><section>
<title>Rights included in the default templates</title><content><para><?xm-insertion_mark_start author="" time="20151117T115127-0800"?>The rights that are included with the default templates are as follows:<?xm-insertion_mark_end?></para><?xm-insertion_mark_start author="" time="20151117T115219-0800"?><table border="1"><thead><tr><TD><para>Display Name</para></TD><TD><para>Rights included (common name) </para></TD></tr></thead><tbody><tr><TD><para>&lt;organization name&gt; - Confidential View Only</para></TD><TD><para>View, Open, Read</para></TD></tr><tr><TD> <para>&lt;organization name&gt; - Confidential</para></TD><TD><para>View, Open, Read</para><para>Save</para><para>Edit Content, Edit</para><para>View Rights</para><para>Allow Macros</para><para>Forward</para><para>Reply</para><para>Reply All</para></TD></tr></tbody></table><?xm-insertion_mark_end?></content>
</section><?xm-deletion_mark author="" time="20150617T153409-0800" data="&lt;maml:section xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;
    &lt;maml:title&gt;Examples for Configuring Usage Rights&lt;/maml:title&gt;
    &lt;maml:content&gt;
      &lt;maml:para&gt;Use the following examples to help you configure usage rights.&lt;/maml:para&gt;
    &lt;/maml:content&gt;
  &lt;/maml:section&gt;"?>
  <?xm-deletion_mark author="" time="20150617T153411-0800" data="&lt;maml:section xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;
    &lt;maml:title&gt;Considerations and Gotchas when Configuration Usage Rights&lt;/maml:title&gt;
    &lt;maml:content&gt;
      &lt;maml:para&gt;Use the following list as things to watch out for when you configure usage rights.&lt;/maml:para&gt;
    &lt;/maml:content&gt;
  &lt;/maml:section&gt;"?>
  <relatedTopics>
    <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
