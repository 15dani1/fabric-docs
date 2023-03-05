---
title: How to configure Azure SQL Database in copy activity
description: This article explains how to copy data using Azure SQL Database.
author: jianleishen
ms.author: jianleishen
ms.subservice: data-factory
ms.topic: how-to
ms.date: 01/10/2023
ms.custom: template-how-to 
---

# How to configure Azure SQL Database in copy activity

This article outlines how to use the copy activity in data pipeline to copy data from and to Azure SQL Database.

## Supported format

Azure SQL Database supports the following file formats. 

## Supported configuration

For the configuration of each tab under copy activity, go to the following sections respectively.

- [General](#general)  
- [Source](#source)
- [Destination](#destination)
- [Mapping](#mapping)
- [Settings](#settings)

### General

For **General** tab configuration, go to General.

### Source

The following properties are supported for Azure SQL Database under the **Source** tab of a copy activity.

:::image type="content" source="./media/connector-azure-sql-database/source.png" alt-text="Screenshot showing the source tab and the list of properties." lightbox="./media/connector-azure-sql-database/source.png":::

The following properties are **required**:
- **Data store type**: Select **External**.
- **Connection**:  Select an Azure SQL Database connection from the connection list. If not exist, then create a new Azure SQL Database connection by clicking on **New**.
- **Connection type**: Select **Azure SQL Database**.
- **Table**: Select the table in your database from the drop-down list. Or check **Edit** to enter your table name manually.
- **Preview data**: Select on **Preview data** to preview the data in your table.

Under **Advanced**, you can specify the following fields:

- **Use query**: You can choose **Table**, **Query** or **Stored procedure**. Go to the configuration of each setting below：

    - **Table**: Read data from the table you specified in **Table** above if you select this button.

    - **Query**: Specify the custom SQL query to read data. An example is `select * from MyTable`. Or select the pencil icon to edit in code editor.

        :::image type="content" source="./media/connector-azure-sql-database/query.png" alt-text="Screenshot showing choosing query.":::

    - **Stored procedure**: Use the stored procedure that reads data from the source table. The last SQL statement must be a SELECT statement in the stored procedure.
        - **Stored procedure name**: Select the stored procedure or specify the stored procedure name manually when checking the **Edit** box to read data from the source table. 
        - **Stored procedure parameters**: Specify values for stored procedure parameters. Allowed values are name or value pairs. The names and casing of parameters must match the names and casing of the stored procedure parameters.
            
            :::image type="content" source="./media/connector-azure-sql-database/stored-procedure.png" alt-text="Screenshot showing stored procedure settings."::: 
                
- **Query timeout (minutes)**: Specify the timeout for query command execution, default is 120 minutes. If parameter is set for this property, allowed values are timespan, such as "02:00:00" (120 minutes).

    :::image type="content" source="./media/connector-azure-sql-database/query-timeout.png" alt-text="Screenshot showing Query timeout settings."::: 

- **Isolation level**: Specifies the transaction locking behavior for the SQL source. The allowed values are: **None**, **ReadCommitted**, **ReadUncommitted**, **RepeatableRead**, **Serializable**, **Snapshot**. If not specified, **None** isolation level is used. Refer to this [doc](/dotnet/api/system.data.isolationlevel) for more details.

    :::image type="content" source="./media/connector-azure-sql-database/isolation-level.png" alt-text="Screenshot showing Isolation level settings."::: 

- **Partition option**: Specify the data partitioning options used to load data from Azure SQL Database. Allowed values are: **None** (default), **Physical partitions of table**, and **Dynamic range**. When a partition option is enabled (that is, not None), the degree of parallelism to concurrently load data from an Azure SQL Database is controlled by the [parallel copy](/azure/data-factory/copy-activity-performance-features#parallel-copy) setting on the copy activity.

    :::image type="content" source="./media/connector-azure-sql-database/partition-option-1.png" alt-text="Screenshot showing Partition option settings."::: 
    
    - **None**: Choose this to not use partition.
    - **Physical partitions of table**: When using physical partition, the partition column and mechanism will be auto determined based on your physical table definition.
    - **Dynamic range**: When using query with parallel enabled, range partition parameter(?AdfDynamicRangePartitionCondition) is needed. Sample query: `SELECT * FROM <TableName> WHERE ?AdfDynamicRangePartitionCondition`.

        - **Partition column name**: Specify the name of the source column in **integer or date/datetime** type (`int`, `smallint`, `bigint`, `date`, `smalldatetime`, `datetime`, `datetime2`, or `datetimeoffset`) that will be used by range partitioning for parallel copy. If not specified, the index or the primary key of the table is autodetected and used as the partition column.
        - **Partition upper bound**: Specify the maximum value of the partition column for partition range splitting. This value is used to decide the partition stride, not for filtering the rows in table. All rows in the table or query result will be partitioned and copied.
        - **Partition lower bound**: Specify the minimum value of the partition column for partition range splitting. This value is used to decide the partition stride, not for filtering the rows in table. All rows in the table or query result will be partitioned and copied.

- **Additional columns**: Add additional data columns to store source files' relative path or static value. Expression is supported for the latter. For more information, see [Add additional columns during copy](/azure/data-factory/copy-activity-overview#add-additional-columns-during-copy).

### Destination

The following properties are supported for Azure SQL Database under **Destination** tab of a copy activity.

:::image type="content" source="./media/connector-azure-sql-database/destination.png" alt-text="Screenshot showing Destination tab.":::

The following properties are **required**:
- **Data store type**: Select **External**.
- **Connection**:  Select an Azure SQL Database connection from the connection list. If not exist, then create a new Azure SQL Database connection by clicking on **New**.
- **Connection type**: Select **Azure SQL Database**.
- **Table**: Select the table in your database from the drop-down list. Or check **Edit** to enter your table name manually.
- **Preview data**: Select on **Preview data** to preview the data in your table.

Under **Advanced**, you can specify the following fields:

- **Write behavior**: Defines the write behavior when the source is files from a file-based data store. You can choose **Insert**, **Upsert** or **Stored procedure**.

    :::image type="content" source="./media/connector-azure-sql-database/writer-behavior.png" alt-text="Screenshot showing write behavior tab.":::

    - **Insert**: Choose this option if your source data has inserts.

    - **Upsert**: Choose this option if your source data has both inserts and updates.

        - **Use TempDB**: Specify whether to use a global temporary table or physical table as the interim table for upsert. By default, the service uses global temporary table as the interim table and this checkbox is selected.
        
            :::image type="content" source="./media/connector-azure-sql-database/use-tempdb.png" alt-text="Screenshot showing select Use TempDB.":::

        - **Select user DB schema**: When the **Use TempDB** checkbox is not selected, specify the interim schema for creating interim table if physical table is used. 
        
            >[!Note]
            > User need to have the permission for creating and deleting table. By default, interim table will share the same schema as destination table.
    
            :::image type="content" source="./media/connector-azure-sql-database/not-use-tempdb.png" alt-text="Screenshot showing not select Use TempDB.":::

        - **Key columns**: Specify the column names for unique row identification. Either a single key or a series of keys can be used. If not specified, the primary key is used.

    - **Stored procedure**: Use the stored procedure that defines how to apply source data into a target table. This stored procedure is *invoked per batch*. 

        - **Stored procedure name**: Select the stored procedure or specify the stored procedure name manually when checking the **Edit** box to read data from the source table. 
        - **Stored procedure parameters**: Specify values for stored procedure parameters. Allowed values are name or value pairs. The names and casing of parameters must match the names and casing of the stored procedure parameters.
            
            :::image type="content" source="./media/connector-azure-sql-database/stored-procedure.png" alt-text="Screenshot showing stored procedure settings."::: 

    
- **Bulk insert table lock**: Choose **Yes** or **No**. Use this to improve copy performance during bulk insert operation on table with no index from multiple clients. For more information, see [BULK INSERT (Transact-SQL)](/sql/t-sql/statements/bulk-insert-transact-sql)

- **Table option**: Specifies whether to [automatically create the destination table](/azure/data-factory/copy-activity-overview#auto-create-sink-tables) if not exists based on the source schema. Choose **None** or **Auto create table**. Auto table creation is not supported when destination specifies stored procedure. 

- **Pre-copy script**: Specify a script for Copy Activity to execute before writing data into destination table in each run. You can use this property to clean up the pre-loaded data.

- **Write batch timeout**: Specify the wait time for the batch insert operation to finish before it times out. The allowed value is timespan. The default value is "00:30:00" (30 minutes).

- **Write batch size**: Specify the number of rows to insert into the SQL table per batch. The allowed value is integer (number of rows). By default, the service dynamically determines the appropriate batch size based on the row size.

- **Max concurrent connections**: Specify the upper limit of concurrent connections established to the data store during the activity run. Specify a value only when you want to limit concurrent connections.

- **Disable performance metrics analytics**: This is to collect metrics such as DTU, DWU, RU, etc. for copy performance optimization and recommendations. If you are concerned with this behavior, please select this checkbox.

### Settings

For **Settings** tab configuration, see Settings.

### Mapping

For **Mapping** tab configuration, see Mapping.

## Table summary 

To learn more information about copy activity in Azure SQL Database, see the following table.

### Source

|Name |Description |Value|Required |JSON script property |
|:---|:---|:---|:---|:---|
|**Data store type**|Your data store type.| **Workspace** or **External**|Yes|type|
|**Connection** |Your connection to the source data store.|< your connection > |Yes|connection|
|**Connection type** |Your connection type. Select **Azure SQL Database**.|< your connection type> |Yes|type|
|**Table** | Your source data table. |< name of your destination table>|Yes |schema <br> table|
|**Use query** |The custom SQL query to read data.|- None <br>- Query<br>- Stored procedure |No |<br><br>- sqlReaderQuery <br>- sqlReaderStoredProcedureName, storedProcedureParameters|
|**Query timeout** |The timeout for query command execution, default is 120 minutes. |timespan |No |queryTimeout|
|**Isolation level** |Specifies the transaction locking behavior for the SQL source.|- None<br> - ReadCommitted<br>- ReadUncommitted<br> - RepeatableRead<br> - Serializable<br> - Snapshot|No |isolationLevel|
|**Partition option** |The data partitioning options used to load data from Azure SQL Database. |- None<br>- Physical partitions of table<br>- Dynamic range |No |partitionOption:<br>- PhysicalPartitionsOfTable<br> - DynamicRange|
|**Additional columns** |Add additional data columns to store source files' relative path or static value. Expression is supported for the latter.| - Name<br>- Value|No |additionalColumns:<br>- name<br>- value |

### Destination

|Name |Description |Value|Required |JSON script property |
|:---|:---|:---|:---|:---|
|**Data store type**|Your data store type.|**Workspace** or **External** |Yes|type|
|**Connection** |Your connection to destination data store.|< your connection >|Yes|connection|
|**Connection type** |Your connection type. Select **Azure SQL Database**.|< your connection type> |Yes|type|
|**Table**|Your destination data table.| \<name of your destination table\> |Yes |schema <br> table|
|**Write behavior** |Defines the write behavior when the source is files from a file-based data store.|- Insert<br>- Upsert<br>- Stored procedure|No |writeBehavior:<br> - insert<br>- upsert<br>- sqlWriterStoredProcedureName, sqlWriterTableType, storedProcedureParameters|
|**Bulk insert table lock** |Use this to improve copy performance during bulk insert operation on table with no index from multiple clients.|Yes or No |No |sqlWriterUseTableLock:<br>true or false|
|**Table option** |Specifies whether to automatically create the destination table if not exists based on the source schema.|- None <br>- Auto create table|No |tableOption:<br>- autoCreate|
|**Pre-copy script**|A script for Copy Activity to execute before writing data into destination table in each run. You can use this property to clean up the pre-loaded data.| < pre-copy script ><br>(string)|No |preCopyScript|
|**Write batch timeout**|The wait time for the batch insert operation to finish before it times out. The allowed value is timespan. The default value is "00:30:00" (30 minutes).|timespan |No |writeBatchTimeout|
|**Write batch size**|The number of rows to insert into the SQL table per batch. By default, the service dynamically determines the appropriate batch size based on the row size.|< number of rows ><br>(integer) |No |writeBatchSize|
|**Max concurrent connections**|The upper limit of concurrent connections established to the data store during the activity run. Specify a value only when you want to limit concurrent connections.| < upper limit of concurrent connections ><br>(integer)|No |maxConcurrentConnections|
|**Disable performance metrics analytics**|This is to collect metrics such as DTU, DWU, RU, etc. for copy performance optimization and recommendations. If you are concerned with this behavior, please select this checkbox.| select or unselect |No |disableMetricsCollection：<br> true or false|


## Next Steps

[How to create Azure SQL Database connection](connector-azure-sql-database.md)

