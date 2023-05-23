---
title: Manual updates with Git integration
description: Learn how to update your workspace manually when there's an internal inconsistency.
author: mberdugo
ms.author: monaberdugo
ms.service: powerbi
ms.topic: how-to
ms.date: 05/23/2023
ms.custom: build-2023
---

# Manual update

When updating items in a workspace, there’s always a chance that one of them will fail. The workspace fails to update if the incoming update from the git branch causes inconsistencies or other problems in the workspace that are difficult to determine in advance. When an item fails to update, the update process stops. If the item that failed is the first (or only) item that was updating, the update fails, but the workspace is still synced with the original branch. If an item fails after one or more items succeeded in updating, you're left in a situation where some items are synced and some aren't so your workspace isn't synced to any git branch.

[!INCLUDE [preview-note](../../includes/preview-note.md)]

There are many reasons that an update can fail, including, but not limited to the following problems:

* Dependent items were changed or deleted
* Circular dependencies were created
* Item renamed
* Invalid item data

> [!NOTE]
> This is not the same as [conflict resolution](./conflict-resolution.md). If changes were made to the same item in both the workspace and git branch, it causes a conflict and updates are disabled. This article discusses what to do a workspace fails to update even though there are no direct conflicts.

An error message lets you know which item failed and why.

:::image type="content" source="./media/partial-update/partial-update-error.png" alt-text="Screenshot showing the error message when update fails.":::

This error message appears when the update fails. Any user trying to access the workspace after that sees the following error until the update is completed successfully.

:::image type="content" source="./media/partial-update/unable-to-update.png" alt-text="Screenshot showing the error message when someone tries to connect to a workspace after an update fails.":::

Select **View details** to see the previous error message.

## Git statuses after an item fails

Your workspace now contains the following items

* The item or items updated before the failure. These items are identical to the items in git, but the metadata isn't updated. They have a git status of *synced* but with a triangle warning sign. :::image type="icon" source="./media/partial-update/warning.png":::
* The item that failed. This item has a git status of *Update required*.
* Possibly, items that weren't updated yet when the item failed. These items haven't been updated yet and have a git status of *Update required*.

The status bar at the bottom of the screen that shows the latest sync status is red and indicated the partially synced status.

:::image type="content" source="./media/partial-update/partial-update-status.png" alt-text="Screenshot showing status line at the bottom of the screen when an update fails.":::

## Update the failed item

To update the workspace manually after it failed to update automatically:

1. Figure out which item is causing the update to fail and what the problem is using the error dialog that says which item failed and error message.
1. Fix the problem in git. This can mean doing one or more of the following depending on what the issue is:
   * Revert the item to an earlier version that doesn't fail
   * Edit the item so it doesn't fail
   * Restore a dependant item that was deleted
1. Go back to the workspace and [**Update**](./git-get-started.md#update-workspace-from-git) the entire workspace again

## Considerations and limitations

The update process fails as soon as one item fails. Therefore, there's no way to know if other items in the git branch are also problematic. If you're updating many items and more than one item is problematic, you have to repeat this process once for each failed item.

## Next steps

[Conflict resolution](./conflict-resolution.md)
