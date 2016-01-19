---
description: na
keywords: na
pagetitle: View and use files that have been protected by Rights Management
search: na
ms.date: 2015-11-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5fa4666-6906-405a-9e0c-2c52d4cd27c8
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# View and use files that have been protected by Rights Management
When the [Rights Management (RMS) sharing application is installed on your computer](https://technet.microsoft.com/library/dn574734%28v=ws.10%29.aspx), you view a protected file by simply double-clicking it. The file might be an attachment in an email message, or you might see it when you use File Explorer.

> [!NOTE]
> Before you can view the protected file, RMS must first confirm that you are authorized to view the file, which it does by checking your user name and password. In some cases, this might be cached and you will not see a prompt that asks for your credentials. In other cases, you will be prompted to supply your credentials.
> 
> If your organization does not use either Azure Rights Management (Azure RMS) or AD RMS, you can apply for a free account that will accept your credentials so that you can open files that are protected by using RMS:
> 
> - To apply for this account, click the link to apply for [RMS for individuals](http://go.microsoft.com/fwlink/?LinkId=309469).
> 
>    When you sign up, use your company email address rather than a personal email address. If you are signing up because you were emailed a protected attachment, use the same email address that was used to send you the email message.
> - For more information, see [RMS for Individuals and Windows Azure Rights Management](http://technet.microsoft.com/library/dn592127.aspx).

## <a name="BKMK_ViewPFILE"></a>To view a protected file
By using File Explorer or the email message that contains the attachment, double-click the protected file, and enter your credentials if prompted to do so.

If you see two versions of the file but with different file name extensions, open the file that has a .ppdf file extension only if the other file does not open. If you cannot open the .ppdf version either, first install the [RMS sharing application](http://technet.microsoft.com/library/dn574734.aspx), which knows how to open files that have a .ppdf file name extension.

> [!NOTE]
> For more information, see “[What’s the .ppdf file that’s automatically created?](../Topic/Dialog_box_options_for_the_Rights_Management_sharing_application.md#BKMK_PPDF)”.

How the file opens depends on how it was protected, which you can tell by looking at the file name extension. In each case, opening the file might be audited and remains audited as long as it is protected. In addition, if the file was sent as an email attachment, the sender might be notified by email each time you open the file.

|File name extension and protection <br /> <br />|More information <br /> <br />|
|--------------------------------------|--------------------|
|The file has a **.pfile** file name extension. <br /> <br />The file was generically protected. <br /> <br />|When you open the file, you see a **protected file** dialog box from the sharing application that tells you who protected the file and that you are expected to honor the co-owner permissions. Click **Open** to read the file. <br /> <br />![](../Image/ADRMS_MSRMSApp_PfilePermission.png) <br /> <br />|
|The file has a **.ppdf** file name extension or is a protected text or image file (such as **.ptxt** or **.pjpg**). <br /> <br />The file has been natively protected as a read-only copy. <br /> <br />|The file opens by using the viewer that installs with the RMS sharing application. This file is read-only, even if you save it to another location or rename it. <br /> <br />|
|Other file name extensions. <br /> <br />The file has been natively protected. <br /> <br />|The file opens by using the application that is associated with the original file name extension, and a restriction banner is displayed at the top of the file. The banner might display the permissions that are applied to the file, or it might provide a link to display them. For example, you might see the following where you must click **Permission is currently restricted** to see the actual permissions that are applied to the file and the people that can access it: <br /> <br />![](../Image/ADRMS_MSRMSApp_RestrictedAccess.png) <br /> <br />|
For a complete list of file name extensions that Rights Management supports, see the [Supported file types and file name extensions](../Topic/Rights_Management_sharing_application_administrator_guide.md#BKMK_SupportFileTypes) sections in the  [Rights Management sharing application administrator guide](../Topic/Rights_Management_sharing_application_administrator_guide.md). If your file name extension is not listed, use a web search to see if it is a file name extension that is supported by another application.

> [!NOTE]
> If, after confirming that the file is protected by Rights Management, and the file does not open, download and use the [RMS Analyzer tool](https://www.microsoft.com/en-us/download/details.aspx?id=46437). Follow the instructions in the tool to check for problems on your computer that might prevent a protected document from opening.

## <a name="BKMK_UserDefined"></a>To use files that have been protected (for example, edit and print the file)
If, after opening the protected file,  you want to do more than just read it (for example, edit, copy, and print it):

|File name extension <br /> <br />|Instructions <br /> <br />|
|-----------------------|----------------|
|The file has a **.pfile** file name extension. <br /> <br />|Save the opened file and give it a new file name extension that is associated with the application that you want to use. <br /> <br />For example, if a file was protected by using the file name document.vsdx.pfile, view the file and in File Explorer, save the file as document.vsdx. <br /> <br />The new file is no longer protected. If you want to protect it, you must do this manually. For instructions, see [Protect a file on a device &#40;protect in-place&#41; by using the Rights Management sharing application](../Topic/Protect_a_file_on_a_device__protect_in-place__by_using_the_Rights_Management_sharing_application.md). <br /> <br />|
|The file has a **.ppdf** file name extension or is a protected text or image file (such as **.ptxt** or **.pjpg**). <br /> <br />|You can only view the file and if you rename or move it, the protection remains with the file. <br /> <br />|
|Other file name extensions. <br /> <br />|Your device must have an application that understands Rights Management to use these files. These applications are called RMS-enlightened applications. Applications from Office 2016, Office 2013,  and Office 2010 (such as Word, Excel, PowerPoint, and Outlook) are examples of applications that are enlightened for Rights Management. But applications that do not come from Microsoft, such as other software companies and your own line-of-business applications, might also be enlightened for Rights Management. <br /> <br />Applications that are enlightened for Rights Management know how to open files that have been protected by other Rights Management enlightened applications. They also persist the protection that is applied to them, even if you edit the file or save it to another file name or another location. These applications let you use the file according to the permissions that are currently applied to the file, so that if you have permissions to use the file, you can do so. For example, you might be able to edit the file but not print it. <br /> <br />|

## Examples and other instructions
For examples for how you might use the Rights Management sharing application, and how-to instructions, see the following sections from the Rights Management sharing application user guide:

- [Examples for using the RMS sharing application](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingExamples)

- [What do you want to do?](../Topic/Rights_Management_sharing_application_user_guide.md#BKMK_SharingInstructions)

## See Also
[Rights Management sharing application user guide](../Topic/Rights_Management_sharing_application_user_guide.md)

