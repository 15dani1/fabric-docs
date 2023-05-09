---
title: Data management in Real-Time Analytics
description: Learn how to manage your data in Real-Time Analytics in Microsoft Fabric.
ms.reviewer: tzgitlin
ms.author: yaschust
author: YaelSchuster
ms.topic: conceptual
ms.date: 05/23/2023
ms.search.form: product-kusto
---

# Data management

[!INCLUDE [preview-note](../includes/preview-note.md)]

Synapse Real-Time Analytics offers a range of options for managing your data, both on a database and table level. You can manage your data either through the UI of your KQL database or by using management commands. Management commands, also known as control commands, are requests to the service to retrieve information that isn't necessarily data in the database tables, or requests to modify the service state.

For more information, see [Management commands](/azure/data-explorer/kusto/management/index?context=/fabric/context/context&pivots=fabric)


## Database management

### Data retention policy

To change the data retention policy, browse to your KQL database and select the **Manage** tab. Then, select **Data retention policy**. Enter a time period and select **Done**. By default, your data is stored for 36,500 days.

For more information, see [Retention policy](/azure/data-explorer/kusto/management/retentionpolicy?context=/fabric/context/context).

### One logical copy

To expose the data in your KQL database to all of [!INCLUDE [product-name](../includes/product-name.md)] experiences, create a OneLake shortcut.

For more information, see [One logical copy](onelake-mirroring.md).

## Table management

### Table update policy

When you trigger an update policy with a command that adds data to a source table, data also appends to a target table. The target table can have a different schema, retention policy, and other policies from the source table.

For more information, see [Create a table update policy](table-update-policy.md).

### Materialized views

A materialized view is an aggregation query over a source table, or over another materialized view. It represents a single `summarize` statement. You can create materialized views using the `.create materialized-view` command.

For more information, see [Create materialized views](materialized-view.md)

## Stored functions

This feature allows you to create or alter an existing function using the `.create-or-alter` `function` command, which stores it in the database metadata. If the function with the provided *functionName* doesn't exist in the database metadata, the command creates a new function. Otherwise, the named function is changed.

For more information, see [Create stored functions](create-functions.md)

## Next steps

* [Create a database](create-database.md)
* [Get data from a blob](get-data-blob.md)
* [Query data in the KQL Queryset](kusto-query-set.md)
