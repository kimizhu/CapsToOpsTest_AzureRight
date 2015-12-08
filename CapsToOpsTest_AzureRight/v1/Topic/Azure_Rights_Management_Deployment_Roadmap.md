---
description: na
search: na
title: Azure Rights Management Deployment Roadmap
ms.service: rights-management
ms.tgt_pltfrm: na
ms.topic: article
ms.date: 2015-08-01
ms.author: e8f708ba3bce4153b61467184c747c7f
---
# Azure Rights Management Deployment Roadmap
<?xml version="1.0" encoding="utf-8"?>
<developerConceptualDocument xmlns="http://ddue.schemas.microsoft.com/authoring/2003/5" xmlns:xlink="http://www.w3.org/1999/xlink" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://ddue.schemas.microsoft.com/authoring/2003/5 http://dduestorage.blob.core.windows.net/ddueschema/developer.xsd">
  <introduction>
    <para>Use the following steps to prepare for, implement, and manage Azure Rights Management (Azure RMS) for your organization.</para>
    <para>However, if you just want to quickly try Azure RMS for yourself, rather than roll it out in a production environment, see <link xlink:href="1db923bf-7d19-4fdd-a413-bfeb58af5e03">Quick Start Tutorial for Azure Rights Management</link>.</para>
    <alert class="important">
      <para>Before you do the following steps, make sure that you have reviewed <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link>.</para>
    </alert>
  </introduction>
  <section>
    <title>Step 1: Confirm that you have a subscription that includes Azure Rights Management</title>
    <content>
      <para>There is more than one type of subscription that includes <token>aad_rightsmanagement_1</token>. See the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb#BKMK_SupportedSubscriptions">Cloud subscriptions that support Azure RMS</link> section in the <link xlink:href="dc78321d-d759-4653-8818-80da74b6cdeb">Requirements for Azure Rights Management</link> topic, and check that your subscription includes the functionality that you want to use in your organization by referring to the table in <externalLink><linkText>Comparison of Rights Management Services (RMS) Offerings</linkText><linkUri>https://technet.microsoft.com/dn858608</linkUri></externalLink>. </para>
    </content>
  </section>
  <section>
    <title>Step 2: Prepare your tenant account to use Rights Management</title>
    <content>
      <para>Before you begin using <token>aad_rightsmanagement_2</token>, do the following preparation: </para>
      <list class="ordered">
        <listItem>
          <para>Make sure that your Azure or Office 365 tenant contains the user accounts and groups that will be used by Azure RMS to authenticate users from your organization. If necessary, create these account and groups, or synchronize them from your on-premises directory. For more information, see <link xlink:href="afbca2d6-32a7-4bda-8aaf-9f93f5da5abc">Prepare for rights management</link>.</para>
        </listItem>
        <listItem>
          <para>Decide whether you want Microsoft to manage your tenant key (the default), or generate and manage your tenant key yourself (known as bring your own key, or BYOK). Note that currently, you cannot use BYOK if you use Exchange Online. For more information, see <link xlink:href="f0d33c5f-a6a6-44a1-bdec-5be1bc8e1e14">Planning and operations for your Rights Management tenant key</link>.</para>
        </listItem>
        <listItem>
          <para>Install the Windows PowerShell module for <token>aad_rightsmanagement_2</token> on at least one computer that has Internet access. You can do this step now, or later. For more information, see <link xlink:href="0d665ed6-b1de-4d63-854a-bc57c1c49844">Install Windows PowerShell for rights management</link>.</para>
        </listItem>
        <listItem>
          <para>If you are currently using on-premises Rights Management services: Perform a migration to move the keys, templates, and URLs to the cloud. For more information, see <link xlink:href="828cf1f7-d0e7-4edf-8525-91896dbe3172">Migrating from AD RMS to Azure Rights Management</link>.</para>
        </listItem>
        <listItem>
          <para>Activate Rights Management so that you can begin to use the service. If a phased deployment is required, configure user onboarding controls to restrict usage to specific users. For more information, see <link xlink:href="f8707e01-b239-4d1a-a1ea-0d1cf9a8d214">Activating rights management</link>. </para>
        </listItem>
      </list>
      <para>Optionally, consider configuring the following: </para>
      <list class="bullet">
        <listItem>
          <para>Custom templates if the default rights policy templates are not sufficient for your organization. You can do this step now, or later. For more information, see <link xlink:href="1775d8d0-9a59-42c8-914f-ce285b71ac1c">Configuring Custom Templates for Azure Rights Management</link>.</para>
        </listItem>
        <listItem>
          <para>Usage logging so that you can monitor how your organization is using Rights Management. You can do this step now, or later. For more information, see <link xlink:href="a735f3f7-6eb2-4901-9084-8c3cd3a9087e">Log and analyze rights management usage</link>.</para>
        </listItem>
      </list>
    </content>
  </section>
  <section>
    <title>Step 3: Configure your applications and services for Rights Management</title>
    <content>
      <para>Configuring your applications can include installing the Rights Management sharing application and enabling support for information rights management (IRM) features in SharePoint Online or Exchange Online. For more information, see <link xlink:href="ea09cbc5-b98b-444e-8b60-5bc3cb199c36">Configuring Applications for Azure Rights Management</link>.</para>
      <para>If you have existing IT services that need to inspect files that Azure RMS will protect—such as data leak prevention (DLP) solutions, content encryption gateways (CEG), and anti-malware products—configure the service accounts to be super users for Azure RMS. For more information, see <link xlink:href="acb4c00b-d3a9-4d74-94fe-91eeb481f7e3">Configuring Super Users for Azure Rights Management and Discovery Services or Data Recovery</link>.</para>
      <para>If you have on-premises services that you want to use with Azure Rights Management, install and configure the Rights Management connector. For more information, see <link xlink:href="90e7e33f-9ecc-497b-89c5-09205ffc5066">Rights management connector</link>.</para>
    </content>
  </section>
  <section>
    <title>Step 4: Publish and consume rights-protected content </title>
    <content>
      <para>You’re now ready to publish and consume protected content, and log how your company is using Rights Management. For more information, see <link xlink:href="18564e4a-9364-4ed2-8f17-89d24fc0d878">Using rights management</link>.</para>
    </content>
  </section>
  <section>
    <title>Step 5: Administer Rights Management for your tenant account as needed</title>
    <content>
      <para>As you begin to use <token>aad_rightsmanagement_2</token>, you might find the <token>aad_rightsmanagement_2</token> module for Windows PowerShell useful to help script or automate administrative changes. For more information, see <link xlink:href="a890e04a-4b70-41b5-8d5f-3c210a669faa">Administering rights management</link>.</para>
    </content>
  </section>
  <relatedTopics>
    <link xlink:href="206a0bfe-0912-4e0e-aa15-484b000b264c">Configuring Azure Rights Management</link>
  </relatedTopics>
</developerConceptualDocument>
