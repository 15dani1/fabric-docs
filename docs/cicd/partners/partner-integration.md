---
title: Microsoft Fabric ISV Partner integration with Fabric
description:  Fabric ISV Partner Ecosystem enables ISVs to use a streamlined solution that’s easy to connect, onboard, and operate. 
ms.reviewer: richin
ms.author: monaberdugo
author: mberdugo
ms.topic: overview
ms.custom: 
ms.search.form: 
ms.date: 10/30/2023
---

# Microsoft Fabric Integration Pathways for ISVs

[Microsoft Fabric](https://www.microsoft.com/microsoft-fabric/blog/) offers three distinct pathways for ISVs to seamlessly integrate with Fabric. For an ISV starting on this journey, we want to walk through various resources we have available under each of these pathways.

:::image type="content" source="media/partner-integration/integrate-fabric.png" alt-text="Figure showing the three pathways to integrate with Fabric: Interop, Develop Apps, and Build a Fabric workload.":::

## Interop with Fabric

The primary focus with Interop model is on enabling ISVs to integrate their solutions with the [OneLake Foundation](../../get-started/microsoft-fabric-overview.md). To Interop with Microsoft Fabric, we provide integration using REST APIs for OneLake, a multitude of connectors in Data Factory, shortcuts in OneLake, and database mirroring.

:::image type="content" source="media/partner-integration/onelake-interop.png" alt-text="Figure showing four ways to interop with OneLake: APIs, Fabric Data Factory, Multicloud shortcuts, and database mirroring.":::

Here are a few ways to get you started with this model:

### OneLake APIs

- OneLake supports existing Azure Data Lake Storage (ADLS) Gen2 APIs and SDKs for direct interaction, allowing developers to read, write, and manage their data in OneLake. Learn more about [ADLS Gen2 REST APIs](/rest/api/storageservices) and [how to connect to OneLake](../../onelake/onelake-access-api.md).
- Since not all functionality in ADLS Gen2 maps directly to OneLake, OneLake also enforces a set folder structure to support Fabric workspaces and items. For a full list of different behaviors between OneLake and ADLS Gen2 when calling these APIs, see [OneLake API parity](../../onelake/onelake-api-parity.md).
- If you're using Databricks and want to connect to Microsoft Fabric, Databricks works with ADLS Gen2 APIs. [Integrate OneLake with Azure Databricks](../../onelake/onelake-azure-databricks.md).
- To take full advantage of what the Delta Lake storage format can do for you, review and understand the format, table optimization, and V-Order. [Delta Lake table optimization and V-Order](../../data-engineering/delta-optimization-and-v-order.md).
- Once the data is OneLake, explore locally using [OneLake File Explorer](../../onelake/onelake-file-explorer.md). OneLake file explorer seamlessly integrates OneLake with Windows File Explorer. This application automatically syncs all OneLake items that you have access to in Windows File Explorer. You can also use any other tool compatible with ADLS Gen2 like [Azure Storage Explorer](/products/storage/storage-explorer).

:::image type="content" source="media/partner-integration/onelake-apis.png" alt-text="Diagram showing how OneLake APIs interact with Fabric workloads.":::

### Data Factory in Fabric

1. Data Pipelines boast an **extensive set of connectors**, enabling ISVs to effortlessly connect to a myriad of data stores. Whether you're interfacing traditional databases or modern cloud-based solutions, our connectors ensure a smooth integration process. [Connector overview](../../data-factory/connector-overview.md).
1. With our supported Dataflow Gen2 connectors, ISVs can harness the power of Fabric Data Factory to manage complex data workflows. This feature is especially beneficial for ISVs looking to streamline data processing and transformation tasks. [Dataflow Gen2 connectors in Microsoft Fabric](../../data-factory/dataflow-support.md).
1. For a full list of capabilities supported by Data Factory in Fabric checkout this [Data Factory in Fabric Blog](https://blog.fabric.microsoft.com/blog/introducing-data-factory-in-microsoft-fabric?ft=All).

:::image type="content" source="media/partner-integration/fabric-data-factory.png" alt-text="Screenshot of the Fabric Data Factory interface.":::

### Multicloud Shortcuts

Shortcuts in Microsoft OneLake allow you to unify your data across domains, clouds, and accounts by creating a single virtual data lake for your entire enterprise. All Fabric experiences and analytical engines can directly point to your existing data sources such as OneLake in different tenant, [Azure Data Lake Storage (ADLS) Gen2](../../onelake/create-adls-shortcut.md), [Amazon S3 storage accounts](../../onelake/create-s3-shortcut.md), and [Dataverse](/power-apps/maker/data-platform/azure-synapse-link-view-in-fabric) through a unified namespace. OneLake presents ISVs with a transformative data access solution, seamlessly bridging integration across diverse domains and cloud platforms.

- [Learn more about OneLake shortcuts](../../onelake/onelake-shortcuts.md)
- [Learn more about OneLake, one copy](../../real-time-analytics/onelake-mirroring.md)

:::image type="content" source="media/partner-integration/multicloud-shortcuts.png" alt-text="Diagram showing multicloud shortcuts in OneLake.":::

### Database Mirroring

You’ve seen the shortcuts, now you’re wondering about integration capabilities with external databases and warehouses. Mirroring provides a modern way of accessing and ingesting data continuously and seamlessly from any database or data warehouse into the Data warehousing experience in Microsoft Fabric. Mirror is all in near real-time thus giving users immediate access to changes in the source. You can learn more about mirroring and the supported databases here (Link to Priya’s blog).

:::image type="content" source="media/partner-integration/database-mirroring.png" alt-text="Diagram of database mirroring.":::

## Develop on Fabric

:::image type="content" source="media/partner-integration/develop-on-fabric.png" alt-text="Diagram showing how to build apps on Fabric.":::

With the **Develop on Fabric model** ISVs can build their products and services on top of Fabric or seamlessly embed Fabric's functionalities within their existing applications. It's a transition from basic integration to actively applying the capabilities Fabric offers. The main integration surface area is via REST APIs for various Fabric workloads. Here's a list of REST APIs available today.

| Fabric Experience   | API                                                   | Description                                                                                                                 |
|---------------------|-------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------|
| Data Warehouse      |                                                       |                                                                                                                             |
|                     | Create Warehouse                                      | Creates a Data warehouse                                                                                                    |
|                     | Get Warehouse                                         | Get Metadata about warehouse                                                                                                |
|                     | Update Warehouse                                      | Update an existing warehouse                                                                                                |
|                     | Delete Warehouse                                      | Delete an existing warehouse                                                                                                |
|                     | List Warehouse                                        | List warehouses in your workspace                                                                                           |
| [Data Engineering](../../data-engineering/lakehouse-api.md)    |            |                                                                                                                             |
|                     | Create Lakehouse                                      | Creates Lakehouse along with SQL analytics Endpoint.                                                                        |
|                     | Update Lakehouse                                      | Updates the name of a lakehouse and the SQL analytics endpoint.                                                             |
|                     | Delete Lakehouse                                      | Deletes lakehouse and the associated SQL analytics endpoint.                                                                |
|                     | Get Properties                                        |                                                                                                                             |
|                     | List tables in Lakehouse                              |                                                                                                                             |
|                     | Table Load                                            | Creates delta tables from CSV and parquet files and folders.                                                                |
| OneLake             |                                                       |                                                                                                                             |
|                     | [Create Shortcut](/rest/api/fabric/core/onelake-shortcuts/create-shortcut)   | Creates a new shortcut.                                                                                                     |
|                     | [Delete Shortcut](/rest/api/fabric/core/onelake-shortcuts/delete-shortcut)   | Deletes the shortcut but doesn't delete destination storage folder.                                                        |
|                     | [Get Shortcut](/rest/api/fabric/core/onelake-shortcuts/get-shortcut)                                          | Returns shortcut Properties.                                                                                                |
|                     | [ADLS Gen2 APIs](/rest/api/storageservices/data-lake-storage-gen2)           | ADLS Gen2 APIs to create and manage file systems, directories, and path.                                                    |
| Workspace           |                                                       |                                                                                                                             |
|                     | [CRUD APIs for Workspace and Workspace Role Management](/rest/api/fabric/core/workspaces) | create Workspace, get Workspace details, Delete Workspace, assign workspace to a capacity, add a workspace role assignment. |
| Fabric Data Factory | Coming soon                                           |                                                                                                                             |
| Real Time Analytics | Coming Soon                                           |                                                                                                                             |

This section will be updated as more Fabric APIs become available.

## Build a Fabric Workload

:::image type="content" source="media/partner-integration/create-fabric-workload.png" alt-text="Diagram describing the process of creating a Fabric workload.":::

Build a Fabric Workload model is designed to equip ISVs with the tools and platform capabilities required to craft customized workloads and experiences on Fabric. It enables ISVs to tailor their offerings to deliver their value proposition while leveraging the Fabric ecosystem by combining the best of both the worlds.
We're working closely with select design partners for this integration path and it's currently available by invitation only.
