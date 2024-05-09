---
title: Manage tasks
description: This show how to add, delete, change, and connect tasks, and also how to assign items to tasks.
ms.reviewer: liud
ms.author: painbar
author: paulinbar
ms.topic: how-to
ms.date: 05/07/2024
---

# Manage tasks

When you select a task, the side panel displays the task details.

:::image type="content" source="./media/task-flow-work-with/task-details-side-pane.png" alt-text="Screenshot explaining the task details pane.":::

1. [Delete task](#delete-tasks)
1. [Edit task name and description](#edit-task-name-and-description)
1. [Change task type](#change-task-type)

## Add a task 

To add a new task to the task flow canvas, open the **Add** dropdown menu and select the desired task type.

:::image type="content" source="./media/task-flow-work-with/add-task.png" alt-text="Screenshot showing the Add dropdown menu on the task flow canvas." lightbox="./media/task-flow-work-with/add-task.png":::

The task of the selected task type is added onto the canvas. The name and description of the new task are the default name and description of the task type. Consider [changing the name and description](#change-task-details-and-type) of the new task to better describe its purpose in the work flow. A good task name should identify the task and provide a clear indication of its intended use.

## Edit task name and description

To edit a task's name or description:

1. Select the task on the canvas to open the [task details side pane](#manage-tasks).

2. Select **Edit** and change the name and description fields as desired. When done, select **Save**.

## Change task type

To change a task to a different type:

1. Select the task on the canvas to open the [task details side pane](#manage-tasks).

1. Open the **Task type** dropdown menu and choose the new desired task type.

> [!NOTE]
> Changing the task type doesn't change the task name or description. Consider changing these fields to suit the new task type.

## Connect tasks

[NOTE: Add note or important bubble to inform that connectors don't do any acutual data connections - they are graphic representations of the flow of tasks only.]

[NOTE: Add tip: arrange the tasks on the canvas they way you want them to appear before connecting them. Connected tasks maintain their arrangement when you add new tasks to the canvas. Unconnected tasks get rearranged vertically every time you add a new task.]

Up this point, the tasks are arranged vertically and separately on the canvas.

To illustrate the flow of work, you can connect the tasks. To connect two tasks, select the edge of the starting task and drag to an edge of the next task.

:::image type="content" source="./media/task-flow-work-with/connecting-two-tasks-select-drag.png" alt-text="Screenshot showing how to create a connector via select and drag.":::

The connector appears between the two tasks.

:::image type="content" source="./media/task-flow-work-with/connector-between-two-tasks.png" alt-text="Screenshot showing a connector between two tasks.":::

Alternatively, you can select **Add** > **Connector**.

:::image type="content" source="./media/task-flow-work-with/connecting-two-tasks-add-menu.png" alt-text="Screenshot showing how to create a connector using the add menu.":::

Then, in the **Add connector** dialog, select the start and end tasks, then select **Add**.

:::image type="content" source="./media/task-flow-work-with/connecting-two-tasks-add-connector-dialog.png" alt-text="Screenshot showing how to specify the start and end tasks in the add connector dialog.":::

Repeat these steps to add connectors between the other tasks.

To delete a connector or to update its start and end values, select the connector. The **Connector details** side pane allows you to delete the connector or change its start and end values.

:::image type="content" source="./media/task-flow-work-with/connector-details-pane.png" alt-text="Screenshot showing how to delete or edit a connector on the connector details pane.":::

## Assign items to a task

Once the task flow is set up, you can assign items to individual tasks for logically structuring and organizing your work. You can create a new item or assign items that already exist in the workspace.

### Create an new item for a task

To create a new item for a specific task, select **+ New item** on the task. On the **Create an item** pane that opens, the recommended item types for the task are displayed by default. Choose one of the recommended types. If you don't see the item type you want, change the **Display** selector from *Recommended items* to *All items*. Choose the item type you want.

:::image type="content" source="./media/task-flow-work-with/create-item-for-task.png" alt-text="Screenshot showing how to create a new item for a task.":::

Once the item is created, the item count on the task shows that the task has had an item assigned to it, and the item shows up in the items list. Note that the task column in the item list indicates the task the item is assigned to, if any. 

:::image type="content" source="./media/task-flow-work-with/new-item-assigned-to-task.png" alt-text="Screenshot showing a new item in the items list and the incremented item count on the task." lightbox="./media/task-flow-work-with/new-item-assigned-to-task.png":::

### Attach existing items to a task

To attach existing items to a task, select the clip icon on the task.

:::image type="content" source="./media/task-flow-work-with/assign-existing-task-clip-icon.png" alt-text="Screenshot showing the assign existing items clip icon.":::

In the **Assign item** dialog box that opens, hover over item you want to assign to the task and mark the checkbox. You can assign more than one item. When done choosing the items you want to assign to the task, choose **Select** to attach the selected items to the task.

:::image type="content" source="./media/task-flow-work-with/assign-existing-item-dialog.png" alt-text="Screenshot showing the Assign item dialog.":::

The items you selected items are assigned to the task and listed in the items list.

### Detach items from tasks

You can detach items from a selected task or detach items from all tasks.

> [!NOTE]
> Detaching items from tasks does not remove the items from the workspace.

#### Detach items from a task

To unassign items from a task, first select the task you want to remove the items from. This filters the item list to show just the items that are assigned to the task. Next, in the item list, hover over the items you want to unassign and then mark the checkboxes that apppear. Finally, on the workspace toolbar, choose **Unassign from task**.

:::image type="content" source="./media/task-flow-work-with/unassign-items-from-task.png" alt-text="Screenshot illustrating how to unassign items from a task.":::

#### Detach items from all tasks

You can also detach multiple items that are attached to different tasks at once.

To unassign multiple items from multiple tasks, select **Clear all** at the top of the items list to clear all filters so that all items in the workspace are visible. Next hover over the items you want to unassign and mark the checkboxes. When you've finished making your selections, select **Unassign from all tasks** in the workspace toolbar.

:::image type="content" source="./media/task-flow-work-with/unassign-items-from-all-tasks.png" alt-text="Screenshot showing how to unassign items from all tasks." lightbox="./media/task-flow-work-with/unassign-items-from-all-tasks.png":::

[QUESTION: Can an item only be assigned to one task at a time?]

## Delete a task

To delete a task, select it to open the task details side pane, and then select the trash can icon.

:::image type="content" source="./media/task-flow-work-with/delete-task.png" alt-text="Screenshot showing how to delete a task.":::

Alternatively, select the task flow canvas to open the task flow details pane. Then in the task flow details pane, hover over the task you want to delete in the Tasks list and select the trash can icon.

:::image type="content" source="./media/task-flow-work-with/delete-task-via-task-flow-details-pane.png" alt-text="Screenshot showing how to delete a task from the task flow details pane.":::

## Navigate items with task flows

With items assigned to the tasks, you can use the task flow to quickly understand how items in the workspace work together and get a clear view of your work in the workspace.

* For each item that you see in the items list, you can see the item type as well as what task it is assigned to, if any.

    :::image type="content" source="./media/task-flow-work-with/navigate-with-task-flow.png" alt-text="Screenshot illustrating how to use the task flow to navigate the item list.":::

* When you select a task, the items list is filtered to show only the items that are assigned to that task.

    :::image type="content" source="./media/task-flow-work-with/filter-item-list.png" alt-text="Screenshot illustrating how to filter the item list by selecting a task.":::

[QUESTION: Can you clarify what you mean by "understand how they work together, and "get a clear view of your work in the workspace. To mean, I understand that selecting a task filters the items to those that are in the task. Can you state more precisely how this helps you understand your work?] 

## Delete a task flow

Deleting the task flow will only delete all the tasks and any associations between the items and the tasks.

[QWESTION: What do you mean by "associations between the items and the tasks? Do you mean assignments?]

To delete a task flow, first select a blank area of the canvas to display the task flow pane. Next, select the trash icon to delete the task flow.

:::image type="content" source="./media/task-flow-work-with/delete-task-flow.png" alt-text="Screenshot showing how to delete a task flow.":::

Deleting a task flow deletes all tasks, the task list, and any item assignments.

Any items created will remain in the workspace, but you need to assign them to tasks in your new task flow.

## Related concepts

* [Task flow overview](./task-flow-overview.md)
* [Task flow concepts](./task-flow-concepts.md)
* [Set up a task flow](./task-flow-create.md)