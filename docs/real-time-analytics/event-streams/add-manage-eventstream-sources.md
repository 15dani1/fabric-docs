---
title: Add and manage eventstream sources
description: This article describes how to add and manage an event source in an Eventstream item with Microsoft Fabric event streams feature.
ms.reviewer: spelluru
ms.author: xujiang1
author: xujxu
ms.topic: how-to
ms.custom: build-2023
ms.date: 05/23/2023
ms.search.form: product-kusto
---

# Add and manage an event source in an eventstream

Once you have created an eventstream, you can connect it to various data sources and destinations. The types of event sources that you can add to your eventstream include Azure Event Hubs, Sample data and Custom app. See the [Supported event sources](#supported-event-sources) section for details about these event sources. 

[!INCLUDE [preview-note](../../includes/preview-note.md)]

## Prerequisites

To get started, you must complete the following prerequisites:

- Get access to a **premium workspace** with **Contributor** or above permissions where your eventstream is located in.
- For Azure Event Hubs source, an Azure event hub with event data and appropriate permission available to access its policy keys.

## Add an Azure event hub as a source

If you have an Azure event hub created with event data there, follow these steps to add an Azure event hub as your eventstream source:  

1. Select **New source** on the ribbon or "**+**" in the main editor canvas and then **Azure Event Hubs**.

2. Enter a source name for the new source and select a cloud connection to your Azure event hub.

   :::image type="content" source="./media/event-streams-source/eventstream-sources-event-hub.png" alt-text="Screenshot showing the Azure Event Hubs source configuration." lightbox="./media/event-streams-source/eventstream-sources-event-hub.png" :::

3. If you don’t have a cloud connection, select **Create new connection** to create one. To create a new connection, fill in the information of your Azure event hub on the **New connection** page.

   :::image type="content" source="./media/add-manage-eventstream-sources/eventstream-eventhub-source-cloud-connection.png" alt-text="Screenshot showing the cloud connection in event hub source." lightbox="./media/add-manage-eventstream-sources/eventstream-eventhub-source-cloud-connection.png" :::

   - **Connection name**: Enter a name for the cloud connection. 
   - **Connection type**: Default value is `EventHub`. 
   - **Event Hub namespace**: Enter the name of your Azure event hub namespace. 
   - **Authentication username and password**: Go to your Azure event hub and create a policy under **Share access policies**. Then use **policy name** and **primary key** as the username and password. 
   
       :::image type="content" source="./media/add-manage-eventstream-sources/azure-event-hub-policy-key.png" alt-text="Screenshot showing the Azure event hub policy key." lightbox="./media/add-manage-eventstream-sources/azure-event-hub-policy-key.png" :::
   
   - **Privacy level**: choose a privacy level for the cloud connection.

4. After you create a cloud connection, hit the refresh button, and select the cloud connection you created.

   :::image type="content" source="./media/add-manage-eventstream-sources/cloud-connection-refresh.png" alt-text="Screenshot showing the cloud connection refresh." lightbox="./media/add-manage-eventstream-sources/cloud-connection-refresh.png" :::

5. Select a **Data format** of the incoming real-time events that you want to get from your Azure event hub.

   > [!NOTE]
   > The event streams feature supports the ingestion of events from Azure Event Hubs in JSON, Avro, and CSV (with header) data formats.

6. Select a **Consumer group** that is used for reading the event data from your Azure event hub and then **Create**. 

    After the event hub source is created, you see an event hub source added to your eventstream on the canvas.

    :::image type="content" source="./media/add-manage-eventstream-sources/event-hub-source-completed.png" alt-text="Screenshot showing the event hub source." lightbox="./media/add-manage-eventstream-sources/event-hub-source-completed.png" :::

## Add a sample data as a source

To get a better understanding of how an eventstream works, you can use the out-of-box sample data provided and send data to the eventstream. Follow these steps to add a sample data source: 

1. Select **New source** on the ribbon or "**+**" in the main editor canvas and then Sample data. 

2. On the right pane, enter a source name to be displayed on the canvas, select the desired sample data to be added to your eventstream and then Create. 
   - **Yellow Taxi**: sample taxi data with a preset schema that includes fields such as pickup time, drop-off time, distance, total fee, and more. 
   - **Stock Market**: sample data of a stock exchange with a preset schema column such as time, symbol, price, volume and more.
   
       :::image type="content" source="./media/event-streams-source/eventstream-sources-sample-data.png" alt-text="Screenshot showing the sample data source configuration." lightbox="./media/event-streams-source/eventstream-sources-sample-data.png" :::

3. When the sample data source is created successfully, you can find it on the canvas and navigation pane.

    To verify if the sample data is added successfully, select Data preview in the bottom pane.

    :::image type="content" source="./media/add-manage-eventstream-sources/sample-data-source-completed.png" alt-text="Screenshot showing the sample data source." lightbox="./media/add-manage-eventstream-sources/sample-data-source-completed.png" :::


## Add custom application as a source

If you want to connect your own application with an eventstream, you can add it as a custom app source. Then, send data to the eventstream with your own application with the connection endpoint exposed in the custom app. Follow these steps to add a custom app source:  

1. Select **New source** on the ribbon or "**+**" in the main editor canvas and then Custom App. 

2. Enter a **Source name** for the custom app and select Create. 

   :::image type="content" source="./media/event-streams-source/eventstream-sources-custom-app.png" alt-text="Screenshot showing the custom app source configuration." lightbox="./media/event-streams-source/eventstream-sources-custom-app.png" :::

3. Once the custom app is created successfully, you can view the information of the custom app such as **connection string** on the bottom pane. 

   The connection string is an **event hub compatible connection string** and you can use it in your application to send events to your eventstream.

   :::image type="content" source="./media/add-manage-eventstream-sources/custom-app-source-completed.png" alt-text="Screenshot showing the custom app source." lightbox="./media/add-manage-eventstream-sources/custom-app-source-completed.png" :::

## Manage source

- **Edit/remove**: You can select an eventstream source to edit or remove either through the navigation pane or canvas. When you select **Edit**, the edit pane opens in the right of the main editor. 

   :::image type="content" source="./media/add-manage-eventstream-sources/source-modification-deletion.png" alt-text="Screenshot showing the source modification and deletion." lightbox="./media/add-manage-eventstream-sources/source-modification-deletion.png" :::

- **Regenerate key for a custom app**: If you want to regenerate a new connection key for your application, select one of your custom app sources on the canvas and select **Regenerate** to get a new connection key.

   :::image type="content" source="./media/add-manage-eventstream-sources/regenerate-key-in-custom-app.png" alt-text="Screenshot showing how to regenerate a key." lightbox="./media/add-manage-eventstream-sources/regenerate-key-in-custom-app.png" :::

## Supported event sources

By utilizing the eventstream sources, users can seamlessly incorporate their real-time events into Microsoft Fabric, facilitating efficient and effective data ingestion.

:::image type="content" source="./media/event-streams-source/eventstream-sources.png" alt-text="Screenshot showing the overview of the event streams source types." lightbox="./media/event-streams-source/eventstream-sources.png" :::

> [!NOTE]
> - The total count of sources and destinations for one eventstream is **11**.
> - Event data retention in eventstream is **1 day**, with the option to extend it up to 7 days in the future.

The following sources are currently available.

### Azure Event Hubs

If you already have an Azure event hub set up in Azure, you can utilize that event hub to ingest real-time data into Microsoft Fabric via event streams feature.

- **Source name** - Meaningful source name that appears in your eventstream. 
- **Cloud connection** - A cloud connection needs to be established between existing event hub to Microsoft Fabric. Once that cloud connection is in place, it can be reused across multiple Eventstream items. To create a new cloud connection, you must provide the **event hub namespace name**, **event hub name**, **shared access policy name** and **primary key**.  
- **Data format** - Format of the incoming real-time events that you want to get from your Azure event hub.
- **Consumer group** - The consumer group of your event hub that is used for reading the event data from your Azure event hub.

    :::image type="content" source="./media/event-streams-source/eventstream-sources-event-hub.png" alt-text="Screenshot showing the Azure Event Hubs source configuration." lightbox="./media/event-streams-source/eventstream-sources-event-hub.png" :::

### Sample data

By utilizing the sample data source (**Yellow Taxi** or **Stock Market events**), you can effortlessly test your configuration without the need for writing any code, as the sample data is pushed directly into your eventstream.

- **Source name** – Meaningful source name that appears in your eventstream. 
- **Sample data** – Select either the Yellow Taxi or Stock Market sample data.
 
    :::image type="content" source="./media/event-streams-source/eventstream-sources-sample-data.png" alt-text="Screenshot showing the sample data source configuration." lightbox="./media/event-streams-source/eventstream-sources-sample-data.png" :::

### Custom application

Custom application enables a streaming endpoint where you can point your existing event hubs or Kafka clients to your eventstream in Microsoft Fabric without needing any code changes. 

- **Source name** – Meaningful source name that appears in your eventstream.

    :::image type="content" source="./media/event-streams-source/eventstream-sources-custom-app.png" alt-text="Screenshot showing the custom app source configuration." lightbox="./media/event-streams-source/eventstream-sources-custom-app.png" :::


## Next steps

- [Create and manage an eventstream](./create-manage-an-eventstream.md)
- [Add and manage a destination in an eventstream](./add-manage-eventstream-destinations.md)
