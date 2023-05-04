---
title: Lakehouse tutorial - build a report
description: After ingesting data for the tutorial, and using notebooks to transform and prepare the data, you create a Power BI data model and create a report.
ms.reviewer: sngun
ms.author: arali
author: ms-arali
ms.topic: tutorial
ms.date: 5/23/2023
---

# Lakehouse tutorial: Building reports in Microsoft Fabric

In this section of the tutorial, you create a Power BI data model and create a report from scratch.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

* [Prepare and transform the data using notebooks and Spark runtime](tutorial-lakehouse-data-preparation.md)

## Build a report

Power BI is natively integrated in the whole Fabric experience. This native integration brings a unique mode, called DirectLake, of accessing the data from the lakehouse to provide the most performant query and reporting experience. DirectLake mode is a groundbreaking new engine capability to analyze very large datasets in Power BI. The technology is based on the idea of loading parquet-formatted files directly from a data lake without having to query a data warehouse or lakehouse endpoint, and without having to import or duplicate data into a Power BI dataset. DirectLake is a fast path to load the data from the data lake straight into the Power BI engine, ready for analysis.

In traditional DirectQuery mode, the Power BI engine queries the data directly from the data source every time it's queried and hence query performance depends on the speed data can be retrieved from the data source. This method avoids having to copy the data; any changes at the source are immediately reflected in the query results while in the import mode. And yet performance is better because the data is readily available in memory without having to query the data source each time. However, the Power BI engine must first copy the data into the dataset at refresh time. Any changes at the source are only picked up during the next data refresh.

DirectLake mode now eliminates this import requirement by loading the data files directly into memory. Because there's no explicit import process, it's possible to pick up any changes at the source as they occur, thus combining the advantages of DirectQuery and import mode while avoiding their disadvantages. DirectLake mode is therefore the ideal choice for analyzing very large datasets and datasets with frequent updates at the source.

1. Go the **wwilakehouse** lakehouse, select **SQL endpoint** under **Lake mode** on top right of the screen to open warehouse mode of the selected lakehouse.

   :::image type="content" source="media\tutorial-lakehouse-build-report\load-data-choose-sql-endpoint.png" alt-text="Screenshot showing where to find and select SQL endpoint under the Lake mode drop down.":::

1. Once you are in warehouse mode, you should be able to see all the tables you created. If you don't see them yet, select the **Refresh** icon at the top. Next, select the **Model** tab at the bottom to open the default Power BI dataset.

   :::image type="content" source="media\tutorial-lakehouse-build-report\warehouse-mode-refresh-model.png" alt-text="Screenshot showing where to select the Refresh icon and the Model tab." lightbox="media\tutorial-lakehouse-build-report\warehouse-mode-refresh-model.png":::

1. For this data model, you need to define the relationship between different tables so that you can create reports and visualizations based on data coming across different tables. From the **fact_sale** table, drag the **CityKey** field and drop it on the **CityKey** field in the **dimension_city** table to create a relationship. Check the “Assume referential integrity” and select ***Confirm*** to establish the relationship. **Note** - When defining relationships, make sure you have many to one relationship from the fact to the dimension and not vice versa.

   :::image type="content" source="media\tutorial-lakehouse-build-report\drag-drop-tables-relationships.png" alt-text="Screenshot showing drag and drop fields across tables to create relationships.":::

1. On the **Create Relationship** settings:
   1. Table 1 is populated with fact_sale and the column of CityKey.
   1. Table 2 is populated with dimension_city and the column of CityKey.
   1. Cardinality: **Many to one (\*:1)**
   1. Cross filter direction: **Single**
   1. Leave the box next to **Make this relationship active** checked.
   1. Check the box next to **Assume referential integrity.**
   1. Select **Confirm.**

      :::image type="content" source="media\tutorial-lakehouse-build-report\create-relationship-dialog.png" alt-text="Screenshot of the Create Relationship dialog box, showing where to select Assume referential integrity.":::

   1. Similarly, you need to add these relationships as well. After you add these relationships, your data model is ready for reporting as shown in the previous image:

      * StockItemKey(fact_sale) - StockItemKey(dimension_stock_item)
      * Salespersonkey(fact_sale) - EmployeeKey(dimension_employee)
      * CustomerKey(fact_sale) - CustomerKey(dimension_customer)
      * InvoiceDateKey(fact_sale) - Date(dimension_date)

        :::image type="content" source="media\tutorial-lakehouse-build-report\new-report-relationships.png" alt-text="Screenshot of a New report screen showing multiple table relationships." lightbox="media\tutorial-lakehouse-build-report\new-report-relationships.png":::

1. Select **New report** to start creating reports/dashboards in Power BI. On the Power BI report canvas, you can create reports to meet your business requirements by dragging required columns from the **Data** pane to the canvas and using one or more of available visualizations.

   :::image type="content" source="media\tutorial-lakehouse-build-report\report-canvas-drag-columns.png" alt-text="Screenshot of the Power BI report canvas, showing where to select columns in the Data pane." lightbox="media\tutorial-lakehouse-build-report\report-canvas-drag-columns.png":::

1. Add a title:
   1. In the Ribbon, select the Text Box icon.
   1. Type in **WW Importers Profit Reporting**.
   1. Highlight the text and increase size to 20 and place in the upper left of the report page.

1. Add a Card:
   1. On the **Data** pane, expand **fact_sales** and check the box next to **Profit**. This selection creates a column chart and adds the field to the Y-axis.
   1. With the bar chart selected, select the Card visual in the visualization pane. This selection converts the visual to a card.
   1. Place the card under the title.

      :::image type="content" source="media\tutorial-lakehouse-build-report\card-visualization.png" alt-text="Screenshot showing a visual converted to a card." lightbox="media\tutorial-lakehouse-build-report\card-visualization.png":::

1. Add a Bar chart:
   1. On the **Data** pane, expand **fact_sales** and check the box next to **Profit**. This selection creates a column chart and adds the field to the Y-axis.
   1. On the **Data** pane, expand **dimension_city** and check the box for **SalesTerritory**. This selection adds the field to the Y-axis.
   1. With the bar chart selected, select the Clustered Bar Chart visual in the visualization pane. This selection converts the column chart into a bar chart.

      :::image type="content" source="media\tutorial-lakehouse-build-report\build-visual-bar-chart.png" alt-text="Screenshot of the Build visual screen, showing where to select the Clustered bar chart icon.":::

   1. Resize the Bar chart to fill in the area under the title and Card.

      :::image type="content" source="media\tutorial-lakehouse-build-report\resize-bar-chart-under-card.png" alt-text="Screenshot of a resized bar chart positioned below a card." lightbox="media\tutorial-lakehouse-build-report\resize-bar-chart-under-card.png":::

1. Click anywhere on the blank canvas (or press the Esc key) so the bar chart visual is no longer selected.

1. Build a stacked area chart visual:
   1. On the **Visualizations** pane, select the **Stacked** **area** **chart** visual.

      :::image type="content" source="media\tutorial-lakehouse-build-report\stacked-area-chart.png" alt-text="Screenshot of the visualizations pane, showing where to select Stacked area chart.":::

   1. Reposition and resize the stacked area chart to the right of the card and bar chart visuals created in the previous steps.

   1. On the **Data** pane, expand **fact_sales** and check the box next to **Profit.** Expand dimension_date and check the box next to **FiscalMonthNumber**. This selection creates a filled line chart showing profit by fiscal month.

   1. On the **Data** pane, expand **dimension_stock_item** and drag **BuyingPackage** into the Legend field well. This selection adds a line for each of the Buying Packages.

      :::image type="content" source="media\tutorial-lakehouse-build-report\data-pane-change-chart.png" alt-text="Screenshot of the data pane showing how to add lines to the chart." lightbox="media\tutorial-lakehouse-build-report\data-pane-change-chart.png":::

1. Click anywhere on the blank canvas (or press the Esc key) so the stacked area chart visual is no longer selected.

1. Build a column chart:
   1. On the **Visualizations** pane, select the **Stacked column chart** visual.

      :::image type="content" source="media\tutorial-lakehouse-build-report\select-stacked-column-chart.png" alt-text="Screenshot showing where to select Stacked column chart.":::

   1. On the **Data** pane, expand **fact_sales** and check the box next to **Profit**. This selection adds the field to the Y-axis.
   1. On the **Data** pane, expand **dimension_employee** and check the box next to **Employee**. This selection adds the field to the X-axis.

      :::image type="content" source="media\tutorial-lakehouse-build-report\add-field-x-axis.png" alt-text="Screenshot showing how to add a field to the x axis." lightbox="media\tutorial-lakehouse-build-report\add-field-x-axis.png":::

1. Click anywhere on the blank canvas (or press the Esc key) so the LINE chart visual is no longer selected.
1. From the ribbon, select **File > Save**.
1. Enter the name of your report as **Profit Reporting**.
1. Select **Save**.

   :::image type="content" source="media\tutorial-lakehouse-build-report\save-your-report.png" alt-text="Screenshot showing the Save your report dialog.":::

## Next steps

Advance to the next article to learn how to
> [!div class="nextstepaction"]
> [Clean up resources](tutorial-lakehouse-clean-up.md)
