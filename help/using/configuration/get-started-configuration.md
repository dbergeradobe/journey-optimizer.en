---
title: Get started with [!DNL Journey Optimizer] configuration
description: Learn more about [!DNL Journey Optimizer] configuration
role: Admin
level: Intermediate
exl-id: 0964a484-f957-4aae-a571-61b2a1615026
feature: Application Settings
topic: Administration
---

# Get started with [!DNL Journey Optimizer] configuration {#start-optimizer-configuration}

When accessing [!DNL Journey Optimizer] for the first time, you are provisioned a production sandbox and allocated a certain number of IPs depending on your contract.

To be able to create your journeys and send messages, you need to go though these configuration steps:

1. **Configure messages and channels**: define channel surfaces, adapt and customize the messages.

    * Create channel surfaces to configure all the technical parameters required to deliver messages. [Learn more](channel-surfaces.md)

    * Determine which email address to use in priority for your recipients when several addresses are available in Adobe Experience Platform. [Learn more](primary-email-addresses.md)

    * Manage the number of days during which retries are performed before sending email addresses to the suppression list. [Learn more](manage-suppression-list.md)

    * Define push notifications settings in both [!DNL Adobe Experience Platform] and [!DNL Adobe Experience Platform Launch]. [Learn more](../configuration/push-gs.md)

    <!--* Understand the push notification flow. [Learn more](../configuration/push-gs.md)-->

    * Configure your instance to send SMS (currently only available for a set of organizations - Limited Availability). [Learn more](sms-configuration.md)
    
1. **Delegate subdomains**: for any new subdomain to be used in Journey Optimizer, the first step will be to delegate it. [Learn more](about-subdomain-delegation.md)

    ![](assets/subdomain.png)

1. **Create IP pools**: improve your email deliverability and reputation by grouping together IP addresses provisioned with your instance. [Learn more](ip-pools.md)

    ![](assets/ip-pool.png)

1. **Configure journeys**: in order to build journeys, you need to configure **[!UICONTROL Data Sources]**, **[!UICONTROL Events]** and **[!UICONTROL Actions]**. [Learn more](about-data-sources-events-actions.md)

    ![](assets/admin-menu.png)

    * The **data source** configuration allows you to define a connection to a system to retrieve additional information that will be used in your journeys. [Learn more](../datasource/about-data-sources.md)

    * **Events** allow you to trigger your journeys unitarily to send messages, in real-time, to the individual flowing into the journey. In the event configuration, you configure the events expected in the journeys. The incoming events’ data is normalized following the Adobe Experience Data Model (XDM). Events come from Streaming Ingestion APIs for authenticated and unauthenticated events (such as Adobe Mobile SDK events). [Learn more](../event/about-events.md)
    
    * [!DNL Journey Optimizer] comes with built-in message capabilities that allow you to design and send your content. If you are using a third-party system to send your messages, create a **custom action**. [Learn more](../action/action.md)