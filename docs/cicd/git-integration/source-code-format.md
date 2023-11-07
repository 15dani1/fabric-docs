---
title: Git source code format
description: Understand how the items in Microsoft Fabric's Git integration tool are structured
author: mberdugo
ms.author: monaberdugo
ms.reviewer: NimrodShalit
ms.topic: conceptual 
ms.date: 11/06/2023
ms.custom: ignite-2023
---

# Git integration source code format

Items in Microsoft Fabric are stored in a folder. The folder containing the item can either be in the root directory or a subdirectory. When you connect your workspace to git, connect to the folder containing the items. Each item in the folder is represented in its own subdirectory. These item directories have the same name as the item followed by the item type.

:::image type="content" source="./media/source-code-format/item-directory-names.png" alt-text="Screenshot of Git directory containing items.":::

[!INCLUDE [preview-note](../../includes/feature-preview-note.md)]

Inside each item directory are the [item definition files](#item-definition-files) as well as either one or two [automatically generated system files](#automatically-generated-system-files) in each directory.

## Item definition files

Each item's directory has specific [mandatory files that define that item](/power-bi/developer/projects/projects-overview).

The following items are currently supported in Microsoft Fabric:

- [Dataset files](#dataset-files)
- [Notebook files](#notebook-files)
- [Paginated report files](#paginated-report-files)
- [Report files](#report-files)

### Dataset files

Dataset folders contain the following files:

- definition.pbidataset
- model.bim

:::image type="content" source="./media/source-code-format/dataset-directory.png" alt-text="Screenshot of directory tree showing files in the dataset directory.":::

For more information about dataset folders and a complete list of their contents, see [Power BI Desktop project dataset folder](/power-bi/developer/projects/projects-dataset).

### Notebook files

Notebook folders contain a *.py* file

:::image type="content" source="./media/source-code-format/notebook-directory.png" alt-text="Screenshot of directory tree showing files in the notebook directory.":::

For instructions on using Git integration with notebooks, see [Notebook source control and deployment](../../data-engineering/notebook-source-control-deployment.md).

### Paginated report files

Paginated report folders contain an *.rdl* file defining the paginated report. RDL (Report Definition Language) is an XML representation of a paginated report definition.

For more information o RDL, see [Report Definition Language (RDL)](/power-bi/paginated-reports/report-definition-language).
For instructions on using Git integration with paginated reports, see [Git integration with paginated reports](/power-bi/paginated-reports/paginated-github-integration).

### Report files

Report folders contain the following files:

- definition.pbir
- report.json

:::image type="content" source="./media/source-code-format/report-directory.png" alt-text="Screenshot of directory tree showing files in the report directory.":::

For more information about report folders and a complete list of their contents, see [Power BI Desktop project report folder](/power-bi/developer/projects/projects-report).

## Automatically generated system files

In addition to the item definition files, each item directory contains one or two automatically generated system files, depending on which version you're using:

- **Version 1** directories contain [item.metadata.json](#metadata-file) and [item.config.json](#config-file). When using V1, both files must be in the directory.
- **Version 2** directories contain [.platform](#platform-file). This file includes the content of both *metadata.json* and *item.config.json* files. If you have this file, you can't have the other two files.

>[!NOTE]
>Your directory must contain either the item.metadata.json* and *item.config.json* files *or* the *.platform* file. You can't have all three files.

### [Version 1](#tab/v1)

### Metadata file

```json
{ 
    "type": <string>, 
    "displayName": <string>,
    "description": <string>
} 
```

The item.metadata.json file contains the following attributes:

- `type`: the item's type (dataset, report etc.)
- `displayName`: the name of the item
- `description`: (optional) description of the item

To rename an item, change the `displayName` in the 'item.metadata.json' file. Changing the name of the folder doesn't change the display name of the item in the workspace.

### Config file

```json
{ 
    version: "1.0", 
    logicalId: <guid>, 
} 
```

The `item.config.json` file contains the following attributes:

- `version`: version number of the system files. This number is used to enable backwards compatibility. Version number of the item might be different.
- `logicalId`: an automatically generated cross-workspace identifier representing an item and its source control representation.

The logicalId connects an item in a workspace with its corresponding item in a Git branch. Items with the same logicalIds are assumed to be the same. The logicalId preserves the link even if the name or directory change. Since a branch can be synced to multiple workspaces, it's possible to have items in different workspaces with the same logicalId, but a single workspace can't have two items with the same logicalId. The logicalId is created when the workspace is connected to a Git branch or a new item is synced. The logicalId is necessary for Git integration to function properly. Therefore, it's essential not to change it in any way.

### [Version 2](#tab/v2)

### Platform file

In version 2, instead of having two source files in each item directory, the *.platform* file combines all the information into one file. If you have this file, you can't have the other two files.

```json
{ 
    version: "2.0", 
    logicalId: <guid>, 
}, 
{
    "type": <string>, 
    "displayName": <string>,
    "description": <string>
}
```

The *.platform* file contains the following attributes:

- `type`: the item's type (dataset, report etc.)
- `displayName`: the name of the item
- `description`: (optional) description of the item
- `version`: version number of the system files. This number is used to enable backwards compatibility. Version number of the item might be different.
- `logicalId`: an automatically generated cross-workspace identifier representing an item and its source control representation.

---

> [!NOTE]
> Though you should not generally change the *logicalId* or *display name* of an item, one exception might be if you're creating a new item by copying an existing item directory. In that case, you do need to change the *logicalId* and the *display name* to something unique in the repository.

## Next steps

[Get started with Git integration](./git-get-started.md)
