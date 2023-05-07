---
title:  Visualize data in a Power BI report in Real-time Analytics
description: Learn how to visualize data from a KQL Queryset in a Power BI report.
ms.reviewer: tzgitlin
ms.author: yaschust
author: YaelSchuster
ms.topic: how-to
ms.date: 05/23/2023
ms.search.form: product-kusto
---

# Visualize data in a Power BI report

[!INCLUDE [preview-note](../includes/preview-note.md)]

In this article, you learn how to build a Power BI report using a KQL Queryset. The output of your query is used as the dataset of your report.

To use multiple tables to build your Power BI report, see [Use data from KQL Databases in Power BI Desktop](power-bi-data-connector.md).

## Prerequisites

* A [workspace](../get-started/create-workspaces.md) with a Microsoft Fabric-enabled [capacity](../enterprise/licenses.md#capacity)
* [KQL Database](create-database.md)
* [KQL Queryset](kusto-query-set.md).

## Create a report

1. Navigate to your KQL Queryset.
1. Write and select the query you want to build into a Power BI report. The output of this query is used as the dataset for building the report.
1. On the ribbon, select **Build Power BI report**.

    :::image type="content" source="media/create-powerbi-report/build-report.png" alt-text="Screenshot of query editor showing an example query. The Build Power BI report option on the ribbon is highlighted." lightbox="media/create-powerbi-report/build-report.png":::

    >[!NOTE]
    > When you build a report, a dataset is created and saved in your workspace. You can create multiple reports from a single dataset.
    >
    > If you delete the dataset, your reports will also be removed.

### Report preview

You can manipulate the visualizations in the report's preview. In the **Data** pane, expand **Kusto Query Result** to see a summary of your query. For more information, see [Power BI visualizations](/power-bi/visuals/power-bi-report-visualizations).

When you're satisfied with the visualizations, select **File** on the ribbon, and then **Save this report** to name and save your report in a workspace.

:::image type="content" source="media/create-powerbi-report/report-preview.png" alt-text="Screenshot of Power BI report preview window showing a preview of the dataset visualization. The Save button is highlighted." lightbox="media/create-powerbi-report/report-preview.png":::

### Report details

1. In **Name your file in Power BI**, give your file a name.
1. Select the workspace in which to save this report. The report can be a different workspace than the one you started in.

    :::image type="content" source="media/create-powerbi-report/report-details.png" alt-text="Screenshot of report details showing the report's name and the workspace it's saved in. The button titled Continue is highlighted." lightbox="media/create-powerbi-report/report-details.png":::

1. Select the sensitivity label to apply to the report. For more information, see [sensitivity labels](/power-bi/enterprise/service-security-apply-data-sensitivity-labels).
1. Select **Continue**.

### Manage report

To view and edit your report, select **Open the file in Power BI to view, edit, and get a shareable link**.

:::image type="content" source="media/create-powerbi-report/open-report.png" alt-text="Screenshort of report preview showing that the report has been saved. The link to open the report in Power BI is highlighted." lightbox="media/create-powerbi-report/open-report.png":::

## Next steps

[Visualizations in Power BI reports](/power-bi/visuals/power-bi-report-visualizations)
