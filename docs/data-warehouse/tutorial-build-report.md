---
title: Data warehouse tutorial - build a report from the OneLake data hub
description: In this tutorial step, learn how to build a report from the OneLake data hub with the data you ingested into your warehouse in the last step.
ms.reviewer: wiassaf
ms.author: scbradl
author: bradleyschacht
ms.topic: tutorial
ms.date: 5/23/2023
---

# Tutorial: Build a report from the OneLake data hub

**Applies to:** [!INCLUDE[fabric-se-and-dw](includes/applies-to-version/fabric-se-and-dw.md)]

Learn how to build a report with the data you ingested into your [!INCLUDE [fabric-dw](includes/fabric-dw.md)] in the last step.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Build a report

1. Select the **OneLake data hub** in the navigation menu.

   :::image type="content" source="media\tutorial-build-report\build-report-onelake-data-hub.png" alt-text="Screenshot of the navigation menu, showing where to select OneLake data hub.":::

1. From the item list, select `WideWorldImporters` with the type of **Dataset (default)**.

   :::image type="content" source="media\tutorial-build-report\select-dataset-default-list.png" alt-text="Screenshot of WWI default dataset in the list of items in the workspace.":::

1. In the **Visualize this data** section, select **Create a report** > **Auto-create**. A report is generated from the `dimension_customer` table that was loaded in the previous section.

   :::image type="content" source="media\tutorial-build-report\visualize-create-report.png" alt-text="Screenshot of the Visualize this data section, showing where to select Auto-create from the Create a report menu.":::

1. A report similar to the following image is generated.

   :::image type="content" source="media\tutorial-build-report\quick-summary-report-example.png" alt-text="Screenshot of a Quick summary page that shows four different bar charts as an example of an auto-created report."lightbox="media\tutorial-build-report\quick-summary-report-example.png":::

1. From the ribbon, select **Save**.

1. Enter `Customer Quick Summary` in the name box. In the **Save your report** dialogue, select **Save**.

   :::image type="content" source="media\tutorial-build-report\save-report-dialog.png" alt-text="Screenshot of the Save your report dialog with the report name Customer Quick Summary entered.":::

1. Your tutorial is complete!
    1. Review [Security for data warehousing in Microsoft Fabric](security.md).
    1. Learn more about [Workspace roles in Fabric data warehousing](workspace-roles.md).
    1. Consider [Microsoft Purview](../governance/microsoft-purview-fabric.md), included by default in every tenant to meet important compliance and governance needs.

## Next steps

> [!div class="nextstepaction"]
> [Tutorial: Clean up tutorial resources](tutorial-clean-up.md)