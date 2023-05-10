---
title: Data warehouse tutorial - analyze data with a notebook
description: In this tutorial step, learn how to analyze Fabric data with a notebook.
ms.reviewer: wiassaf
ms.author: prlangad
author: prlangad
ms.topic: tutorial
ms.date: 5/23/2023
---

# Tutorial: Analyze data with a notebook

**Applies to:** [!INCLUDE[fabric-se-and-dw](includes/applies-to-version/fabric-se-and-dw.md)]

In this tutorial, learn about how you can save your data once and then use it with many other services.  Shortcuts can also be created to data stored in Azure Data Lake Storage and S3 to enable you to directly access delta tables from external systems.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Create a lakehouse

First, we create a new lakehouse. To create a new lakehouse in your [!INCLUDE [product-name](../includes/product-name.md)] workspace:

1. Select the `Data Warehouse Tutorial` workspace in the navigation menu.
1. Select **+ New** > **Lakehouse (Preview)**.

    :::image type="content" source="media/tutorial-analyze-data-notebook/new-lakehouse-menu.png" alt-text="A screenshot from the Fabric portal showing the + New menu. Lakehouse (Preview) is boxed in red.":::

1. In the **Name** field, enter `ShortcutExercise` and select **Create**.

    :::image type="content" source="media/tutorial-analyze-data-notebook/new-lakehouse-create-name.png" alt-text="A screenshot from the Fabric portal showing name field for the new lakehouse. The name provided is ShortcutExercise.":::

1. The new lakehouse loads and the **Explorer** view opens up, with the **Get data in your lakehouse** menu. Under **Load data in your lakehouse**, select the **New shortcut** button.

    :::image type="content" source="media/tutorial-analyze-data-notebook/lakehouse-load-data-new-shortcut.png" alt-text="A screenshot from the Fabric portal showing the Load data in your lakehouse menu on the landing page. The New shortcut button is boxed in red.":::

1. In the **New shortcut** window, select the button for **Microsoft OneLake**.

    :::image type="content" source="media/tutorial-analyze-data-notebook/new-shortcut-onelake.png" alt-text="A screenshot from the Fabric portal showing the New shortcut window. The button for Microsoft OneLake is boxed in red.":::

1. In the **Select a data source type** window, scroll through the list until you find the **Warehouse** named `WideWorldImporters` you created previously. Select it, then select **Next**.
1. In the OneLake object browser, expand **Tables**, expand the `dbo` schema, and then select the radio button beside `dimension_customer`. Select the **Create** button. 

    :::image type="content" source="media/tutorial-analyze-data-notebook/dim-customer-shortcut-exercise.png" alt-text="A screenshot from the Fabric portal showing the OneLake object browser. Under WideWorldImporters, Tables, dbo, the dimension_customer is boxed in red.":::

1. If you see a folder called `Unidentified` under **Tables**, select the **Refresh** icon in the horizontal menu bar.

    :::image type="content" source="media/tutorial-analyze-data-notebook/lakehouse-explorer-refresh-button.png" alt-text="A screenshot from the Fabric portal showing the refresh button on the horizontal menu bar, and the Unidentified tables under ShortcutExercise in the Lakehouse explorer.":::

1. Select the `dimension_customer` in the **Table** list to preview the data. Notice that the lakehouse is showing the data from the `dimension_customer` table from the [!INCLUDE [fabric-dw](includes/fabric-dw.md)]!

    :::image type="content" source="media/tutorial-analyze-data-notebook/lakehouse-table-preview.png" alt-text="A screenshot from the Fabric portal showing the data preview of the dimension_customer table.":::

1. Next, create a new notebook to query the `dimension_customer` table. In the **Home** ribbon, select the drop down for **Open notebook** and choose **New notebook**.

    :::image type="content" source="media/tutorial-analyze-data-notebook/lakehouse-explorer-open-notebook-new-notebook.png" alt-text="A screenshot from the Fabric portal showing the Open notebook button pressed, and the New notebook option selected.":::

1. Select, then drag the `dimension_customer` from the **Tables** list into the open notebook cell. You can see a PySpark query has been written for you to query all the data from `ShortcutExercise.dimension_customer`. This notebook experience is similar to Visual Studio Code Jupyter notebook experience. You can also open the notebook in VS Code.

    :::image type="content" source="media/tutorial-analyze-data-notebook/drop-dim-customer-notebook.png" alt-text="A screenshot from the Fabric portal notebook view. An arrow indicates the path to select dimension_customer, then drag and drop it into the open notebook cell.":::

1. In the **Home** ribbon, select the **Run all** button. Once the query is completed, you will see that you can now easily use PySpark to query the [!INCLUDE [fabric-dw](includes/fabric-dw.md)] tables!

    :::image type="content" source="media/tutorial-analyze-data-notebook/data-notebook-run-all-results.png" alt-text="A screenshot from the Fabric portal showing the results of running the the notebook to display data from dimension_customer.":::

## Next steps

> [!div class="nextstepaction"]
> [Tutorial: Create a Power BI report](tutorial-power-bi-report.md)
