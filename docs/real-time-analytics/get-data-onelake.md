---
title: Get data from OneLake in Real-Time Analytics
description: Learn how to get data from OneLake into a KQL database in Real-Time Analytics.
ms.reviewer: tzgitlin
ms.author: yaschust
author: YaelSchuster
ms.topic: how-to
ms.date: 05/23/2023
ms.search.form: product-kusto
---

# Get data from OneLake

In this article, you'll learn how to get data from OneLake into an existing KQL database.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

* A [workspace](../get-started/create-workspaces.md) with a Microsoft Fabric-enabled [capacity](../enterprise/licenses.md#capacity)
* [Lakehouse](../data-engineering/create-lakehouse.md)
* [KQL Database](create-database.md)

## Copy folder path from Lakehouse

1. In the experience switcher, choose **Data Engineering**.
1. Select the Lakehouse environment containing the data source you want to use.

1. Place your cursor over the desired file and select the **More** menu, then select **Properties**.
    :::image type="content" source="media/get-data-onelake/lakehouse-file-menu.png" alt-text="Screenshot of a Lakehouse file's dropdown menu. The option titled Properties is highlighted.":::

1. Under **URL**, select the **Copy to clipboard** icon and save it somewhere to retrieve in a later step.
    :::image type="content" source="media/get-data-onelake/lakehouse-file-properties.png" alt-text="Screenshot of a Lakehouse file's Properties pane. The copy icon to the right of the file's URL is highlighted.":::

1. Return to your workspace and select a KQL Database.

## Get data

1. Select **Get Data** > **OneLake**.

    :::image type="content" source="media/get-data-onelake/get-data-onelake.png" alt-text="Screenshot of Home ribbon showing the dropdown menu of Get data. The option titled Onelake is highlighted.":::

1. In **Table**, enter a name for your table.

     :::image type="content" source="media/get-data-onelake/onelake-table-name.png" alt-text="Screenshot of Destination window showing the database and table name in Real-Time Analytics. The table name field is highlighted.":::

      > [!TIP]
      > Table names can be up to 1024 characters including alphanumeric, hyphens, and underscores. Special characters aren't supported.

1. Select **Next: Source**.

### Source

1. In **Link to source**, paste the folder path of the Lakehouse you copied in [Copy folder path from Lakehouse](#copy-folder-path-from-lakehouse).

    > [!NOTE]
    >  The OneLake path you add will be the basis for the schema tab. You can add up to 10 items of up to 1-GB uncompressed size each. If you upload more than one item, you can change the schema-defining file by selecting the star icon on the right side of the source link field.

1. Select **Next: Schema** to view and edit your table column configuration.

### Schema

Your data format and compression are automatically identified in the left-hand pane. If incorrectly identified, use the **Data format** dropdown menu to select the correct format.

* If your data format is JSON, you must also select JSON levels, from 1 to 10. The levels determine the table column data division.
* If your data format is CSV, select the check box **Ignore the first record** to ignore the heading row of the file.

For more information on data formats, see [Data formats supported for ingestion](/azure/data-explorer/ingestion-supported-formats?context=/fabric/context/context&pivots=fabric).

1. The **Mapping name** field is automatically filled. Optionally, you can enter a new name. You can use alphanumeric characters and underscores. Spaces, special characters, and hyphens aren't supported.

    :::image type="content" source="media/get-data-onelake/onelake-schema.png" alt-text="Screenshot of Schema window showing the data configuration. ":::

    >[!NOTE]
    >
    > The tool automatically infers the schema based on your data. If you want to change the schema to add and edit columns, you can do so under [Partial data preview](#partial-data-preview).
    >
    > You can optionally use the [Command viewer](#command-viewer) to view and copy the automatic commands generated from your inputs.

1. Select **Next: Summary**. To skip to the summary pane explanation, select [Complete data ingestion](#complete-data-ingestion).

#### Command viewer

The command viewer shows the commands for creating tables, mapping, and ingesting data in tables.

To open the command viewer, select the **v** button on the right side of the command viewer. In the command viewer, you can view and copy the automatic commands generated from your inputs.

:::image type="content" source="media/get-data-onelake/onelake-command-viewer.png" alt-text="Screenshot of Command viewer pane showing mapping commands.":::

#### Partial data preview

The partial data preview is automatically inferred based on your data. You can change the data preview by editing existing columns and adding new columns.

1. To add a new column, select the **+** button on the right-hand column under **Partial data preview**.

    :::image type="content" source="media/get-data-onelake/onelake-partial-preview.png" alt-text="Screenshot of Partial data preview pane.":::

    * The column name should start with a letter, and may contain numbers, periods, hyphens, or underscores.
    * The default column type is `string` but can be altered in the drop-down menu of the Column type field.
    * Source: for table formats (CSV, TSV, etc.), each column can be linked to only one source column. For other formats (such as JSON, Parquet, etc.), multiple columns can use the same source.

1. Select **Next: Summary** to create a table and mapping and to begin data ingestion.

### Complete data ingestion

In the **Data ingestion completed** window, all three steps will be marked with green check marks when data ingestion finishes successfully.

:::image type="content" source="media/get-data-onelake/onelake-summary.png" alt-text="Screenshot of the Summary pane showing the successful completion of data ingestion.":::

## Next steps

* [Query data in the KQL Queryset](kusto-query-set.md)
* [Visualize data in a Power BI report](create-powerbi-report.md)
