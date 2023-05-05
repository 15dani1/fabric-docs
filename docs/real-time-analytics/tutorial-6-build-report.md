---
title: "Synapse Real-Time Analytics tutorial part 6: Build a Power BI report"
description: Part 6 of the Real-Time Analytics tutorial in Microsoft Fabric
ms.reviewer: tzgitlin
ms.author: yaschust
author: YaelSchuster
ms.topic: tutorial
ms.date: 05/23/2023
ms.search.form: product-kusto
---
# Real-Time Analytics tutorial part 6: Build a Power BI report

[!INCLUDE [preview-note](../includes/preview-note.md)]

> [!NOTE]
> This tutorial is part of a series. For the previous section, see: [Tutorial part 5: Use advanced KQL queries](tutorial-5-advanced-kql-query.md)

A Power BI report is a multi-perspective view into a dataset, with visuals that represent findings and insights from that dataset. In this section, you create a new query that joins both datasets, and use this query output to create a new Power BI report.

## Build Power BI report

1. Copy and paste the following query into your KQL queryset. The output of this query will be used as the dataset for building the Power BI report.

    ```kusto 
    nyctaxitrips
    | where PULocationID == DOLocationID
    | lookup (Locations) on $left.PULocationID==$right.LocationID
    | summarize Count=count() by Borough, Zone, Latitude, Longitude 
    ```

1.  Place your cursor somewhere within the query, and then select **Build Power BI report**.
    The Power BI report editor opens with query results available as a data source named *Kusto Query Result*.

1.  In the report editor, select **Visualizations** > **Map** icon. :::image type="icon" source="media/realtime-analytics-tutorial/map-icon.png" border="false":::
1. Drag the following fields from **Data** > **Kusto Query Result** to the **Visualizations** pane.

    * **Borough**  > **Legend**
    * **Latitude** > **Latitude**
    * **Longitude** > **Longitude**
    * **Count** > **Bubble size**

    :::image type="content" source="media/realtime-analytics-tutorial/create-power-bi-second-report.png" alt-text="Screenshot of creating second Power BI report in Synapse Real-Time Analytics in Microsoft Fabric." lightbox="media/realtime-analytics-tutorial/create-power-bi-second-report.png":::

## Add a visualization

1.  Select the **Stacked Bar Chart** icon. :::image type="icon" source="media/realtime-analytics-tutorial/stacked-bar-chart-icon.png" border="false":::
1. Drag the **Borough** field to Y-Axis and **Count** to the X-axis

    :::image type="content" source="media/realtime-analytics-tutorial/power-bi-second-visual.png" alt-text="Screenshot of adding second visualization to the Power BI report in Synapse Real-Time Analytics in Microsoft Fabric.":::

## Save the Power BI report

1.  In the top left corner of the ribbon, select **File** > **Save**.
1.  Enter the name *nyctaximapsreport*. Choose your workspace, and set sensitivity as *Public*.
1. Select **Continue**.
1. Select **Open the file in Power BI to view, edit, and get a shareable link**. 
    
    :::image type="content" source="media/realtime-analytics-tutorial/open-in-power-BI.png" alt-text="Screenshot of opening in Power BI in Real-Time Analytics in Microsoft Fabric.":::

## Change refresh settings

1. On the ribbon, select the **Edit** (pencil) button. :::image type="icon" source="media/realtime-analytics-tutorial/edit-pencil-icon.png" border="false":::
1. In the **Visualizations** pane, select the paintbrush icon to **Format page**.
1. Expand **Page Refresh**.

    :::image type="content" source="media/realtime-analytics-tutorial/page-refresh-on.png" alt-text="Screenshot of page refresh details in Real-Time Analytics in Microsoft Fabric.":::

1. Toggle **Page Refresh** to **On** and set the refresh interval to 10 seconds.

    > [!NOTE]
    >  The refresh interval can only be greater than or equal to the Admin interval.

1. Select the **Save** icon on the ribbon.

    The Power BI report now autorefreshes on streaming data arriving in a KQL database from an eventstream.

## Next steps

> [!div class="nextstepaction"]
> [Synapse Real-Time Analytics tutorial part 7: Clean up resources](tutorial-7-clean-up-resources.md)