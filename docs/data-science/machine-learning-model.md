---
title: Machine learning model
description: Learn how to create machine learning models, manage versions within a model, track models, and apply a model.
author: midesa
ms.reviewer: franksolomon
ms.topic: conceptual
ms.custom: build-2023
ms.date: 10/17/2023

ms.search.form: Create New Model, Model Comparison
---

# Machine learning model in Microsoft Fabric

A machine learning (ML) model is a file trained to recognize certain types of patterns. You train a model over a set of data, and you provide it with an algorithm that uses to reason over and learn from that data set. After you train the model, you can use it to reason over data that it never saw before, and make predictions about that data.

[!INCLUDE [preview-note](../includes/preview-note.md)]

In [MLflow](https://mlflow.org/), an ML model can include multiple model versions. Here, each version can represent a model iteration. In this article, you learn how to interact with ML models to track and compare model versions.

## Create an ML model

In MLflow, machine learning models include a standard packaging format. This format allows use of those models in various downstream tools, including batch inferencing on Apache Spark. The format defines a convention to save a model in different “flavors” that different downstream tools can understand.

The user experience can directly create an ML model from the user experience. The MLflow API can also directly create an ML model.

To create an ML model from the user experience, you can:

1. Create a new data science workspace, or select an existing data science workspace.
1. From the **+ New** dropdown, select **Model**. This creates an empty model in your data science workspace.

   :::image type="content" source="media/machine-learning-model/new-drop-down-menu.png" alt-text="Screenshot showing the New drop-down menu." lightbox="media/machine-learning-model/new-drop-down-menu.png":::

3. After model creation, you can start adding model versions to track run metrics and parameters. Register or save experiment runs to an existing model.

You can also create a machine learning experiment directly from your authoring experience with the `mlflow.register_model()` API. If a registered ML model with the given name doesn't exist, the API creates it automatically.

```python
import mlflow

model_uri = "runs:/{}/model-uri-name".format(run.info.run_id)
mv = mlflow.register_model(model_uri, "model-name")

print("Name: {}".format(mv.name))
print("Version: {}".format(mv.version))
```

## Manage versions within an ML model

A machine learning model contains a collection of model versions for simplified tracking and comparison. Within a model, a data scientist can navigate across various model versions to explore the underlying parameters and metrics. Data scientists can also make comparisons across model versions to identify whether or not newer models might yield better results.

### Track ML models

A machine learning model version represents an individual model that has been registered for tracking.

:::image type="content" source="media/machine-learning-model/ml-model-version-tracking.png" alt-text="Screenshot showing the details screen of a model." lightbox="media/machine-learning-model/ml-model-version-tracking.png":::

Each model version includes the following information:

- **Time Created**: Date and time of model creation.
- **Run Name**: The identifier for the experiment runs used to create this specific model version.
- **Hyperparameters**: Hyperparameters are saved as key-value pairs. Both keys and values are strings.
- **Metrics**: Run metrics saved as key-value pairs. The value is numeric.
- **Model Schema/Signature**: A description of the model inputs and outputs.
- **Logged files**: Logged files in any format. For example, you can record images, environment, models, and data files.

### Compare and filter ML models

To compare and evaluate the quality of machine learning model versions, you can compare the parameters, metrics, and metadata between selected versions.

#### Visually compare ML models

You can visually compare runs within an existing model. This allows easy navigation between, and sorts across, multiple versions.

:::image type="content" source="media/machine-learning-model/visual-compare-model-runs.png" alt-text="Screenshot showing a list of runs for comparison." lightbox="media/machine-learning-model/visual-compare-model-runs.png":::

To compare runs, you can:

1. Select an existing machine learning model that contains multiple versions.
1. Select the **View** tab, and then navigate to the **Model list** view. You can also select the option to **View model list** directly from the details view.
1. You can customize the columns within the table. Expand the **Customize columns** pane. From there, you can select the properties, metrics, and hyperparameters that you want to see.
1. Lastly, you can select multiple versions, to compare their results, in the metrics comparison pane. From this pane, you can customize the charts with changes to the chart title, visualization type, X-axis, Y-axis, and more.

#### Compare ML models using the MLflow API

Data scientists can also use MLflow to search among multiple models saved within the workspace. Visit the [MLflow documentation](https://www.mlflow.org/docs/latest/python_api/mlflow.html) to explore other MLflow APIs for model interaction.

```Python
from pprint import pprint

client = MlflowClient()
for rm in client.list_registered_models():
    pprint(dict(rm), indent=4)
```

## Apply ML models

Once you train a model on a data set, you can apply that model to data it never saw to generate predictions. We call this model use technique **scoring** or **inferencing**. For more information about [!INCLUDE [product-name](../includes/product-name.md)] model scoring, see the next section.

## Next steps

- [Learn about MLflow Experiment APIs](https://www.mlflow.org/docs/latest/python_api/mlflow.html)
