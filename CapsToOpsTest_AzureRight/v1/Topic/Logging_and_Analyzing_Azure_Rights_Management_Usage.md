---
description: na
keywords: na
pagetitle: Logging and Analyzing Azure Rights Management Usage
search: na
ms.author: e8f708ba3bce4153b61467184c747c7f
ms.date: 2015-12-01
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a735f3f7-6eb2-4901-9084-8c3cd3a9087e
---
# Logging and Analyzing Azure Rights Management Usage
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the information in this topic to help you understand how you can use usage logging with Azure Rights Management (Azure RMS). The Azure Rights Management service can log every request that it makes for your organization, which includes requests from users, actions performed by Rights Management administrators in your organization, and actions performed by Microsoft operators to support your Azure Rights Management deployment.</para>
    <para>You can then use these Azure Rights Management logs to support the following business scenarios:</para>
    <list class="bullet">
      <listItem>
        <para>Analyze for business insights.</para>
        <para>Azure Rights Management writes logs in W3C extended log format into an Azure storage account that you provide. You can then direct these logs into a repository of your choice (such as a database, an online analytical processing (OLAP) system, or a map-reduce system) to analyze the information and produce reports. As an example, you could identify who is accessing your RMS-protected data. You can determine what RMS-protected data people are accessing, and from what devices and from where. You can find out whether people can successfully read protected content. You can also identify which people have read an important document that was protected. </para>
      </listItem>
      <listItem>
        <para>Monitor for abuse.</para>
        <para>Azure Rights Management logging information is available to you in near-real time, so that you can continuously monitor your company’s use of Rights Management . 99.9% of logs are available within 15 minutes of an RMS-initiated action.</para>
        <para>For example, you might want to be alerted if there is a sudden increase of people reading RMS-protected data outside standard working hours, which could indicate that a malicious user is collecting information to sell to competitors. Or, if the same user apparently accesses data from two different IP addresses within a short time frame, which could indicate that a user account has been compromised.</para>
      </listItem>
      <listItem>
        <para>Perform forensic analysis.</para>
        <para>If you have an information leak, you are likely to be asked who recently accessed specific documents and what information did a suspected person access recently. You can answer these type of questions when you use Azure Rights Management and logging because people who use protected content must always get a Rights Management license to open documents and pictures that are protected by Azure Rights Management, even if these files are moved by email or copied to USB drives or other storage devices. This means that you can use Azure Rights Management logs as a definitive source of information for forensic analysis when you protect your data by using Azure Rights Management.</para>
      </listItem>
    </list>
    <alert class="note">
      <para>If you are interested only in the logging of administrative tasks for Azure Rights Management, and do not want to track how users are using Rights Management, you can use the <externalLink><linkText>Get-AadrmAdminLog</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629430.aspx</linkUri></externalLink> Windows PowerShell cmdlet for Azure Rights Management. </para>
      <para>You can also use the Azure classic portal for high-level usage reports that include <ui>RMS usage</ui>, <ui>Most active RMS users</ui>, <ui>RMS device usage</ui>, and <ui>RMS enabled application usage</ui>. To access these reports from the Azure classic portal, click <ui>Active Directory</ui>, select and open a directory, and then click <ui>REPORTS</ui>, </para>
    </alert>
    <para>Use the following sections for more information about Azure Rights Management usage logging.</para>
    <list class="bullet">
      <listItem>
        <para>
          <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e#BKMK_EnableRMSLogging">How to enable RMS logging</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e#BKMK_AccesAndUseLogs">How to access and use your RMS logs</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e#BKMK_ManageStorage">How to manage your RMS log storage</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e#BKMK_Delegate">How to delegate access to your RMS logs</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e#BKMK_Interpret">How to interpret your RMS logs</link>
        </para>
      </listItem>
      <listItem>
        <para>
          <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e#BKMK_PowerShell">Windows PowerShell reference</link>
        </para>
      </listItem>
    </list>
  </introduction>
  <section address="BKMK_EnableRMSLogging">
    <title>How to enable Azure Rights Management usage logging</title>
    <content>
      <para>Azure Rights Management usage logging is optional, so if you want to use it, you must take specific steps. When you use Azure Rights Management usage logging, there is no change in how  Rights Management works and the logging process itself is free. However, you must provide an Azure storage account for the logs and you will be charged for this storage. </para>
      <para>Before you begin, make sure that you meet the following prerequisites to use Azure Rights Management usage logging:</para>
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
              <para>An IT-managed subscription that includes Azure Rights Management</para>
            </TD>
            <TD>
              <para>You must have a Microsoft Azure Rights Management subscription that is managed by your organization. Organizations that use RMS for individuals cannot use Azure Rights Management usage logging.</para>
              <para>If your organization has users who use RMS for individuals, Azure Rights Management usage logging provides a very compelling business reason to convert RMS for individuals into a Microsoft Azure Rights Management subscription. </para>
              <para>For more information about the subscriptions that include Azure RMS, see the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedSubscriptions">Cloud subscriptions that support Azure RMS</link> section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic.</para>
              <para>For more information about RMS for individuals, see <link xlink:href="2efcb440-fefd-45e9-872b-f471573aadf2">RMS for Individuals and Azure Rights Management</link></para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Azure subscription</para>
            </TD>
            <TD>
              <para>You must have a subscription to Azure and sufficient storage on Azure for your Azure Rights Management logs.</para>
            </TD>
          </tr>
          <tr>
            <TD>
              <para>Windows PowerShell for Azure Rights Management</para>
            </TD>
            <TD>
              <para>If you haven’t already done so, download and install the Windows PowerShell module for Azure Rights Management. You will use Windows PowerShell cmdlets to configure and manage your Azure Rights Management usage logs.</para>
              <para>For more information, see <link xlink:href="0d665ed6-b1de-4d63-854a-bc57c1c49844">Installing Windows PowerShell for Azure Rights Management</link>.</para>
            </TD>
          </tr>
        </tbody>
      </table>
      <para>Use the following procedure to enable Azure Rights Management usage logging, which includes steps to create an Azure storage account and then configure Azure to use this storage account for your  Rights Management logs. </para>
      <alert class="note">
        <para>This procedure assumes that you have an Azure account. Azure Rights Management usage logging supports individual accounts but as a best practice, use work or school accounts. In addition, we recommend that you create a dedicated storage account for your Rights Management logs. You must share the storage access keys with Azure Rights Management, and potentially with other people if they will also use the log files.</para>
        <para>For more information about Azure storage, see the <externalLink><linkText>Azure documentation for Storage</linkText><linkUri>http://azure.microsoft.com/documentation/services/storage/</linkUri></externalLink>.</para>
      </alert>
      <procedure>
        <title>How to create your storage account and enable Azure Rights Management usage logging</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Sign in to the <externalLink><linkText>Azure classic portal</linkText><linkUri>https://manage.windowsazure.com/</linkUri></externalLink>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select <ui>Storage</ui>.</para>
              <alert class="tip">
                <para>If you do not see this option, check that you have an Azure subscription in addition to your subscription for Rights Management.</para>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>Click <ui>CREATE A STORAGE ACCOUNT</ui> and for the <ui>URL</ui>, enter a unique name for storage account, and if necessary, change the <ui>LOCATION/AFFINITY GROUP</ui> so that it matches your region.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click <ui>OK</ui>, and wait until you see your storage name show a status of <ui>Online</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click <ui>Manage Access Keys</ui>. </para>
            </content>
          </step>
          <step>
            <content>
              <para>From the <ui>Manage Access Keys</ui> dialog box that shows your primary and secondary access keys, copy the primary access key to the clipboard, and then close the dialog box.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Start Windows PowerShell with the <ui>Run as administrator</ui> option. Run the <externalLink><linkText>Connect-AadrmService</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629415.aspx</linkUri></externalLink> command to connect to the Azure Rights Management service: </para>
              <code>Connect-AadrmService</code>
            </content>
          </step>
          <step>
            <content>
              <para>Use the <externalLink><linkText>Set-AadrmUsageLogStorageAccount</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629426.aspx</linkUri></externalLink> command to specify where you want to keep your Azure Rights Management usage logs, replacing <placeholder>&lt;Access_Key&gt;</placeholder> with the primary access key that you copied in step 6 and <placeholder>&lt;StorageAccount&gt;</placeholder> with the name of the storage account that you created in step 3:</para>
              <code>$accesskey = convertto-securestring -asplaintext -force –string <placeholder>&lt;Access_Key&gt;</placeholder>
Set-AadrmUsageLogStorageAccount -AccessKey $accesskey -StorageAccount <placeholder>&lt;StorageAccount&gt;</placeholder></code>
            </content>
          </step>
          <step>
            <content>
              <para>Use the <externalLink><linkText>Enable-AadrmUsageLogFeature</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629421.aspx</linkUri></externalLink> command to enable Azure Rights Management usage logging:</para>
              <code>Enable-AadrmUsageLogFeature</code>
              <para>You should see the message: <ui>The usage log feature is enabled for the Rights management service.</ui></para>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>Now that usage logging is enabled, Azure Rights Management starts to log all actions for your organization and saves this information to your storage account. Logging information is not available before this point.</para>
          </content>
        </conclusion>
      </procedure>
    </content>
  </section>
  <section address="BKMK_AccesAndUseLogs">
    <title>How to access and use your Azure Rights Management usage logs</title>
    <content>
      <para>Azure Rights Management writes logs to your Azure storage account as a series of blobs. Each blob contains one or more log records, in W3C extended log format. The blob names are numbers, in the order in which they were created. The <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e#BKMK_Interpret">How to interpret the RMS logs</link> section later in this document contains more information about the log contents and their creation.</para>
      <para>It can take a while for logs to appear in your storage account after an Azure Rights Management action. Most logs appear within 15 minutes.</para>
      <para>The storage account that you created for your Azure Rights Management usage logs is like a mailbox and supports reading directly from the storage account, but it is not optimized to be used in this way. Instead, for best performance and to help reduce costs, we recommend that you download the logs to local storage, such as a local folder, a database, or a map-reduce repository. </para>
      <para>You can download your usage logs in two ways:</para>
      <list class="bullet">
        <listItem>
          <para>Use the Windows PowerShell cmdlet <externalLink><linkText>Get-AadrmUsageLog</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629401.aspx</linkUri></externalLink>. </para>
          <para>This is the simplest way to access your usage logs. This cmdlet downloads logs to your computer, downloading each blob as a file to a location that you specify.</para>
        </listItem>
        <listItem>
          <para>Use the <externalLink><linkText>Azure Storage SDK</linkText><linkUri>http://www.windowsazure.com/en-us/develop/net/</linkUri></externalLink> to write your own custom application to download the logs.</para>
          <para>A custom application can provide more flexibility than the Get-AadrmUsageLogs cmdlet. For example, you might want to delegate the download of logs to somebody or a process that must not use your Azure Rights Management administrative credentials. Or, you might want to poll the logs in real time because you want to monitor for misuse.</para>
        </listItem>
      </list>
      <procedure>
        <title>To download your usage logs by using PowerShell</title>
        <steps class="bullet">
          <step>
            <content>
              <para>Start Windows PowerShell with the <ui>Run as administrator</ui> option and run <userInput>Get-AadrmUsageLog –Path &lt;location&gt;</userInput>. For example, after creating a folder named <system>logs</system> on your E drive:</para>
              <list class="bullet">
                <listItem>
                  <para>To download all available logs to your E:\logs folder: <codeInline>Get-AadrmUsageLog -Path "e:\logs"</codeInline></para>
                </listItem>
                <listItem>
                  <para>To download a specific range of blobs: <codeInline>Get-AadrmUsageLog –Path "e:\logs" –FromCounter 1024 –ToCounter 2047</codeInline></para>
                </listItem>
              </list>
            </content>
          </step>
        </steps>
        <conclusion>
          <content>
            <para>When you run these cmdlets, Windows PowerShell displays the name of the last blob that was downloaded. You can assign this name to a variable, which lets you run Get-AadrmUsageLog in a loop or a schedule job, downloading only the incremental logs each time. </para>
            <para>For example:  </para>
            <para>
              <ui>PS C:\&gt; $LastBlobName = Get-AadrmUsageLog –Path "e:\logs"</ui>
            </para>
            <para>
              <ui>1527</ui>
            </para>
            <para>
              <ui>PS C:\&gt; $LastBlobName</ui>
            </para>
            <para>
              <ui>1527</ui>
            </para>
          </content>
        </conclusion>
      </procedure>
      <alert class="tip">
        <para>You can aggregate all your downloaded log files into a CSV format by using <externalLink><linkText>Microsoft’s Log Parser</linkText><linkUri>http://www.microsoft.com/download/details.aspx?id=24659</linkUri></externalLink>, which is a tool to convert between various well-known log formats. You can also use this tool to convert data to SYSLOG format, or import it into a database. After you have installed the tool, run <userInput>LogParser.exe /?</userInput> for help and information to use this tool. For example, you might run the <?Comment CB: What does this do? 2013-10-26T18:06:00Z  Id='40?>following command<?CommentEnd Id='40'
    ?> to import all information into a .log file format: <userInput>logparser –i:w3c –o:csv “SELECT * INTO AllLogs.csv FROM *.log”</userInput>.</para>
      </alert>
      <para>You can suspend and resume usage logging. When you suspend logging, Azure Rights Management retains your storage account information, so that you can easily resume logging again.</para>
      <procedure>
        <title>To suspend and resume usage logging</title>
        <steps class="bullet">
          <step>
            <content>
              <para>To suspend logging, use the following cmdlet: <externalLink><linkText>Disable-AadrmUsageLogFeature</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629404.aspx</linkUri></externalLink></para>
            </content>
          </step>
          <step>
            <content>
              <para>To resume logging, use the following cmdlet: <externalLink><linkText>Enable-AadrmUsageLogFeature</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629421.aspx</linkUri></externalLink></para>
            </content>
          </step>
          <step>
            <content>
              <para>To check whether logging is enabled or disabled, use the following cmdlet: <externalLink><linkText>Get-AadrmUsageLogFeature</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629425.aspx</linkUri></externalLink></para>
              <para>A value of <ui>True</ui> means that usage logging is enabled for Azure Rights Management and a value of <ui>False</ui> means that usage logging is disabled.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
  </section>
  <section address="BKMK_ManageStorage">
    <title>How to manage your Azure Rights Management log storage</title>
    <content>
      <para>You are charged for the storage space that is used to keep your Azure Rights Management logs.</para>
      <para>Azure Rights Management does no automatic management of your usage log files. If you take no action, they will remain in your storage account. However, to conserve space and reduce storage costs, you might want to delete them after you have downloaded them. Or you can choose which files to delete. With one exception, Azure Rights Management does not use these log files, so there are no restrictions about when you can delete them. </para>
      <para>The file that you must not delete (or modify) is named <ui>metadata</ui> that is in the <ui>rms-metadata</ui> container. Azure Rights Management uses this blob to keep track of the last blob number that it used. If this file is deleted, Azure Rights Management starts a new container for logs, with a blob number that starts from 1, and all future downloads that use the Get-AadrmUsageLog cmdlet use this new container to download log files. As a result, any logs in the original container are retained, but orphaned. The only way to download these orphaned logs is to use the Azure storage SDK.</para>
      <alert class="tip">
        <para>Instead of managing your Azure Rights Management log storage yourself, you can delegate this management function to another company by sharing your storage account name and access key. For more information, see the <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e#BKMK_Delegate">How to delegate access to your RMS logs</link> section later in this topic.</para>
      </alert>
      <para>In some circumstances, you might want to regenerate your storage access keys. For example:</para>
      <list class="bullet">
        <listItem>
          <para>You change the company that manages your Azure Rights Management usage logs.</para>
        </listItem>
        <listItem>
          <para>You suspect that your storage access key is compromised.</para>
        </listItem>
      </list>
      <para>If this happens to you, this is when you use the secondary access key (on the assumption that you were previously using the primary access key) to ensure service continuity. When you regenerate the access key that you were not previously using, you then configure Azure Rights Management to use the new key. Use the following procedure to regenerate the secondary access key and configure Azure Rights Management to use it:</para>
      <procedure>
        <title>To regenerate the secondary access key</title>
        <steps class="ordered">
          <step>
            <content>
              <para>Sign in to the <externalLink><linkText>Azure classic portal</linkText><linkUri>https://manage.windowsazure.com/</linkUri></externalLink>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Select <ui>Storage</ui>.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Click <ui>Manage Access Keys</ui>. </para>
            </content>
          </step>
          <step>
            <content>
              <para>In the <ui>Manage Access Keys</ui> dialog box, click <ui>regenerate</ui> next to the secondary access key, and copy the new secondary access key to the clipboard.</para>
            </content>
          </step>
          <step>
            <content>
              <para>Start Windows PowerShell with the <ui>Run as administrator</ui> option and use the <externalLink><linkText>Set-AadrmUsageLogStorageAccount</linkText><linkUri>https://msdn.microsoft.com/library/azure/dn629426.aspx</linkUri></externalLink> cmdlet to configure Azure Rights Management to use this new access key, replacing <placeholder>&lt;StorageAccount&gt;</placeholder> with the name of your storage account and <placeholder>&lt;Access_Key&gt;</placeholder> with the regenerated secondary access key that you just copied:</para>
              <code>Set-AadrmUsageLogStorageAccount -StorageAccount <placeholder>&lt;StorageAccount&gt;</placeholder>-AccessKey <placeholder>&lt;Access_Key&gt;</placeholder></code>
              <alert class="warning">
                <para>Although you can switch to another storage account when you run this command, this action orphans your previous logs and they will no longer be accessible to the Set-AadrmUsageLogStorageAccount cmdlet or similar management commands and functions.</para>
              </alert>
            </content>
          </step>
          <step>
            <content>
              <para>Back in the <ui>Manage Access Keys</ui> dialog box, regenerate your primary access key.</para>
            </content>
          </step>
        </steps>
      </procedure>
    </content>
  </section>
  <section address="BKMK_Delegate">
    <title address="BKMK_DelegateAccess">How to delegate access to your Azure Rights Management usage logs</title>
    <content>
      <para>You can delegate access to your RMS logs by sharing your storage account name and access key. You might want to delegate access to another administrative user, to a developer within your own organization, or to an independent software vendor (ISV). Because they will not have your RMS administrator credentials, they cannot use the Get-AardrmUsageLog cmdlet to download the RMS logs. Instead, they must use the Windows Storage SDK to download the logs. Alternatively, they can write an application to read the logs directly from Azure Storage.</para>
      <para>It is safe to share your storage account name and access key in this way when the storage account is dedicated to your RMS logs. Even though other people have your access key, they cannot use this to access any other storage account or use your RMS tenant account. </para>
    </content>
  </section>
  <section address="BKMK_Interpret">
    <title>How to interpret your Azure Rights Management usage  logs</title>
    <content>
      <para>Use the following information to help you interpret the Azure Rights Management usage  logs.</para>
    </content>
    <sections>
      <section>
        <title>The storage account layout</title>
        <content>
          <para>The first time Azure Rights Management writes logs to your storage account, it creates the following two containers:</para>
          <list class="bullet">
            <listItem>
              <para>
                <ui>Rms-metadata</ui>: This container is reserved for Azure Rights Management . Do not modify or delete this container. </para>
            </listItem>
            <listItem>
              <para>
                <ui>Rms-logs-&lt;guid&gt;</ui>: This container is where Azure Rights Management creates and saves the logs. You can safely delete any files in this container if you no longer want the logging information that they contain.</para>
            </listItem>
          </list>
          <para>Over time, Azure Rights Management might create additional <ui>Rms-logs-&lt;guid&gt;</ui> containers. For example, if the <ui>Rms-metadata</ui> container becomes corrupted or it is accidentally deleted, Azure Rights Management resets its contents and creates a new <ui>Rms-logs-&lt;guid&gt;</ui> container for all future logs. The old logs in the old container are not deleted but are orphaned.</para>
        </content>
      </section>
      <section>
        <title>The log sequence</title>
        <content>
          <para>Azure Rights Management writes the logs as a series of blobs. Each blob contains one or more log records, in extended W3C log format.</para>
          <para>The name of each blob is a number. Within each log container the first blob is named 000000001. Each blob is named sequentially in the order in which it was created. Each blob contains one or more log records. Each log record has a UTC time stamp that indicates when the corresponding request was served by Azure Rights Management.</para>
          <alert class="important">
            <para>The Azure Rights Management logging system is optimized to provide you with logs quickly, rather than in strict sequential order. The order of the blobs, as well as the order of log records within a blob, might be out of chronological sequence. The only reason the blobs are named sequentially is to enable you to efficiently download them incrementally.</para>
            <para>Two examples of potential log sequence results:</para>
            <list class="bullet">
              <listItem>
                <para>The log records in blob 000000004 might overlap chronologically with the log records in blob 000000003. In an extreme case, all log records in blob 000000004 might have been generated before all log records in blob 000000003.</para>
              </listItem>
              <listItem>
                <para>The second log record in a blob might have been generated before the first log record, but was written to storage in reverse order.</para>
              </listItem>
            </list>
          </alert>
          <para>Before you analyze your Azure Rights Management usage logs, we recommend that you download and import the log into a repository where you can sort the logs based on their timestamp. For more information about to download the logs, see the <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e#BKMK_AccesAndUseLogs">How to access and use your RMS logs</link> section in this topic.</para>
          <para>Because the logs are not necessarily chronological but the majority of them are written within 15 minutes of the request, when you identify the logs that you want by using their timestamp , add 15 minutes to the time that you are interested in. Then download these logs. This strategy should ensure that you get almost all logs. </para>
          <para>One other thing to remember is that the timestamp on each log record is the local time of the Azure Rights Management service that processed the request. Because Azure Rights Management runs on multiple servers across multiple data center, sometimes the logs might seem to be out of sequence, even when they are sorted by their timestamp. However, the different is small and usually within a minute. In most cases, this is not an issue that would be a problem for log analysis.</para>
        </content>
      </section>
      <section>
        <title>The blob format</title>
        <content>
          <para>Each blob is in W3C extended log format. It starts with the following two lines:</para>
          <para>
            <ui>#Software: RMS</ui>
          </para>
          <para>
            <ui>#Version: 1.1</ui>
          </para>
          <para>The first line identifies that these are Azure Rights Management logs. The second line identifies that the rest of the blob follows the version 1.1 specification. We recommend that any applications that parse these logs verify these two lines before continuing to parse the rest of the blob.</para>
          <para>The third line enumerates a list of field names that are separated by tabs:</para>
          <para>
            <ui>#Fields: date            time            row-id        request-type           user-id       result          correlation-id          content-id                owner-email           issuer                     template-id             file-name                  date-published      c-info         c-ip</ui></para>
          <para>Each of the subsequent lines is a log record. The values of the fields are in the same order as the preceding line, and are separated by tabs. Use the following table to interpret the fields.</para>
          <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
            <thead>
              <tr>
                <TD>
                  <para>Field name</para>
                </TD>
                <TD>
                  <para>W3C data type</para>
                </TD>
                <TD>
                  <para>Description</para>
                </TD>
                <TD>
                  <para>Example value</para>
                </TD>
              </tr>
            </thead>
            <tbody>
              <tr>
                <TD>
                  <para>date</para>
                </TD>
                <TD>
                  <para>Date</para>
                </TD>
                <TD>
                  <para>UTC date when the request was served. </para>
                  <para>The source is the local clock on the server that served the request.</para>
                </TD>
                <TD>
                  <para>2013-06-25</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>time</para>
                </TD>
                <TD>
                  <para>Time</para>
                </TD>
                <TD>
                  <para>UTC time in 24-hour format when the request was served. </para>
                  <para>The source is the local clock on the server that served the request.</para>
                </TD>
                <TD>
                  <para>21:59:28</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>row-id</para>
                </TD>
                <TD>
                  <para>Text</para>
                </TD>
                <TD>
                  <para>Unique GUID for this log record.</para>
                  <para>This value is useful when you aggregate logs or copy logs into another format.</para>
                </TD>
                <TD>
                  <para>1c3fe7a9-d9e0-4654-97b7-14fafa72ea63</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>request-type</para>
                </TD>
                <TD>
                  <para>Name</para>
                </TD>
                <TD>
                  <para>Name of the RMS API that was requested.</para>
                </TD>
                <TD>
                  <para>AcquireLicense</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>user-id</para>
                </TD>
                <TD>
                  <para>String</para>
                </TD>
                <TD>
                  <para>The user who made the request.</para>
                  <para>The value is enclosed in single quotation marks. Some request types are anonymous, in which case the value is <?Comment CB: ? double quotes, not curly? 2013-10-26T22:34:00Z  Id='41?>”<?CommentEnd Id='41'
    ?>.</para>
                </TD>
                <TD>
                  <para>
                    <?Comment CB: Check curly 2013-10-26T22:34:00Z  Id='42?>‘<?CommentEnd Id='42'
    ?>joe@contoso.com’</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>result</para>
                </TD>
                <TD>
                  <para>String</para>
                </TD>
                <TD>
                  <para>‘Success’ if the request was served successful.</para>
                  <para>The error type in single quotation marks if the request failed.</para>
                </TD>
                <TD>
                  <para>‘Success’</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>correlation-id</para>
                </TD>
                <TD>
                  <para>Text</para>
                </TD>
                <TD>
                  <para>GUID that is common between the RMS client log and server log for a given request.</para>
                  <para>This value can be useful to help troubleshooting client issues.</para>
                </TD>
                <TD>
                  <para>cab52088-8925-4371-be34-4b71a3112356</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>content-id</para>
                </TD>
                <TD>
                  <para>Text</para>
                </TD>
                <TD>
                  <para>GUID, enclosed in curly braces that identifies the protected content (for example, a document).</para>
                  <para>This field has a value only if request-type is AcquireLicense and is blank for all other request types.</para>
                </TD>
                <TD>
                  <para>{bb4af47b-cfed-4719-831d-71b98191a4f2}</para>
                </TD>
              </tr>
              <tr><TD><para>owner-email</para></TD><TD><para>String</para></TD><TD><para>Email address of the owner of the document.</para></TD><TD><para>alice@contoso.com</para></TD></tr><tr><TD><para>issuer</para></TD><TD><para>String</para></TD><TD><para>Email address of the document issuer.</para></TD><TD><para>alice@contoso.com (or) FederatedEmail.4c1f4d-93bf-00a95fa1e042@contoso.onmicrosoft.com'</para></TD></tr><tr><TD><para>Template-id</para></TD><TD><para>String</para></TD><TD><para>ID of the template used to protect the document.</para></TD><TD><para>{6d9371a6-4e2d-4e97-9a38-202233fed26e}</para></TD></tr><tr><TD><para>File-name</para></TD><TD><para>String</para></TD><TD><para>File name of the document that was protected.</para></TD><TD><para>TopSecretDocument.docx</para></TD></tr><tr><TD><para>Date-published</para></TD><TD><para>Date</para></TD><TD><para>Date when the document was protected.</para></TD><TD><para>2015-10-15T21:37:00</para></TD></tr><tr>
                <TD>
                  <para>c-info</para>
                </TD>
                <TD>
                  <para>String</para>
                </TD>
                <TD>
                  <para>Information about the client platform that is making the request.</para>
                  <para>The specific string varies, depending on the application (for example, the operating system or the browser).</para>
                </TD>
                <TD>
                  <para>'MSIPC;version=1.0.623.47;AppName=WINWORD.EXE;AppVersion=15.0.4753.1000;AppArch=x86;OSName=Windows;OSVersion=6.1.7601;OSArch=amd64'</para>
                </TD>
              </tr>
              <tr>
                <TD>
                  <para>c-ip</para>
                </TD>
                <TD>
                  <para>Address</para>
                </TD>
                <TD>
                  <para>IP address of the client that makes the request.</para>
                </TD>
                <TD>
                  <para>64.51.202.144</para>
                </TD>
              </tr>
            </tbody>
          </table>
        </content>
        <sections>
          <section>
            <title>Exceptions for the user-id field</title>
            <content>
              <para>Although the user-id field usually indicates the user who made the request, there are two exceptions where the value does not map to a real user:</para>
              <list class="bullet">
                <listItem>
                  <para>The value <ui>'microsoftrmsonline@&lt;YourTenantID&gt;.rms.&lt;region&gt;.aadrm.com'</ui>.</para>
                  <para>This indicates an Office 365 service, such as Exchange Online or Sharepoint Online, is making the request. In the string, <placeholder>&lt;YourTenantID&gt;</placeholder> is the GUID for your tenant and <placeholder>&lt;region&gt;</placeholder> is the region where your tenant is registered. For example, <ui>na</ui> represents North America, <ui>eu</ui> represents Europe, and <ui>ap</ui> represents Asia.</para>
                </listItem>
                <listItem>
                  <para>If you are using the RMS connector.</para>
                  <para>Requests from this connector are logged with the <?Comment CB: Waiting on information about this – admin doesn’t configure or see it, so how do they know what it is? 2013-10-29T12:40:00Z  Id='43?>service principal <?CommentEnd Id='43'
    ?>name that RMS automatically generates when you install the RMS connector. </para>
                </listItem>
              </list>
            </content>
          </section>
          <section>
            <title>Typical request types</title>
            <content>
              <para>There are many request types for Azure Rights Management but the following table identifies some of the most typically used request types.</para>
              <table xmlns:caps="http://schemas.microsoft.com/build/caps/2013/11">
                <thead>
                  <tr>
                    <TD>
                      <para>Request type</para>
                    </TD>
                    <TD>
                      <para>Description</para>
                    </TD>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <TD>
                      <para>AcquireLicense</para>
                    </TD>
                    <TD>
                      <para>A client from a Windows based machine is requesting a license for RMS-protected content.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T154439-0800"?>AcquirePreLicense<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para>A client, on behalf of the user, is requesting for a license for RMS-protected content<?xm-insertion_mark_start author="" time="20151113T154712-0800"?>.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155005-0800"?>AcquireTemplates<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155013-0800"?>A call was made to acquires templates based on template IDs <?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><?xm-deletion_mark author="" time="20151113T154747-0800" data="&lt;maml:tr xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;
                    &lt;maml:TD&gt;
                      &lt;maml:para&gt;FECreateEndUserLicenseV1&lt;/maml:para&gt;
                    &lt;/maml:TD&gt;
                    &lt;maml:TD&gt;
                      &lt;maml:para&gt;Similar to the AcquireLicense request but from mobile devices.&lt;/maml:para&gt;
                    &lt;/maml:TD&gt;
                  &lt;/maml:tr&gt;"?><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155141-0800"?>AcquireTemplateInformation<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155201-0800"?>A call was made to get the IDs of the template from the service.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T154924-0800"?>AddTemplate<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T154929-0800"?>A call is  made from the Azure <?xm-insertion_mark_end?>classic <?xm-insertion_mark_start author="" time="20151113T154929-0800"?>portal to add a template.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155338-0800"?>BECreateEndUserLicenseV1<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155345-0800"?>A call is  made from a mobile device to create an end-user license.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155420-0800"?>BEGetAllTemplatesV1<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155427-0800"?>A call is  made from a mobile device (back-end) to get all the templates.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para>Certify</para>
                    </TD>
                    <TD>
                      <para>The client is certifying the content for protection.</para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para>Decrypt</para>
                    </TD>
                    <TD>
                      <para>The client is attempting to decrypt the RMS-protected content.</para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155649-0800"?>DeleteTemplateById<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155657-0800"?>A call is  made from the Azure <?xm-insertion_mark_end?>classic <?xm-insertion_mark_start author="" time="20151113T155657-0800"?>portal, to delete a template by template  ID.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160923-0800"?>ExportTemplateById<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160952-0800"?>A call is  made from the Azure <?xm-insertion_mark_end?>classic <?xm-insertion_mark_start author="" time="20151113T160952-0800"?>portal to export a template based on a template ID.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para>FECreateEndUserLicenseV1</para>
                    </TD>
                    <TD>
                      <para>Similar to the AcquireLicense request but from mobile devices.</para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para>FECreatePublishingLicenseV1</para>
                    </TD>
                    <TD>
                      <para>The same as Certify and GetClientLicensorCert combined, from mobile clients.</para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155907-0800"?>FEGetAllTemplates<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T155931-0800"?>A call is  made, from a mobile device (front-end) to get the templates.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160417-0800"?>GetAllTemplates<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160426-0800"?>A call is  made from the Azure <?xm-insertion_mark_end?>classic <?xm-insertion_mark_start author="" time="20151113T160426-0800"?>portal, to get all the templates.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para>GetClientLicensorCert</para>
                    </TD>
                    <TD>
                      <para>The client is requesting a publishing certificate (that is later used to protect content) from a Windows-based computer.</para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160816-0800"?>GetConfiguration<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160840-0800"?>An Azure PowerShell cmdlet is called to get the configuration of the Azure RMS tenant.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160232-0800"?>GetConnectorAuthorizations<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160305-0800"?>A call  is made from the RMS connectors to get their configuration from the cloud.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr>
              <?xm-deletion_mark author="" time="20151113T160111-0800" data="&lt;maml:tr xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;
                    &lt;maml:TD&gt;
                      &lt;maml:para&gt;GetClientLicensorCert&lt;/maml:para&gt;
                    &lt;/maml:TD&gt;
                    &lt;maml:TD&gt;
                      &lt;maml:para&gt;The client is requesting a publishing certificate (that is later used to protect content) from a Windows-based computer.&lt;/maml:para&gt;
                    &lt;/maml:TD&gt;
                  &lt;/maml:tr&gt;"?> <?xm-deletion_mark author="" time="20151113T160748-0800" data="&lt;maml:tr xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;
                    &lt;maml:TD&gt;
                      &lt;maml:para&gt;GetConnectorAuthorizations&lt;/maml:para&gt;
                    &lt;/maml:TD&gt;
                    &lt;maml:TD&gt;
                      &lt;maml:para&gt;A call  is made from the RMS connectors to get their configuration from the cloud.&lt;/maml:para&gt;
                    &lt;/maml:TD&gt;
                  &lt;/maml:tr&gt;"?>   <tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160531-0800"?>GetTenantFunctionalState <?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160537-0800"?>The Azure <?xm-insertion_mark_end?>classic <?xm-insertion_mark_start author="" time="20151113T160537-0800"?>portal is checking whether Azure RMS is activated.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160643-0800"?>GetTemplateById<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T160707-0800"?>A call is  made from the Azure <?xm-insertion_mark_end?>classic <?xm-insertion_mark_start author="" time="20151113T160707-0800"?>portal to get a template by specifying a template ID.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161146-0800"?>ExportTemplateById<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161226-0800"?>A call is being made from the Azure <?xm-insertion_mark_end?>classic <?xm-insertion_mark_start author="" time="20151113T161226-0800"?>portal to export a template by specifying a template ID.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><?xm-deletion_mark author="" time="20151113T161131-0800" data="&lt;maml:tr xmlns:maml=&quot;http://ddue.schemas.microsoft.com/authoring/2003/5&quot;&gt;
                    &lt;maml:TD&gt;
                      &lt;maml:para&gt;&lt;/maml:para&gt;
                    &lt;/maml:TD&gt;
                    &lt;maml:TD&gt;
                      &lt;maml:para&gt;&lt;/maml:para&gt;
                    &lt;/maml:TD&gt;
                  &lt;/maml:tr&gt;"?><tr>
                    <TD>
                      <para>FindServiceLocationsForUser</para>
                    </TD>
                    <TD>
                      <para>A call is made to query for URLs, which is used to call Certify or AcquireLicense.</para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161316-0800"?>Import<?xm-insertion_mark_end?>Template</para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161359-0800"?>A call is  made from the Azure <?xm-insertion_mark_end?>classic <?xm-insertion_mark_start author="" time="20151113T161359-0800"?>portal to import a template.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161440-0800"?>ServerCertify<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161507-0800"?>A call is  made from an RMS-enabled client (such as SharePoint) to certify the server.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr>
                  <tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161535-0800"?>SetUsageLogFeatureState<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161605-0800"?>A call is  made to enable usage logging.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161540-0800"?>SetUsageLogStorageAccount <?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161624-0800"?>A call is  made to specify the location of the Azure RMS logs.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para>SignDigest</para>
                    </TD>
                    <TD>
                      <para>A call is made when a key is used for signing purposes. This is called typically once per AcquireLicence (or FECreateEndUserLicenseV1), Certify, and GetClientLicensorCert (or FECreatePublishingLicenseV1).</para>
                    </TD>
                  </tr><tr>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161644-0800"?>UpdateTemplate<?xm-insertion_mark_end?></para>
                    </TD>
                    <TD>
                      <para><?xm-insertion_mark_start author="" time="20151113T161706-0800"?>A call is  made from the Azure <?xm-insertion_mark_end?>classic <?xm-insertion_mark_start author="" time="20151113T161706-0800"?>portal to update an existing template.<?xm-insertion_mark_end?></para>
                    </TD>
                  </tr>
                </tbody>
              </table>
            </content>
          </section>
        </sections>
      </section>
    </sections>
  </section>
  <section address="BKMK_PowerShell">
    <title>Windows PowerShell reference</title>
    <content>
      <para>Use the following Windows PowerShell cmdlets to help you configure and use Azure Rights Management usage logging:</para>
      <list class="bullet">
        <listItem>
          <para>
            <externalLink>
              <linkText>Disable-AadrmUsageLogFeature</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn629404.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Enable-AadrmUsageLogFeature</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn629421.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Get-AadrmUsageLog</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn629401.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Get-AadrmUsageLogFeature</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn629425.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Get-AadrmUsageLogLastCounterValue</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn629423.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Get-AadrmUsageLogStorageAccount</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn629419.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
        <listItem>
          <para>
            <externalLink>
              <linkText>Set-AadrmUsageLogStorageAccount</linkText>
              <linkUri>https://msdn.microsoft.com/library/azure/dn629426.aspx</linkUri>
            </externalLink>
          </para>
        </listItem>
      </list>
      <para>For more information about using Windows PowerShell for Azure Rights Management, see <link xlink:href="a890e04a-4b70-41b5-8d5f-3c210a669faa">Administering Azure Rights Management by Using Windows PowerShell</link>.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using rights management</link>
  </relatedTopics>
</developerConceptualDocument>
