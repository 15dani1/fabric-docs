---
title: Data science lineage
description: Track relationships between data science artifacts
ms.reviewer: mopeakande
ms.author: midesa
author: midesa 
ms.topic: conceptual
ms.date: 04/24/2023
---

# Lineage for models and experiments

In modern business intelligence (BI) projects, understanding the flow of data from the data source to its destination can be a challenge. The challenge is even bigger if you've built advanced analytical projects spanning multiple data sources, artifacts, and dependencies. Questions like "What happens if I change this data?" or "Why isn't this report up to date?" can be hard to answer. They might require a team of experts or deep investigation to understand. The Fabric lineage view helps you answer these questions.

[!INCLUDE [preview-note](../includes/preview-note.md)]

## Lineage and machine learning

There are several reasons why lineage is important in your machine learning workflow:

- **Reproducibility**: Knowing the lineage of a model makes it easier to reproduce the model and its results. If someone else wants to replicate the model, they can follow the same steps that were used to create it, and use the same data and parameters.
- **Transparency**: Understanding the lineage of a model helps to increase its transparency. This means that stakeholders, such as regulators or users, can understand how the model was created, and how it works. This can be important for ensuring fairness, accountability, and ethical considerations.
- **Debugging**: If a model is not performing as expected, knowing its lineage can help to identify the source of the problem. By examining the training data, parameters, and decisions that were made during the training process, it may be possible to identify issues that are affecting the model's performance.
- **Improvement**: Knowing the lineage of a model can also help to improve it. By understanding how the model was created and trained, it may be possible to make changes to the training data, parameters, or process that can improve the model's accuracy or other performance metrics.

## Data science artifact types

In Fabric, machine learning models and experiments are integrated into a unified platform. As part of this, users can browse the relationship between Fabric Data Science artifacts and other Fabric artifacts.

:::image type="content" source="media/data-science-overview/lineage-data-science.gif" alt-text="Gif showing lineage view for models and experiments." lightbox="media/data-science-overview/lineage-data-science.gif":::

### Machine learning models

In  Fabric, users can create and manage machine learning models. A machine learning model artifact represents a versioned list of models, allowing the user to browse the various iterations of the model.

In the lineage view, users can browse the relationship between a machine learning model and other Fabric artifacts to answer the following questions:

- What is the relationship between machine learning models and experiments within my workspace?
- Which machine learning models exist in my workspace?
- How can I trace back the lineage to see which Lakehouse artifacts were related to this model?

### Machine learning experiments

A machine learning *experiment* is the primary unit of organization and control for all related machine learning runs.

In the lineage view, users can browse the relationship between a machine learning experiment and other Fabric artifacts to answer the following questions:

- What is the relationship between machine learning experiments and code artifacts (e.g. notebooks and Spark Job Definitions) within my workspace?
- Which machine learning experiments exist in my workspace?
- How can I trace back the lineage to see which Lakehouse artifacts were related to this experiment?

## Explore lineage view

Every Fabric workspace automatically has a built-in lineage view. To access this view, you must have at least the **Contributor** role within the workspace. To learn more about permissions in Fabric, you can visit the documentation on [permissions for models and experiments](../data-science/models-experiments-rbac.md).

To access the lineage view:

1. Select your Fabric workspace and then navigate to the workspace list.

  :::image type="content" source="media/lineage/artifact-workspace-list-view-data-science.png" alt-text="Image showing workspace list view in Fabric." lightbox="media/lineage/artifact-workspace-list-view-data-science.png":::

2. Switch from the workspace **List** view to the Workspace **Lineage** view.

  :::image type="content" source="media/lineage/workspace-artifact-lineage-data-science.png" alt-text="Image showing workspace lineage view in Fabric." lightbox="media/lineage/workspace-artifact-lineage-data-science.png":::

3. You can also navigate to **Lineage** view for a specific artifact by opening the related actions.

   :::image type="content" source="media/lineage/artifact-lineage-view-data-science.png" alt-text="Image showing workspace lineage view in Fabric for a given artifact." lightbox="media/lineage/artifact-lineage-view-data-science.png":::

## Next steps

- Learn about machine learning models: [Machine learning models](./machine-learning-model.md)
- Learn about machine learning experiments: [Machine learning experiments](./machine-learning-experiment.md)