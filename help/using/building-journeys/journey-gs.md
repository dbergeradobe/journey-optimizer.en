---
title: Get started with journeys
description: Key steps to build your first journey with Adobe Journey Optimizer
feature: Journeys
topic: Content Management
role: User
level: Intermediate
exl-id: d940191e-8f37-4956-8482-d2df0c4274aa
---
# Get started with journeys{#jo-quick-start}

## Prerequisites{#start-prerequisites}

In order to send messages with journeys, the following configurations are required:

1. **Configure an event**: if you want to trigger your journeys unitarily when an event is received, you need to configure an event. You define the expected information and how to process it. This step is performed by a **technical user**. [Read more](../event/about-events.md).

   ![](assets/jo-event7bis.png)  
 
1. **Create a segment**: your journey can also listen to Adobe Experience Platform segments in order to send messages in batch to a specified set of profiles. For this, you need to create segments. [Read more](../segment/about-segments.md).

   ![](assets/segment2.png)  

1. **Configure the data source**: you can define a connection to a system to retrieve additional information that will be used in your journeys, for example in your conditions. A built-in Adobe Experience Platform data source is also configured at provisioning time. This step is not required if you only leverage data from the events in your journey. This step is performed by a **technical user**. [Read more](../datasource/about-data-sources.md) 

   ![](assets/jo-datasource.png)  

1. **Configure an action**: If you're using a third-party system to send your messages, you can create a custom action. Learn more in this [section](../action/action.md). This step is performed by a **technical user**. If you're using Journey Optimizer built-in message capabilities, you just need to add a channel action to your journey and design your content. See [this section](../messages/get-started-content.md). 

    ![](assets/custom2.png)

## Build your journey{#jo-build}

>[!CONTEXTUALHELP]
>id="ajo_journey_create"
>title="Build your journey"
>abstract="This screen displays the list of existing journeys. Open a journey or click 'Create journey', and combine the different event, orchestration and action activities to build your multi-step cross-channel scenarios."

This step is performed by the **business user**. This is where you create your journeys. Combine the different event, orchestration and action activities to build your multi-step cross-channel scenarios.

Here are the main steps to send messages through journeys:

1. In the JOURNEY MANAGEMENT menu section, click **[!UICONTROL Journeys]**. The list of journeys is displayed.

    ![](assets/interface-journeys.png)

1. Click **[!UICONTROL Create Journey]** to create a new journey. 

1. Edit the journey's properties in the configuration pane displayed on the right side. Learn more in this [section](journey-gs.md#change-properties).

    ![](assets/jo-properties.png)

1. Start by drag and dropping an event or a **Read Segment** activity from the palette into the canvas. To learn more about journey design, refer to [this section](using-the-journey-designer.md).

    ![](assets/read-segment.png)

1. Drag and drop the next steps that the individual will follow. For example, you can add a condition followed by a channel action. To learn more about activities, refer to [this section](using-the-journey-designer.md).

1. Test your journey using test profiles. Learn more in this [section](testing-the-journey.md)

1. Publish your journey to activate it. Learn more in this [section](publishing-the-journey.md).

    ![](assets/jo-journeyuc2_32bis.png)

1. Monitor your journey using the dedicated reporting tools to measure your journey's effectiveness. Learn more in this [section](../reports/live-report.md).

    ![](assets/jo-dynamic_report_journey_12.png)

## Define your journey properties {#change-properties}

>[!CONTEXTUALHELP]
>id="ajo_journey_properties"
>title="Journey properties"
>abstract="This section shows the journey properties. By default, read-only parameters are hidden. Available settings depend on the status of the journey, on your permissions and product configuration."

Click on the pencil icon, in the top right to access the journey's properties.

You can change the name of the journey, add a description, allow re-entrance, choose start and end dates and, as an Admin user, define a **[!UICONTROL Timeout and error]** duration. If enabled for your organization, you can also activate [burst messaging](#burst).

For live journeys, this screen displays the publication date and the name of the user who published the journey.

The **Copy technical details** allows you to copy technical information about the journey which the support team can use to troubleshoot. The following information is copied: JourneyVersion UID, OrgID, orgName, sandboxName, lastDeployedBy, lastDeployedAt.

 ![](assets/journey32.png)

### Entrance{#entrance}

By default, new journeys allow re-entrance. You can uncheck the option for “one shot” journeys, for example if you want to offer a one-time gift when a person enters a shop. In that case, you don't want the customer to be able to re-enter the journey and receive the offer again.

When a journey "ends", it will have the status **[!UICONTROL Closed]**. The journey will stop letting new individuals enter the journey. Persons already in the journey will finish the journey normally.

After the default global timeout of 30 days, the journey will switch to the **Finished** status. See this [section](../building-journeys/journey-gs.md#global_timeout).

### Timeout and error in journey activities {#timeout_and_error}

When editing an action or condition activity, you can define an alternative path in case of error or timeout. If the processing of the activity interrogating a third-party system exceeds the timeout duration defined in the journey's properties (**[!UICONTROL Timeout and  error]** field), the second path will be chosen to perform a potential fallback action. 

Authorized values are between 1 and 30 seconds.

We recommend that you define a very short **[!UICONTROL Timeout and error]** value if your journey is time sensitive (example: reacting to the real-time location of a person) because you cannot delay your action for more than a few seconds. If your journey is less time sensitive, you can use a longer value to give more time to the system called to send a valid response.

Journeys also uses a global timeout. See the [next section](#global_timeout).

### Global journey timeout {#global_timeout}

In addition to the [timeout](#timeout_and_error) used in journey activities, there is also a global journey timeout which is not displayed in the interface and cannot be changed. This timeout will stop the progress of individuals in the journey 30 days after they enter. This means that an individual's journey cannot last longer than 30 days. After the 30 day timeout period, the individual's data is deleted. Individuals still flowing in the journey at the end of the timeout period will be stopped and they will be taken into account as errors in reporting.

>[!NOTE]
>
>Journeys do not directly react to privacy opt-out, access or delete requests. However, the global timeout ensures that individuals never stay more than 30 days in any journey.

Due to the 30-day journey timeout, when journey re-entrance is not allowed, we cannot make sure the re-entrance blocking will work more than 30 days. Indeed, as we remove all information about persons who entered the journey 30 days after they enter, we cannot know the person entered previously, more than 30 days ago.

### Timezone and profile timezone {#timezone}

Timezone is defined at journey level.

You can enter a fixed time zone or use Adobe Experience Platform profiles to define the journey time zone.

If a time zone is defined in Adobe Experience Platform profile, it can be retrieved in the journey.

For more information on timezone management, see [this page](../building-journeys/timezone-management.md).

### Burst mode {#burst}

Burst mode is a Journey Optimizer add-on that allows very fast push message sending in large volumes. It is used for simple journeys that include a **Read segment** activity and a simple push message. Burst is used when delay in message delivery is business-critical, when you want to send an urgent push alert on mobile phones, for example a breaking news to users who have installed your news channel app.

Burst messaging comes with the following requirements:

* The journey must start with a **Read segment** activity. Events are not allowed.
* The next step must be a push message. No other channel, activity or step is allowed.
* No personalization is allowed in the push message.
* The message must be small (<2KB).

>[!CAUTION]
>
>If any of the requirements is not fulfilled, burst mode will not be available in the journey.

To activate **Burst mode**, open your journey and click the pencil icon, in the top right to access the journey's properties. Then, activate the **Enable burst mode** toggle.

![](assets/burst.png)

Burst mode is automatically deactivated if you modify a burst journey and add an activity that is not compliant with burst messaging, such as an email message, any other action, an event etc.

![](assets/burst2.png)

Then test and publish your journey as usual. Note that, in test mode, messages are not sent via the burst mode.

Understand the applicable use cases for burst messaging, and how to configure a journey for burst messages, in this video:

>[!VIDEO](https://video.tv.adobe.com/v/334523?quality=12)
