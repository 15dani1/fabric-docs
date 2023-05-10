---
title: How to configure Lakehouse in a copy activity
description: This article explains how to copy data using Lakehouse.
author: jianleishen
ms.author: jianleishen
ms.topic: how-to
ms.date: 05/23/2023
ms.custom: template-how-to 
---

# How to configure Lakehouse in a copy activity

This article outlines how to use the copy activity in a data pipeline to copy data from and to the Fabric Lakehouse.

[!INCLUDE [df-preview-warning](includes/data-factory-preview-warning.md)]

## Supported format

Lakehouse supports the following file formats. Refer to each article for format-based settings.

- Avro format
- [Binary format](format-binary.md)
- [Delimited text format](format-delimited-text.md)
- [Excel format](format-excel.md)
- JSON format
- ORC format
- Parquet format
- XML format

## Supported configuration

For the configuration of each tab under copy activity, go to the following sections respectively.

- [General](#general)  
- [Source](#source)
- [Destination](#destination)
- [Mapping](#mapping)
- [Settings](#settings)

### General

For the **General** tab configuration, go to [General](activity-overview.md#general-settings).

### Source

The following properties are supported for Lakehouse under the **Source** tab of a copy activity.

:::image type="content" source="./media/connector-lakehouse/source.png" alt-text="Screenshot showing source tab and the list of properties." lightbox="./media/connector-lakehouse/source.png":::

The following properties are **required**:

- **Data store type**: Select **Workspace**.
- **Workspace data store type**: Select **Lakehouse** from the data store type list.
- **Lakehouse**: Select an existing Lakehouse from the workspace. If none exists, then create a new Lakehouse by selecting **New**.
- **Root folder**: Select **Tables** or **Files**, which indicates the virtual view of the managed or unmanaged area in your lake. For more information, refer to [Lakehouse introduction](../data-engineering/lakehouse-overview.md).
  - If you select **Tables**:
    - **Table name**: Choose an existing table from the table list or specify a table name as the source.
    - Under **Advanced**, you can specify the following fields:
      - **Timestamp**: Specify to query an older snapshot by timestamp.
      - **Version**: Specify to query an older snapshot by version.
      - **Additional columns**: Add additional data columns to the store source files' relative path or static value. Expression is supported for the latter.
  - If you select **Files**:
    - **File path type**: You can choose **File path**, **Wildcard file path**, or **List of files** as your file path type. The following list describes the configuration of each setting：

      :::image type="content" source="./media/connector-lakehouse/file-path.png" alt-text="Screenshot showing file path." lightbox="./media/connector-lakehouse/file-path.png":::

      - **File path**: Select **Browse** to choose the file that you want to copy, or fill in the path manually.
      - **Wildcard file path**: Specify the folder or file path with wildcard characters under your given Lakehouse unmanaged area (under Files) to filter your source folders or files. Allowed wildcards are: `*` (matches zero or more characters) and `?` (matches zero or single character). Use `^` to escape if your folder or file name has wildcard or this escape character inside.
        - **Wildcard folder path**: The path to the folder under the given container. If you want to use a wildcard to filter the folder, skip this setting and specify that information in the activity source settings.
        - **Wildcard file name**: The file name under the given Lakehouse unmanaged area (under Files) and folder path.

          :::image type="content" source="./media/connector-lakehouse/wildcard-paths.png" alt-text="Screenshot showing wildcard file path." lightbox="./media/connector-lakehouse/wildcard-paths.png":::

      - **List of files**: Indicates to copy a given file set.
        - **Folder path**: Points to a folder that includes files you want to copy.
        - **Path to file list**: Points to a text file that includes a list of files you want to copy, one file per line, which is the relative path to the file path configured.

        :::image type="content" source="./media/connector-lakehouse/list-of-files.png" alt-text="Screenshot showing path to file list." lightbox="./media/connector-lakehouse/list-of-files.png":::

    - **Recursively**: Indicates whether the data is read recursively from the subfolders or only from the specified folder. If enabled, all files in the input folder and its subfolders are processed recursively. This property doesn’t apply when you configure your file path type as **List of files**.
    - **File format**: Select your file format from the drop-down list. Select the **Settings** button to configure the file format. For settings of different file formats, refer to articles in [Supported format](#supported-format) for detailed information.
    - Under **Advanced**, you can specify the following fields:
      - **Filter by last modified**: Files are filtered based on the last modified dates. This property doesn’t apply when you configure your file path type as **List of files**.
        - **Start time**: The files are selected if their last modified time is greater than or equal to the configured time.
        - **End time**: The files are selected if their last modified time is less than the configured time.
      - **Enable partition discovery**: For files that are partitioned, specify whether to parse the partitions from the file path and add them as extra source columns.
        - **Partition root path**: When partition discovery is enabled, specify the absolute root path in order to read partitioned folders as data columns.
      - **Max concurrent connections**: Indicates the upper limit of concurrent connections established to the data store during the activity run. Specify a value only when you want to limit concurrent connections.

## Destination

The following properties are supported for Lakehouse under the **Destination** tab of a copy activity.

:::image type="content" source="./media/connector-lakehouse/destination.png" alt-text="Screenshot showing destination tab." lightbox="./media/connector-lakehouse/destination.png":::

The following properties are **required**:

- **Data store type**: Select **Workspace**.
- **Workspace data store type**: Select **Lakehouse** from the data store type list.
- **Lakehouse**: Select an existing Lakehouse from the workspace. If none exists, then create a new Lakehouse by selecting **New**.
- **Root folder**: Select **Tables** or **Files**, which indicates the virtual view of the managed or unmanaged area in your lake. For more information, refer to [Lakehouse introduction](../data-engineering/lakehouse-overview.md).
  - If you select **Tables**:
    - **Table name**: Choose an existing table from the table list or specify a table name as the destination.

      :::image type="content" source="./media/connector-lakehouse/table-name.png" alt-text="Screenshot showing table name.":::

    - Under **Advanced**, you can specify the following fields:
      - **Max rows per file**: Specify the maximum rows per file when writing data into Lakehouse.
      - **Table actions**: Specify the operation against the selected table.
        - **Append**: Append new values to existing table.
        - **Overwrite**: Overwrite the existing data and schema in the table using the new values. If this operation is selected, you can enable partition on your target table:
          - **Enable Partition**: This selection allows you to create partitions in a folder structure based on one or multiple columns. Each distinct column value (pair) is a new partition. For example, "year=2000/month=01/file". This selection supports insert-only mode and requires an empty directory in the destination.
            - **Partition column name**: Select from the destination columns in schemas mapping. Supported data types are string, integer, boolean, and datetime. Format respects type conversion settings under the **Mapping** tab.
      - **Max concurrent connections**: The upper limit of concurrent connections established to the data store during the activity run. Specify a value only when you want to limit concurrent connections.

  - If you select **Files**:
    - **File path**: Select **Browse** to choose the file that you want to copy, or fill in the path manually.

      :::image type="content" source="./media/connector-lakehouse/files-path.png" alt-text="Screenshot showing files path in destination." lightbox="./media/connector-lakehouse/files-path.png":::

    - **File format**: Select your file format from the drop-down list. Select **Settings** to configure the file format. For settings of different file formats, refer to articles in [Supported format](#supported-format) for detailed information.
    - Under **Advanced**, you can specify the following fields:
      - **Copy behavior**: Defines the copy behavior when the source is files from a file-based data store. You can choose **Add Dynamic content**, **None**, **Flatten hierarchy**, or **Preserve hierarchy** as your copy behavior. The configuration of each setting is：
        - **Add dynamic content**: To specify an expression for a property value, select **Add dynamic content**. This field opens the expression builder where you can build expressions from supported system variables, activity output, functions, and user-specified variables or parameters. For more information about the expression language, go to [Expressions and functions](/azure/data-factory/control-flow-expression-language-functions).
        - **None**: Choose this selection to not use any copy behavior.
        - **Flatten hierarchy**: All files from the source folder are in the first level of the destination folder. The destination files have autogenerated names.
        - **Preserve hierarchy**: Preserves the file hierarchy in the target folder. The relative path of a source file to the source folder is identical to the relative path of a target file to the target folder.

          :::image type="content" source="./media/connector-lakehouse/copy-behavior.png" alt-text="Screenshot showing copy behavior." lightbox="./media/connector-lakehouse/copy-behavior.png":::

      - **Max concurrent connections**: The upper limit of concurrent connections established to the data store during the activity run. Specify a value only when you want to limit concurrent connections.
      - **Block size (MB)**: Specify the block size in MB when writing data to Lakehouse. Allowed value is between 4 MB and 100 MB.
      - **Metadata**: Set custom metadata when copying to the destination data store. Each object under the `metadata` array represents an extra column. The `name` defines the metadata key name, and the `value` indicates the data value of that key. If [preserve attributes feature](/azure/data-factory/copy-activity-preserve-metadata#preserve-metadata) is used, the specified metadata will union/overwrite with the source file metadata. The allowed data values are:
        - `$$LASTMODIFIED`: a reserved variable indicates to store the source files' last modified time. Apply to a file-based source with binary format only.
        - Expression
        - Static value

          :::image type="content" source="./media/connector-lakehouse/metadata.png" alt-text="Screenshot showing metadata." lightbox="./media/connector-lakehouse/metadata.png":::

### Mapping

For the **Mapping** tab configuration, go to [Mapping](copy-data-activity.md#configure-your-mappings-under-mapping-tab). If you choose Binary as your file format, mapping isn't supported.

### Settings

For the **Settings** tab configuration, go to [Settings](copy-data-activity.md#configure-your-other-settings-under-settings-tab).

## Table summary

The following tables contain more information about a copy activity in Lakehouse.

### Source information

|Name |Description |Value|Required |JSON script property |
|:---|:---|:---|:---|:---|
|**Data store type**|Your data store type.|**Workspace**|Yes|/|
|**Workspace data store type** |Select **Lakehouse** from the data store type list.|**Lakehouse**|Yes|type|
|**Lakehouse** | Select an existing Lakehouse from the workspace. If none exists, then create a new Lakehouse by selecting **New**.|\<your Lakehouse>|Yes |workspaceId<br>artifactId|
|**Root folder** |The type of the root folder.|• **Tables**<br>• **Files** |No|rootFolder|
|**Table name** |Specify your table name.|\<table name> |Yes when you select **Tables** in **Root folder** | table|
|**Timestamp** |Query an older snapshot by timestamp.| \<timestamp>|No |timestampAsOf |
|**Version** |Query an older snapshot by version.| \<version>|No |versionAsOf|
|**Additional columns** |Add additional data columns to store source files' relative path or static value.| • Name<br>• Value|No |additionalColumns:<br>• name<br>• value |
|**File path type** |the type of the file path. |•**File path**<br>• **Wildcard file path**<br> • **List of files** |Yes|**File path**<br>• folderPath<br>• fileName<br>**Wildcard file path**<br>• wildcardFolderPath<br>• wildcardFileName<br>**List of files**<br>• folderPath<br>• fileListPath |
|**Recursively** |Process all files in the input folder and its subfolders recursively or just the ones in the selected folder.| select or unselect |No | recursive:<br>true or false|
|**File format**|Format of the file.|\<file format>|Yes|type (under `formatSettings`):<br>DelimitedTextReadSettings|
|**Filter by last modified**|Files are filtered based on the last modified dates.|• **Start time**<br>• **End time** |No |modifiedDatetimeStart<br>modifiedDatetimeEnd|
|**Enable partition discovery**|Specify whether to parse the partitions from the file path and add them as extra source columns.| Selected or unselected |No| enablePartitionDiscovery: <br> true or false (default)|
|**Partition root path**|For files that are partitioned, specify whether to parse the partitions from the file path and add them as extra source columns.| \<your partition root path\> |No| partitionRootPath|
|**Max concurrent connections**|Specify a value only when you want to limit concurrent connections.|\<max concurrent connections>|No |maxConcurrentConnections|

### Destination information

|Name |Description |Value |Required |JSON script property |
|:---|:---|:---|:---|:---|
|**Data store type**|Your data store type.|**Workspace**|Yes|/|
|**Workspace data store type** |Select **Lakehouse** from the data store type list.|**Lakehouse**|Yes|type|
|**Lakehouse** | Select an existing Lakehouse from the workspace. If none exists, then create a new Lakehouse by selecting **New**.|\<your Lakehouse>|Yes |workspaceId<br>artifactId|
|**Root folder** |The type of the root folder.|• **Tables**<br>• **Files** |Yes | rootFolder|
|**Table name** |Specify your table name.|\<your table name> |Yes when you select **Tables** in **Root folder** | table|
|**Max rows per file** |When writing data into a folder, you can choose to write to multiple files and specify the maximum rows per file.|\<max rows per flie> |No |maxRowsPerFile|
|**Table action**|Append new values to an existing table or overwrite the existing data and schema in the table using the new values|• **Append**<br>• **Overwrite**|No|tableActionOption|
|**Max concurrent connections**|Specify a value only when you want to limit concurrent connections.|\<max concurrent connections>|No |maxConcurrentConnections|
|**File path**|Copy from the given file path specified|\<file path>|No|• folderPath<br>• fileName|
|**File format**|Format of the file.|\<file format>|Yes|type (under `formatSettings`):<br>DelimitedTextWriteSettings|
|**Copy behavior** |Defines behavior when copying files from one file system like storage to the other.|• **Add dynamic content**<br>• **None**<br>• **Flatten hierarchy**<br>• **Preserve hierarchy**|No |copyBehavior:<br><br><br>FlattenHierarchy<br>PreserveHierarchy|
|**Block size (MB)** |Specify the block size in MB when writing data to Lakehouse.|\<block size\>|No|blockSizeInMB|
|**Metadata** |Set custom metadata when copying to a destination.|• `$$LASTMODIFIED`<br>• Expression<br>• Static value|No |metadata|

## Next steps

- [Lakehouse connector overview](connector-lakehouse-overview.md)
