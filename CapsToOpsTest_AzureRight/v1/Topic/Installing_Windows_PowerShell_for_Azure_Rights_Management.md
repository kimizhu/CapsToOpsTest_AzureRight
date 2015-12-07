Use the following information to help you install Windows PowerShell for Microsoft [!INC[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS).

You can use this Windows PowerShell module to administer [!INC[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] from the command line by using any computer that has an Internet connection and that meets the prerequisites listed in the next section. Windows PowerShell for [!INC[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] supports scripting for automation or might be necessary for advanced configuration scenarios. For more information about the administration tasks and configurations that the module supports, see [Administering Azure Rights Management by Using Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md).

## Prerequisites
This table lists the prerequisites to install and use Windows PowerShell for [!INC[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)].

|Requirement <br /> <br />|More information <br /> <br />|
|---------------|--------------------|
|A version of Windows that supports the [!INC[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] administration module <br /> <br />|Check the list of supported operating systems in the **System Requirements** section of the [download page for the Azure Rights Management Administration Tool](http://go.microsoft.com/fwlink/?LinkId=257721). <br /> <br />|
|Minimum version of Windows PowerShell: 2.0 <br /> <br />|Support for the [!INC[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] administration module is introduced in Windows PowerShell 2.0. <br /> <br />By default, most Windows operating systems install with at least version 2.0 of Windows PowerShell. If you need to install Windows PowerShell 2.0, see [Install Windows PowerShell 2.0](http://msdn.microsoft.com/library/ff637750.aspx). **Tip:** You can confirm the version of Windows PowerShell that you are running by typing **$PSVersionTable** in a Windows PowerShell session. <br />|
|Minimum version of the Microsoft .NET Framework: 4.5 **Tip:** This version of the Microsoft .NET Framework is included with the later operating systems, so you should only need to manually install it if your client operating system is less than Windows 8.0 or your server operating system is less than Windows Server 2012. <br />|If this is not already installed, you can download the [Microsoft .NET Framework 4.5](http://www.microsoft.com/download/details.aspx?id=30653). <br /> <br />This version of the Microsoft .NET Framework is required for some of the classes that the [!INC[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] administration module uses. <br /> <br />|
|Microsoft Online Services Sign-In Assistant 7.0 <br /> <br />|The Microsoft Online Services Sign-In Assistant is required for [!INC[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] authentication. <br /> <br />For more information, see [Download Center: Microsoft Online Services Assistant for IT Professionals RTW](http://www.microsoft.com/en-us/download/details.aspx?id=41950). <br /> <br />|

## How to install the Rights Management administration module

1. Go to the Microsoft Download Center and [download the Azure Rights Management Administration Tool](https://go.microsoft.com/fwlink/?LinkId=257721), which contains the [!INC[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] administration module for Windows PowerShell.

2. From the local folder where you downloaded and saved the [!INC[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] installer file, double-click the executable file that you downloaded for your platform (WindowsAzureADRightsManagementAdministration_x64 or WindowsAzureADRightsManagementAdministration_x86.exe) to start the Azure AD Rights Management Administration Setup Wizard.

3. Complete the wizard.

Windows PowerShell for [!INC[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] is now installed.

## Next steps
To see which cmdlets are available, start Windows PowerShell with the **Run as administrator** option and type the following:

```
Get-Command -Module aadrm
```
Use `the Get-Help <cmdlet_name>` command to see the Help for a specific cmdlet.

For more information:

- Full list of cmdlets available: [Azure Rights Management Cmdlets](https://msdn.microsoft.com/library/windowsazure/dn629398.aspx)

- List of main configuration scenarios that support Windows PowerShell: [Administering Azure Rights Management by Using Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

Before you can run any commands that configure the [!INC[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] service, you must connect to the  service by using the [Connect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629415.aspx) cmdlet. When you have finished running the configuration commands that you want, disconnect from the service by using the [Disconnect-AadrmService](https://msdn.microsoft.com/library/windowsazure/dn629416.aspx) cmdlet.

> [!NOTE]
> If you have not yet activated [!INC[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], you can do this after you have connected to the service, by using the [Enable-Aadrm](https://msdn.microsoft.com/library/windowsazure/dn629412.aspx) cmdlet.

## See Also
[Administering Azure Rights Management by Using Windows PowerShell](../Topic/Administering_Azure_Rights_Management_by_Using_Windows_PowerShell.md)

