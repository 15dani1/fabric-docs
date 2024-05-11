---
title: Fabric task flows overview
description: This article gives an overview of task flows and task flow terminology.
ms.reviewer: liud
ms.author: painbar
author: paulinbar
ms.topic: conceptual
ms.date: 04/05/2024
---

# What is a Fabric task flow?

A Fabric task flow is a visualization of the logical structure of your work in the workspace. Fabric provides a range of predefined, end-to-end task flows based on industry best practices that are intended to make it easier to get started with your project. In addition, you can customize the task flows to suit your specific needs and requirements. This enables you to create a tailored solution that meets your unique business needs and goals.

With task flows, you can understand how items are connected and work together in your workspace. This makes it easier for you to navigate your workspace, even as it becomes more complex over time. Moreover, you can easily standardize your team's work and keep your design and development work in sync to boost the team's collaboration and efficiency.  

## Terms

* **Task flow**: A task flow is a collection of connected tasks that represent relationships in a process or collection of processes that complete an end-to-end data solution.

* **Task**: A task is a unit of process in the task flow. On a task, it provides task type and item recommendations to help you select the appropriate item and allows you to create and attach items to tasks, as well as to navigate items.

## Task types

Each task has a task type that classifies the task based on its key capabilities in the data process flow. The predefined task types are:

| Task type | Description |
|:--------|:----------|
| **General** | Create tasks customized to your project needs and associate available item types with them. |
| **Get data** | Ingest both batch and real-time data into a single location within your Fabric workspace. |
| **Store data** | Organize, query, and store your ingested data in an easily retrievable format. |
| **Prepare data** | Prepare your data for analysis or modeling by addressing issues with the data, such as duplicates, missing values, formatting, etc. |
| **Analyze and train data** | Analyze and use your newly structured data to build and train machine learning models to make decisions and predictions. |
| **Track data** | Take actions, such as sending automated emails or notifications, on the insights that your data provides. |
| **Visualize data** | Present your data as rich visualizations and insights that can be shared with others. |

* **Get data**: Ingest both batch and real-time data into a single location within your Fabric workspace.
* **Clean and transform data**: Prepare your data for analysis or modeling by addressing issues with the data, such as duplicates, missing values, formatting, etc.
* **Store and query data**: Organize, query, and store your ingested data in an easily retrievable format.
* **Analyze and model data**: Analyze and use your newly structured data to build and train machine learning models to make decisions and predictions.
* **Visualize data**: Present your data as rich visualizations and insights that can be shared with others.
* **Respond to data**: Take actions, such as sending automated emails or notifications, on the insights that your data provides.
* **General**: Create tasks customized to your project needs and associate available item types with them.

## Set up a task flow in a workspace

Open the workspace, you can see the **Task flow (preview)** tab in workspace page, where you can build task flow and manage items. You can also select the **All items and folders** and back to the item list view.  

![A screenshot of a computer  Description automatically generated1](./media/task flow-overview/image4.png)

To build a task flow, you can either select a task flow from one of predesigned task flows or add a task to start building one yourself.  

## Start with predesigned task flows

In the task flow default page, you can see the option of **Select a task flow**

![A screenshot of a computer  Description automatically generated2](./media/task flow-overview/image5.png)

By clicking it, you can open and browse the predesigned task flows provided by Microsoft. It lists eight task flows with descriptions about each task flow and item types used in each task flow, which gives a high level view of the task flows and how it's used.

The layout and content are listed here and discussed in more detail later.

![A screenshot of a computer  Description automatically generated3](./media/task flow-overview/image6.png)

1. Task flow name 
1. Briefly description of the use case of task flow 
1. Total number of tasks in this task flow 
1. More detailed description of the task flow and how it's used
1. Item types that are used in task flow 

You can select one that can best fit your project needs by clicking **Select.** And the selected task flow is applied into the task flow canvas.

![A screenshot of a computer  Description automatically generated4](./media/task flow-overview/image7.png)

The layout of the task flow view is:

1. Canvas: The canvas contains a graph view of tasks and all interactions of task flow.
1. Task flow details pane: detailed information of the task flow, including name, description, total number of tasks and task list.
1. Item list: which includes items that are attached with tasks in this task flow

You can also update the task flow name and description in task flow details pane by clicking **Edit** .

![A group of rectangular boxes with text  Description automatically generated5](./media/task flow-overview/image8.png)

The details section is in editing mode now. You can edit name and description and save the update by clicking **Save** . 

![A diagram of a diagram  Description automatically generated with medium confidence6](./media/task flow-overview/image9.png)

## Start with a custom task flow

If you already have a clear view of your taskflow, or none of the predesigned task flows fit with your needs, you can choose to build a custom task flow by selecting a task type and adding a task directly into a canvas. 

![A screenshot of a computer  Description automatically generated7](./media/task flow-overview/image10.png)

The task is added into the canvas then. And the task flow is initiated in this workspace now.  Select **Edit** to update task flow name and descriptions to help other members in this workspace to understand the task flow and your project.

![A white background with a black and white flag  Description automatically generated with medium confidence8](./media/task flow-overview/image11.png)

You can continue to add other tasks, link tasks and manage tasks on canvas, which will be discussed in more detail later.

## Task management in task flows

When you select a task by clicking on it, you can see the **Task details**. 

![A white background with a black and white flag  Description automatically generated with medium confidence9](./media/task flow-overview/image12.png)

There are five parts in the Task details pane:

1. Task name, identifying a task and providing a clear indication of its intended use
1. This is an overview of task type and the number of items attached to it.
1. Task description, it provides a detailed explanation of the task and its intended use.
1. Task type, by configuring and selecting task type, the specific category of the recommended items are different.
1. Item recommendation: recommended items vary depending on the selected task type.

### Update task details and type

**When adding a task, the system task type and its associated description are assigned as the default name and description** **to the task. You can update the task name and description by clicking** **Edit details.**

![A white background with black and white clouds  Description automatically generated with medium confidenceA](./media/task flow-overview/image13.png)

**The details section is in editing mode now. You can edit name and description and save the update by clicking** **Save .** 

![A white background with black and white clouds  Description automatically generated with medium confidenceB](./media/task flow-overview/image14.png)

To update or reset the task type for an existing task, simply select on the dropdown menu and choose a new type.

![A white rectangular object with a black border  Description automatically generated with medium confidenceC](./media/task flow-overview/image15.png)

### Add tasks

To add more tasks into canvas, you can select **Add** and select a task type in the drop-down list. 

![A white rectangular object with a black border  Description automatically generatedD](./media/task flow-overview/image16.png)

The task of the selected task type is added into the canvas. You can also update the name and description of the task.  

![A white background with black and white text  Description automatically generated with medium confidenceE](./media/task flow-overview/image17.png)

Repeat the previous steps and add more tasks into the canvas.

### Link tasks

Currently, the tasks are arranged vertically and separately on the canvas.

![A white background with black and white clouds  Description automatically generated with medium confidenceF](./media/task flow-overview/image18.png)

To link tasks on the canvas, you can select **Add** and select **Link**.

![Alttext1](./media/task flow-overview/image19.png)

In the new dialog box, choose the **Start task** and **End task** options accordingly, then select on **Add** to create the link.

![Alttext2](./media/task flow-overview/image20.png)

Repeat this step to add links between other tasks.

![A screenshot of a computer  Description automatically generatedG](./media/task flow-overview/image21.png)

By selecting and clicking on a link on the canvas, you can view the **Link details** and update the link or delete the link as needed.

![Alttext3](./media/task flow-overview/image22.png)

### Delete a task

To delete a task, first select it by clicking on it. Then, in the Task Details pane, you can find the **Delete** button to remove the task.

![Alttext4](./media/task flow-overview/image23.png)

## Attach and detach items with a task

Once the task flow is set up, you can attach items to individual tasks for logically structuring and organizing your work. You can choose to create a new item or attach existing items from the many already saved to the workspace. 

### Create an item on a task

To create a new item for a specific task, first select the task by clicking on it. Then, select on the clip icon located on the task, and select **New item** to open the item creation panel for creating a new item.

![Alttext15](./media/task flow-overview/image24.png)

Alternatively, you can select the **Attach item** in the header of the bottom list to select **New item** and open the item creation panel.

![Alttext6](./media/task flow-overview/image25.png)

The recommended items are displayed by default in the creation panel. If the item you need isn't listed, you can select 'All items' in the display option to view the full list of the items. In the creation panel, select the item and create the item. Once the item is created, it's listed in the bottom list of the page. The task also shows that it has one item attached to it.

![Alttext7](./media/task flow-overview/image26.png)

![Alttext8](./media/task flow-overview/image27.png)

### Attach existing items to a task

To attach existing items, you can either select on the clip icon on task or select the **Attach item** in the header of the bottom list, and select **Existing item**. 

![A group of rectangular boxes with text  Description automatically generated with medium confidenceH](./media/task flow-overview/image28.png)

In the dialog box, select one or multiple items at once and select **Select** to attach selected items to the task. 

![Alttext9](./media/task flow-overview/image29.png)

You can see the selected items are attached to the task and listed in the bottom list. 

### Detach items from task

You can detach items from a selected task or detach items from all tasks. 

#### Detach items from a task

To detach item(s) from a task, first select the task you want to remove the item from. Second, select the item(s) in the bottom list. Then, select on **Detach from task** in the list header to detach the item(s) from the task.

![AlttextA](./media/task flow-overview/image30.png)

#### Detach items from all tasks

You can also detach multiple items that are attached to different tasks at once. When no step is selected in the task flow, you can view all the items in the task flow. Select the items and select **Detach from all tasks** button to detach items from tasks. 

![AlttextB](./media/task flow-overview/image31.png)

## Navigate items with task flows

With items attached to the tasks, you can use task flow to quickly understand how items in the workspace work together and get a clear view of your work in the workspace. 

![AlttextC](./media/task flow-overview/image32.png)

Clicking on each task in the task flow, you can only view the items attached to the task. 

![AlttextD](./media/task flow-overview/image33.png)

## Delete a task flow

Deleting the task flow will only delete all the tasks and any associations between the items and the tasks. 

To delete a task flow, first select on a blank area of the canvas to ensure that no tasks are selected. This makes the task flow pane visible. Next, locate the '...' in the top right corner of the pane and select on it. Then select **Delete** **task flow** to delete the task flow.

![AlttextE](./media/task flow-overview/image34.png)

Select **Delete** to delete the task flow from current workspace. 

![AlttextF](./media/task flow-overview/image35.png)

## Private preview limitations

The private preview of external data sharing has certain limitations that you should be aware of.

* Please note that tasks’ positions can't be saved on canvas. Whenever a new task is added, all tasks on the canvas will be reset to their default positions.
* Keyboard interactions aren't supported.
* Dragging link on the canvas isn't supported.
* Creation of Report and Dataflow Gen2 from tasks aren't supported in task flowa.

## Related content