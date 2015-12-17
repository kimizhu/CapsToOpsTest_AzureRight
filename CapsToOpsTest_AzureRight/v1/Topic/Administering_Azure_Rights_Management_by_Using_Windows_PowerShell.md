---
description: na
keywords: na
pagetitle: Administering Azure Rights Management by Using Windows PowerShell
search: na
ms.date: 2015-12-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a890e04a-4b70-41b5-8d5f-3c210a669faa
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# Administering Azure Rights Management by Using Windows PowerShell
Although you can activate Microsoft [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (Azure RMS) by using the [!INCLUDE[o365_2](../Token/o365_2_md.md)] admin center or the Azure classic portal, you can also use the Windows PowerShell module for [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] (AADRM) to do this.

After you have activated [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], further administration for the service might not be required. However, some advanced configuration scenarios might require you to use the Windows PowerShell module for [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)]. The following table lists some of the advanced configuration scenarios that use Windows PowerShell. For a complete list of the available cmdlets with more information about each one, see [Azure Rights Management Cmdlets](http://msdn.microsoft.com/library/azure/dn629398.aspx).

> [!NOTE]
> If you need to install the Windows PowerShell module for [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)], see [Installing Windows PowerShell for Azure Rights Management](../Topic/Installing_Windows_PowerShell_for_Azure_Rights_Management.md).

There is also a supplemental Windows PowerShell module, **RMSProtection**, which supports both Azure RMS and AD RMS. This module supports protecting and removing protection from multiple files so that, for example, you can bulk-protect all files in a folder. For more information, see the [Scripting options for super users](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md#BKMK_RMSProtectionModule) section in the [Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery](../Topic/Configuring_Super_Users_for_Azure_Rights_Management_and_Discovery_Services_or_Data_Recovery.md) topic.

|If you need to… <br /> <br />|…use the following cmdlets <br /> <br />|
|-------------------|------------------------------|
|Migrate from on-premises Rights Management (AD RMS or Windows RMS) to [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. <br /> <br />|[Import-AadrmTpd](http://msdn.microsoft.com/library/azure/dn857523.aspx) <br /> <br />|
|Connect to or disconnect from the [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service for your organization. <br /> <br />|[Connect-AadrmService](http://msdn.microsoft.com/library/azure/dn629415.aspx) <br /> <br />[Disconnect-AadrmService](http://msdn.microsoft.com/library/azure/dn629416.aspx) <br /> <br />|
|Generate and manage your own tenant key – the bring your own key (BYOK) scenario. <br /> <br />|[Add-AadrmKey](http://msdn.microsoft.com/library/azure/dn629418.aspx) <br /> <br />[Get-AadrmKeys](http://msdn.microsoft.com/library/azure/dn629420.aspx) <br /> <br />|
|Activate or deactivate the [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service for your organization. <br /> <br />|[Enable-Aadrm](http://msdn.microsoft.com/library/azure/dn629412.aspx) <br /> <br />[Disable-Aadrm](http://msdn.microsoft.com/library/azure/dn629422.aspx) <br /> <br />|
|Disable or enable the document tracking site for Azure Rights Management. <br /> <br />|[Disable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548471.aspx) <br /> <br />[Enable-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548469.aspx) <br /> <br />[Get-AadrmDocumentTrackingFeature](https://msdn.microsoft.com/library/azure/mt548470.aspx) <br /> <br />|
|Configure onboarding controls for a phased deployment of Azure Rights Management. <br /> <br />|[Get-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857522.aspx) <br /> <br />[Set-AadrmOnboardingControlPolicy](http://msdn.microsoft.com/library/azure/dn857521.aspx) <br /> <br />|
|Create and manage rights policy templates for your organization. <br /> <br />|[Add-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727075.aspx) <br /> <br />[Export-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727078.aspx) <br /> <br />[Get-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727079.aspx) <br /> <br />[Get-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727081.aspx) <br /> <br />[Import-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727077.aspx) <br /> <br />[New-AadrmRightsDefinition](http://msdn.microsoft.com/library/azure/dn727080.aspx) <br /> <br />[Remove-AadrmTemplate](http://msdn.microsoft.com/library/azure/dn727082.aspx) <br /> <br />[Set-AadrmTemplateProperty](http://msdn.microsoft.com/library/azure/dn727076.aspx) <br /> <br />|
|Configure the maximum number of days that content that your organization protects can be accessed without an Internet connection (the use license validity period). <br /> <br />|[Get-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932062.aspx) <br /> <br />[Set-AadrmMaxUseLicenseValidityTime](https://msdn.microsoft.com/library/azure/dn932063.aspx) <br /> <br />|
|Manage the super user feature of [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] for your organization. <br /> <br />|[Enable-AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629400.aspx) <br /> <br />[Disable-AadrmSuperUserFeature](http://msdn.microsoft.com/library/azure/dn629428.aspx) <br /> <br />[Add-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629411.aspx) <br /> <br />[Get-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629408.aspx) <br /> <br />[Remove-AadrmSuperUser](http://msdn.microsoft.com/library/azure/dn629405.aspx) <br /> <br />|
|Manage users and groups who are authorized to administer the [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service for your organization. <br /> <br />|[Add-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629417.aspx) <br /> <br />[Get-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629407.aspx) <br /> <br />[Remove-AadrmRoleBasedAdministrator](http://msdn.microsoft.com/library/azure/dn629424.aspx) <br /> <br />|
|Get a log of [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] administrative tasks for your organization. <br /> <br />|[Get-AadrmAdminLog](http://msdn.microsoft.com/library/azure/dn629430.aspx) <br /> <br />|
|Log and analyze usage logging for [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)]. <br /> <br />|[Enable-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629421.aspx) <br /> <br />[Get-AadrmUsageLog](http://msdn.microsoft.com/library/azure/dn629401.aspx) <br /> <br />[Get-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629425.aspx) <br /> <br />[Get-AadrmUsageLogLastCounterValue](http://msdn.microsoft.com/library/azure/dn629423.aspx) <br /> <br />[Get-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629419.aspx) <br /> <br />[Set-AadrmUsageLogStorageAccount](http://msdn.microsoft.com/library/azure/dn629426.aspx) <br /> <br />[Disable-AadrmUsageLogFeature](http://msdn.microsoft.com/library/azure/dn629404.aspx) <br /> <br />|
|Display the current [!INCLUDE[aad_rightsmanagement_2](../Token/aad_rightsmanagement_2_md.md)] service configuration for your organization. <br /> <br />|[Get-AadrmConfiguration](http://msdn.microsoft.com/library/azure/dn629410.aspx) <br /> <br />|
|Migrate your organization from [!INCLUDE[aad_rightsmanagement_1](../Token/aad_rightsmanagement_1_md.md)] to an on-premises AD RMS deployment. <br /> <br />|[Set-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629429.aspx) <br /> <br />[Get-AadrmMigrationUrl](http://msdn.microsoft.com/library/azure/dn629403.aspx) <br /> <br />|

## See Also
[Azure Rights Management](../Topic/Azure_Rights_Management.md)

