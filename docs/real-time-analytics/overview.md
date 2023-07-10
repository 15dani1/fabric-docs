---
title: Overview of Real-Time Analytics in Microsoft Fabric
description: Learn about Real-Time Analytics in Microsoft Fabric.
ms.reviewer: tzgitlin
ms.author: yaschust
author: YaelSchuster
ms.topic: conceptual
ms.custom: build-2023, build-2023-dataai, build-2023-fabric
ms.date: 07/10/2023
ms.search.form: product-kusto
---
# What is Real-Time Analytics in Fabric?

[!INCLUDE [preview-note](../includes/preview-note.md)]

The last few decades have seen a paradigm shift in the way we access and consume information, as users have become used to data that is interactive, on demand, and accessible to all. This shift has been powered by big data, streaming data ingestion, and indexed, keyword-based search. All together they form a simplified user experience. With Real-Time Analytics in Microsoft Fabric, we enable organizations to focus and scale up their analytics solution while democratizing data for the needs of both the citizen data scientist all the way to the advanced data engineer. Real-time analytics have become essential in many scenarios in the enterprise world, such as cybersecurity, asset tracking and management, predictive maintenance, supply chain optimization, customer experience, energy management, inventory management, quality control, environmental monitoring, fleet management, and health and safety.

How? Real-Time Analytics reduces complexity and simplifies data integration. Quick access to data insights is achieved through automatic data streaming, automatic indexing and data partitioning of any data source or format, and by using the on-demand query generation and visualizations. This user process is simplified while preserving powerful analytical capabilities. Real-Time Analytics lets you focus on your analytics solutions by scaling up seamlessly with the service as your data and query needs grow.

:::image type="content" source="media/real-time-analytics-overview/product-view.png" alt-text="Screenshot of Real-Time Analytics product showing the database homepage with a quick query pane showing binned ingestion results." lightbox="media/real-time-analytics-overview/product-view.png":::

Real-Time Analytics is a fully managed big data analytics platform optimized for streaming, and time-series data. It utilizes a query language and engine with exceptional performance for searching structured, semi-structured, and unstructured data. Real-Time Analytics is fully integrated with the entire suite of Fabric products, for both data loading, data transformation, and advanced visualization scenarios.

## What makes Real-Time Analytics unique?

* **Capture, transform, and route** real-time events to various destinations, including custom apps.
* **Easily ingest or load** data from any source, in any data format.
* Run analytical queries **directly on raw data** without the need to build complex data models or create scripting to transform the data.
* Import data with **by-default streaming** that provides high performance, low latency, high freshness data analysis.
* Imported data undergoes **default partitioning** - both time and hash-based partitioning, and by-default **indexing**.
* Work with **versatile data structures** including query structured, semi-structured, or free text.
* **Query** raw data without transformation, with high performance, incredibly low response time, while using a wide variety of available [operators](/azure/data-explorer/kusto/query/index?context=/fabric/context/context).
* **Scale to an unlimited** amount of data, from gigabytes to petabytes, with unlimited scale on concurrent queries and concurrent users.
* **Integrate** seamlessly with other experiences and items in Microsoft Fabric.

## When to use Real-Time Analytics?

If any one of these questions describes your data needs, Real-Time Analytics is the right solution for you:

> [!div class="checklist"]
>
> * Do I need high freshness from data ingestion to query?
> * Do I want to transform streaming data?
> * Do I have a service that needs to access data with low query latency (in a matter of seconds)?
> * Does I need to search or access data in different formats, like structured data, semi-structured data (including complicated data such as JSON or other arrays), or unstructured data (for example, free text)?
> * Do I want the ability to query large amounts of data?
> * Does my data have a time component that can benefit from the time series-optimized database structure?
> * Do I want the ability to create ad-hoc queries on any field or row without prior optimization?

The types of industries that benefit from data analysis in Real-Time Analytics is varied. For example: finance, transportation and logistics, smart cities, smart buildings, manufacturing operations, automotive, and oil and gas.

## How to work in Real-Time Analytics?

The main items available in Real-Time Analytics include:

* [Eventstream](event-streams/overview.md) for capturing, transforming, and routing real-time events to various destinations with a no-code experience. 
* A [KQL database](create-database.md) for data storage and management. Data loaded into a KQL database can be accessed in OneLake and is exposed to other Fabric experiences.
* A [KQL queryset](kusto-query-set.md) to run queries, view, and customize query results on data. The KQL queryset allows you to save queries for future use, export and share queries with others, and includes the option to generate a Power BI report.

See how these items work together in the end-to-end streaming data consumption and analysis scenario: [Real-Time Analytics Tutorial- Introduction](tutorial-introduction.md)

## Integration with other experiences

:::image type="content" source="media/real-time-analytics-overview/schematic-architecture.png" alt-text="Schematic image of architecture of Real-Time Analytics integration with other experiences.":::

* Create [Event Hubs cloud connections](get-data-event-hub.md) to stream data into Real-Time Analytics.
* Data in OneLake is accessed by Real-Time Analytics in several ways:
  * Data from OneLake can be [queried from Real-Time Analytics as a shortcut](onelake-shortcuts.md?tab=onelake-shortcut).
  * Data from [OneLake can be loaded](get-data-onelake.md) into Real-Time Analytics.
  * Data loaded into Real-Time Analytics is reflected in OneLake as [one logical copy](onelake-mirroring.md).
* Data loaded into Real-Time Analytics can be used as the underlying data for [visualization in a Power BI report](create-powerbi-report.md).
* Data loaded into Real-Time Analytics can be used for analysis in [Jupyter](jupyter-notebook.md) or [Spark](spark-connector.md) Notebooks in Data Engineering.
* Trigger data loading events in Data Factory using [pipelines](../data-factory/connector-overview.md#supported-data-stores-in-data-pipeline).
* Trigger data loading events using [Dataflows](../data-factory/connector-overview.md#supported-data-connectors-in-dataflows).

## See also

* [Microsoft Fabric event streams - overview](event-streams/overview.md)
* [Compare Real-Time Analytics to Azure Data Explorer](realtime-analytics-compare.md)
* [Tutorial: Real-Time Analytics](tutorial-introduction.md)
* [Query data in a KQL queryset](kusto-query-set.md)
* [Kusto Query Language overview](/azure/data-explorer/kusto/query/index?context=/fabric/context/context)
