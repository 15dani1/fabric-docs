---
title: Create stored functions in Real-Time Analytics
description: "Learn how to use the `.create-or-alter function` command to create stored functions in Real-Time Analytics."
ms.reviewer: tzgitlin
ms.author: yaschust
author: YaelSchuster
ms.topic: how-to
ms.date: 05/23/2023
ms.search.form: product-kusto
---

# Create stored functions

Functions are reusable queries or query parts. Real-Time Analytics supports two kinds of functions:

* Built-in functions, which are hard-coded functions that can't be modified by users.
* User-defined functions, which are divided into two types:

  * Stored functions: are user-defined functions that are stored and managed database schema entities (such as tables). For more information on how to create and manage stored functions, see [Stored functions management overview](/azure/data-explorer/kusto/management/functions?context=/fabric/context/context).
  * Query-defined functions: are user-defined functions that are defined and used within the scope of a single query. The definition of such functions is done through a let statement. For more information on how to create query-defined functions, see [Create a user defined function](/azure/data-explorer/kusto/query/letstatement?context=/fabric/context/context).

In this article, you learn how to create or alter an existing stored function using the `.create-or-alter` `function`.

For more information on the `.create-or-alter` `function` command, see [`.create-or-alter function`](/azure/data-explorer/kusto/management/create-alter-function?context=/fabric/context/context)

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Prerequisites

* [Power BI Premium](/power-bi/enterprise/service-admin-premium-purchase) enabled [workspace](../get-started/create-workspaces.md)
* [KQL database](create-database.md)

## Functions

This feature allows you to create or alter an existing function using the `.create-or-alter` `function` command, which stores it in the database metadata. If the function with the provided *functionName* doesn't exist in the database metadata, the command creates a new function. Otherwise, the named function is changed.

1. Select **New** > **Function**. The `.create-or-alter` command is automatically populated in the **Explore your data** window.

    :::image type="content" source="media/create-functions/function-cmd.png" alt-text="Screenshot of the New option dropdown menu. The option titled Function is highlighted.":::

1. Enter the parameters for your function, and then select **Run**.

    :::image type="content" source="media/create-functions/create-function.png" alt-text="Screenshot of explore your data window showing the newly created function in Real-Time Analytics.":::

    Stored functions appear under **Functions** in the **Data tree**.

    :::image type="content" source="media/create-functions/functions-object-tree.png" alt-text="Screenshot of Object tree showing the list of stored user-defined functions.":::

1. In the **Explore your data** window, run a query to check that you have successfully created or altered your function. 

    :::image type="content" source="media/create-functions/function-example.png" alt-text="Screenshot of the explore your data window showing query results of a stored function in Real-Time Analytics.":::

## Next steps

[Query data in the KQL Queryset](kusto-query-set.md)
