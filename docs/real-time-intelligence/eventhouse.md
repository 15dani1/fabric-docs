---
title: Event house overview
description: Learn about event house data storage in Real-Time Intelligence.
ms.reviewer: sharmaanshul
ms.author: yaschust
author: YaelSchuster
ms.topic: Conceptual
ms.date: 05/23/2024
ms.search.form: Eventhouse
---
# Event house overview

Event houses provide a solution for handling and analyzing large volumes of data, particularly in scenarios requiring real-time analytics and exploration. They're designed to handle real-time data streams efficiently, which lets organizations ingest, process, and analyze data in near real-time. These aspects make event houses particularly useful for scenarios where timely insights are crucial. Event houses provide a scalable infrastructure that allows organizations to handle growing volumes of data, ensuring optimal performance and resource use. Event houses are the preferred engine for semistructured and free text analysis . An event house is a workspace of databases, which might be shared across a certain project. It allows you to manage multiple databases at once, sharing capacity and resources to optimize performance and cost. Event houses provide unified monitoring and management across all databases and per database.

Event houses are specifically tailored to time-based, streaming events with structured, semistructured, and unstructured data. You can get data from multiple sources, in multiple pipelines (For example, Eventstream, SDKs, Kafka, Logstash, data flows, and more) and multiple data formats. This data is automatically indexed and partitioned based on ingestion time.

## When do I create an event house?

Use an event house for any scenario that includes event-based data, for example, telemetry and log data, time series and IoT data, security and compliance logs, or financial records.

## What information do I see in an event house?

The system overview page of an event house shows you the following information:

* Event house details
* Running state of the event house
* OneLake storage usage
* OneLake storage usage by database
* Compute usage
* Compute usage by user
* Most active databases
* Recent events

For more information, see [View system overview details for an event house](manage-monitor-eventhouse.md#view-system-overview-details-for-an-event-house).

The databases page of an event house shows you database information either in list or tile view. The following information about each database is displayed in tile view:

* Database name
* A graph of queries run over the past week
* Data size
* Caching policy
* Retention policy
* Last ingestion date

## Minimum consumption

Your event house is designed to optimize cost by suspending the service when not in use. To reactivate the service, you might encounter a latency of a few seconds. If you have highly time-sensitive systems that can't tolerate this latency, use **Minimum consumption**. When activated, the service is always available at the selected minimum level, and you pay at least the minimum compute selected (or actual use) while no longer paying for premium storage. The specified compute is available to all the databases within the Eventhouse. The free premium storage allotted to the customer is limited, and corresponds to the minimum consumption levels as shown in the following table:

[!INCLUDE [capacity-eventhouse](includes/capacity-eventhouse.md)]

For instructions on how to enable minimum consumption, see [Enable minimum consumption](manage-monitor-eventhouse.md#enable-minimum-consumption).

## Next step

> [!div class="nextstepaction"]
> [Create an event house](create-eventhouse.md)
