---
title: Fabric Autologging
description: Use autologging with MLflow to automatically capture machine learning metrics and parameters 
ms.reviewer: mopeakande
ms.author: midesa
author: midesa 
ms.topic: conceptual
ms.date: 05/23/2023
---

# Fabric autologging

Synapse Fabric autologging significantly reduces the amount of code required to capture machine learning metrics and parameters during the model training process. Synapse Fabric autologging automatically logs the parameters, metrics, and artifacts of a machine learning model during training. This feature extends [MLflow autologging](https://mlflow.org/docs/latest/tracking.html#automatic-logging) capabilities and is deeply integrated into the Microsoft Fabric experience. Using this, developers and data scientists can easily track and compare the performance of different models and experiments without the need for manual tracking.

## How it works

Synapse Fabric autologging works by automatically capturing the values of input parameters, output metrics, and output artifacts of a machine learning model as it is being trained. This information is then logged to your Fabric workspace, where it can be accessed and visualized using the MLFlow APIs or the corresponding experiment & model artifacts in your Fabric workspace.

The default configuration for the notebook [mlflow.auotolog()](https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.autolog) hook is:

```python
mlflow.autolog(
    log_input_examples=False,
    log_model_signatures=True,
    log_models=True,
    disable=False,
    exclusive=True,
    disable_for_unsupported_versions=True,
    silent=True
)
```

When you launch a notebook, Microsoft Fabric calls [mlflow.autolog()](https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.autolog) to instantly set up the tracking and load the corresponding dependencies. As you train models in your notebook, this model information is automatically tracked with MLflow. This configuration is done automatically behind the scenes when you run ```import mlflow```.

### Supported frameworks

Autologging supports a wide range of machine learning frameworks, including TensorFlow, PyTorch, Scikit-learn, and XGBoost. It can capture a variety of metrics, including accuracy, loss, and F1 score, as well as custom metrics defined by the user. To learn more about the framework specific properties that are captured, you can visit [MLflow documentation](https://mlflow.org/docs/latest/tracking.html#automatic-logging).

## Customize logging behavior

To customize the logging behavior, you can use the [mlflow.autolog()](https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.autolog) configuration. This provides the parameters to enable model logging, collect input samples, configure warnings, or even enable logging for user-specified content.

### Track additional content

You can update the autologging configuration to track additional metrics, parameters, files, and metadata with runs created with MLflow. 

To do this:

1. Update the [mlflow.autolog()](https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.autolog) call and set ```exclusive=False```.

    ```python
        mlflow.autolog(
        log_input_examples=False,
        log_model_signatures=True,
        log_models=True,
        disable=False,
        exclusive=False, # Update this property to enable custom logging
        disable_for_unsupported_versions=True,
        silent=True
    )
    ```

2. Use the MLflow tracking APIs to log additional [parameters](https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.log_param) and [metrics](https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.log_metric). This will allow you to capture your custom metrics and parameters, while also allowing you to leverage autologging to capture additional properties.

For instance:
```python
import mlflow
mlflow.autolog(exclusive=False)

with mlflow.start_run():
  mlflow.log_param("parameter name", "example value")
  # <add model training code here>
  mlflow.log_metric("metric name", 20)
```

### Disable Fabric autologging

Fabric autologging can be disabled for a specific notebook session or across all notebooks using the workspace setting.

>[!NOTE]
> If autologging is disabled, users must manually log their own [parameters](https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.log_param) and [metrics](https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.log_metric) using the MLflow APIs.

### Disable autologging for a notebook session

To disable Fabric autologging in a notebook session, you can call [mlflow.autolog()](https://mlflow.org/docs/latest/python_api/mlflow.html#mlflow.autolog) and set ```disable=True```.

For example:

```python
import mlflow
mlflow.autolog(disable=True)
```

### Disable autologging for the workspace

Workspace administrators can enable or disable Synapse Fabric autologging for all sessions across their workspace.

To do this:

1. Navigate to your Microsoft Fabric workspace and select the Workspace Settings.

:::image type="content" source="./media/machine-learning-experiment/autologging-workspace-setting.png" alt-text="Screenshot of the Data science artifact page." lightbox="./media/machine-learning-experiment/autologging-workspace-setting.png":::

2. Withing the **Data Engineering/Science** tab, select **Spark compute**. Here, you will find the setting to enable or disable Synapse Fabric autologging.

:::image type="content" source="./media/machine-learning-experiment/autologging-setting-2.png" alt-text="Screenshot of the Data science Workspace setting for autologging." lightbox="./media/machine-learning-experiment/autologging-setting-2.png":::

## Next steps

- Train a Spark MLlib model with autologging: [Train with Spark MLlib](./model-training/fabric-sparkml-tutorial.md)
- Learn about machine learning experiments in Microsoft Fabric: [Experiments](./machine-learning-experiment.md)