This scenario and supporting user documentation uses Azure Rights Management to apply persistent protection to Office documents in  [Work Folders](https://technet.microsoft.com/library/dn265974.aspx).  Work Folders uses a role service for file servers running Windows Server that provides a consistent way for users to access their work files from their PCs and devices. Although Work Folders provides its own encryption to protect the files, this protection is lost if the files are then moved outside the Work Folders  environment. For example, users copy the synchronized files and save them to storage that is not under the control of your IT department, or the files are emailed to others.

The additional protection that Azure Rights Management provides helps to prevent accidental data loss by preventing the files from being viewed by people outside your organization. To do this, you can use one of the built-in, default rights policy templates. However, before you deploy this scenario, consider whether users might need to legitimately share any of these files with people outside the organization.   For example, after working on a draft price list, a user then emails the final version to their customer in another organization.  When you use the default Rights Management template for Work Folders, that customer in the other organization couldn't be able to read this emailed document. You can accommodate this requirement by creating a custom template that lets users apply a new rights policy to the file, which replaces the original restriction of all employees to the people that they specify in the email.

> [!NOTE]
> When you use the custom template that is documented for this scenario, although   users can intentionally share files with people that you didn't define in the template, the additional protection that you're applying with Azure Rights Management provides a lot of benefits. This additional protection prevents accidental data loss if the content is moved outside the Work Folders boundary, because the content remains protected from unauthorized users, whether it is at rest or transmitted. For example, a user loses or has stolen a device that is using Work Folders, or the content is transferred over unsecured infrastructure.
> 
> If a user shares the content with somebody in another organization, by using the Share Protected functionality from the Rights Management sharing application, that user replace the original protection with a protection policy that they define. As a result, the content is still protected from unauthorized access and only the people that the user specifies can access the content.

You can apply this persistent protection to all Office documents in users' Work Folders, or  only to files that contain sensitive or high-business-impact data.

The instructions are suitable for the following set of circumstances:

- The Work Folder files that you want to protect with persistent protection are Office files. These files can be natively protected by Azure Right Management and do not change their file name extension or require a different work flow to open them.

- You want to apply the persistent protection to  all Office files in users' Work Folders, or to selective files that have been identified by using File Classification Infrastructure from File Server Resource Manager in Windows Server.

- For files that must be shared with people that are not specified in the rights policy template (for example, users in another organization), users must apply a new rights policy to replace the original rights policy protection .

## Deployment Instructions
![](../Image/AzRMS_AdminBanner.png)

Make sure that the following requirements are in place, and then follow the instructions for the supporting procedures before going on to the user documentation.

## Requirements for this Scenario
For the  instructions for this scenario to work, the following must be in place:

|Check <br /> <br />|Requirement <br /> <br />|If you need more information <br /> <br />|
|---------|---------------|--------------------------------|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|Azure Rights Management is activated <br /> <br />|[Activating Azure Rights Management](https://technet.microsoft.com/library/jj658941.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|You have synchronized your on-premises Active Directory user accounts with Azure Active Directory or Office 365, including their email address. This is required for all users that use Work Folders. <br /> <br />|[Preparing for Azure Rights Management](https://technet.microsoft.com/library/jj585029.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|Either: <br /> <br /><ul><li>To use a default template for all users that does not allow users to apply a new rights policy: You have not archived the default template, **&lt;organization name&gt; - Confidential** </li><li>To use a custom template that is suitable for users to apply a new rights policy: You use the instructions that follow to create a custom template </li> </ul>|[Configuring Custom Templates for Azure Rights Management](https://technet.microsoft.com/library/dn642472.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|The Rights Management connector is installed, authorized for the Windows Server computer, and configured for the **FCI Server** role. <br /> <br />|[Deploying the Azure Rights Management Connector](https://technet.microsoft.com/library/dn375964.aspx) <br /> <br />|
|![](../Image/4d269a30-a873-45c5-87de-30ee6558e7b0.gif) <br /> <br />|The Rights Management sharing application is deployed to users’ computers that run Windows <br /> <br />|[Automatic deployment for the Microsoft Rights Management sharing application](https://technet.microsoft.com/library/dn339003%28v=ws.10%29.aspx) <br /> <br />|

#### Configuring the custom rights policy template so that users can share Work Folders files outside the organization

1. Sign into the Azure portal, and navigate to the Azure Rights Management templates.

2. Copy the **&lt;organization name&gt; - Confidential** template, and supply a name and description for this Work Folders scenario.  We suggest the following:

   - Name:  **Content protected by Work Folders**

   - Description: **This content is protected by Work Folders and is restricted to company employees only. To share this content with people outside the organization, attach the document to an email message and use the Share Protected function.**

3. On the **RIGHTS** page:

   - Change the existing  rights from **Custom** to **Co-Owner**.

4. On the **CONFIGURE** page:

   - Make sure the **STATUS** is set to **PUBLISH**

   - For the **name and description**, delete the entries for the languages that you do not use. For the languages that you do use, update the **NAME** and **DESCRIPTION** so that these match the name and description that you gave this template, using the specified language.

5. Save the template.

#### Configuring Work Folders to apply persistent protection to Office file

1. Implement Work Folders for your users so that locally saved files are synchronized to a file server folder, known as a *sync share*. The sync share should be on the file server same server that runs the Rights Management connector.

   This solution requires the Work Folders role service in Server Manager, for the File and Storage Services role.  The file server must be running a minimum version of Windows Server 2012 R2, and this file server can be on-premises, or    in a virtual machine in Azure. For more information about Work Folders, see [Work Folders Overview](https://technet.microsoft.com/library/dn265974.aspx).

   For deployment instructions, see [Deploying Work Folders](https://technet.microsoft.com/library/dn528861.aspx). Make sure that you select the built-in  encryption (the option **Encrypt Work Folders**), which will be applied in addition to Azure Rights Management encryption.

2. To complete the configuration for the Rights Management connector:

   1. Using File Server Resource Manager, create a file management task that identifies the sync share folder as the scope.

   2. For the  action, choose **RMS encryption**, and select a template:

      - If you did not create a custom template because you do not want users to be able to share files with others outside the organization, select the template name of **&lt;organization name&gt; - Confidential**. For example, **VanArsdel, Ltd - Confidential**.

      - If you created a custom template by using the preceding instructions, select this template. For example, **Content protected by Work Folders**.

   3. Specify a schedule that allows plenty of time for all the Office files to be encrypted by Azure Rights Management, and specify the option to **Run continuously on new files**.

3. To manually test this configuration, make sure that the folder contains some Office files, and then use the **Run File Management Task Now** option, and select **Wait for the task to complete**.

   Wait for the **Running File Management Task** dialog box to close and then view the results in the automatically displayed report. You should see the number of files that are in your chosen folder in the **Files** field. Confirm that the files in your chosen folder are now protected by Azure Rights Management. For example, open a file and confirm that you see the information banner at the top of the document that displays the name and description of the Rights Management template.

4. If you decided to selectively protect files by using File Classification Infrastructure, configure your classification rule and schedule, and then modify the file management task to include this classification property as a condition.

## User Documentation Instructions
If the files you are protecting with Azure Rights Management do not need to be shared with people outside your organization,  you might not have to provide users with any additional instructions than those you provide for using Work Folders. When  users open the files that are protected by Azure Rights Management and the default template, the files  open as usual in Office, with the only difference being that users might be prompted to authenticate, and they will see an information bar at the top of the document that informs them that the content contains proprietary information intended for internal users only.

If you configured the custom template as documented for this scenario,  users will see the template description in the information bar: **This content is protected by Work Folders and is restricted to company employees only. To share this content with people outside the organization, attach the document to an email message and use the Share Protected function.**. Although this description provides a summary of how to share the file outside the organization, users will probably need detailed instructions how to do this, especially for the first few times they do this. To support this follow-on scenario, use the administrator and end-user instructions from  [Scenario - Share an Office File with Users in Another Organization](../Topic/Scenario_-_Share_an_Office_File_with_Users_in_Another_Organization.md).

> [!TIP]
> If you decided not to use the custom template in these instructions, because you do not want users to be able to share these files outside the organization without IT oversight, let  your help desk know so that if the sharing requirement is legitimate, it can be accommodated by using whatever mechanism is most appropriate for your business. For example,    somebody who is a [super user](https://technet.microsoft.com/library/mt147272.aspx) could apply a new template to the content that grants the requesting user Full Control rights, so that this user can then use the Share Protected function.
> 
> After a period of time, if you discover there are many such requests, you might decide to define your own custom template for this scenario that grants only specific users (such as managers or the help desk)   the Co-Owner option while standard users are granted Co-Author or whatever [rights](https://technet.microsoft.com/library/mt169423.aspx) you decide are suitable.

