---
title: Create a Data workflows project in Microsoft Fabric
description: This tutorial helps you create a Data workflows in Microsoft Fabric.
ms.reviewer: abnarain
ms.author: abnarain
author: nabhishek
ms.topic: quickstart
# ms.custom:
#   - ignite-2023
ms.date: 03/25/2024
---

# Quickstart: Create a Data workflow

> [!NOTE]
> Data workflows is powered by Apache Airflow. </br> [Apache Airflow](https://airflow.apache.org/) is an open-source platform used to programmatically create, schedule, and monitor complex data workflows. It allows you to define a set of tasks, called operators, that can be combined into directed acyclic graphs (DAGs) to represent data pipelines.

Data workflows provides a simple and efficient way to create and manage Apache Airflow environments, enabling you to run data pipelines at scale with ease. In this quickstart, you create your first Data workflow and run a Directed Acyclic Graph (DAG) to familiarize yourself with the environment and functionalities of Data workflows.

## Prerequisites

Enable Apache Airflow in your Tenant.

> [!NOTE]
> Since Data workflows is in preview state, you need to enable it through your tenant admin. If you already see Data workflows, your tenant admin may have already enabled it.

1. Go to Admin Portal -> Tenant Settings -> Under Microsoft Fabric -> Expand 'Users can create and use Apache Airflow projects (preview)' section.
2. Select **Apply**.

:::image type="content" source="media/data-workflows/enable-tenant.png" lightbox="media/data-workflows/enable-tenant.png" alt-text="Screenshot to enable Apache Airflow in tenant.":::

### Create a Data workflows

1. You can use an existing workspace or [Create a new workspace](../get-started/create-workspaces.md).
2. Expand `+ New` dropdown -> Click on More Options -> Under `Data Factory` section -> Select Apache Airflow Project (preview)

   :::image type="content" source="media/data-workflows/more-options.png" lightbox="media/data-workflows/more-options.png" alt-text="Screenshot shows click on more options.":::

   :::image type="content" source="media/data-workflows/apache-airflow-project.png" lightbox="media/data-workflows/apache-airflow-project.png" alt-text="Screenshot to select Apache Airflow Project.":::

3. Give a suitable name to your project and Click on Create Button.

### Configure an Airflow Environment

1. Click on 'Configure Airflow' Card.
2. Specify the Apache Airflow environment configuration for your DAGs to run against. You can change these settings later as well.

   :::image type="content" source="media/data-workflows/configure-airflow-env.png" lightbox="media/data-workflows/configure-airflow-env.png" alt-text="Screenshot to configure Apache Airflow Project.":::

   * <strong>Compute Node Size:</strong> The size of the compute node you want your Airflow environment to run on.
   * <strong>Enable Autoscale:</strong> Allow your Airflow environment to scale nodes up or down as needed.
   * <strong>Environment variables:</strong> You can use this key value store within Airflow to store and retrieve arbitrary content or settings.
   * <strong>Configuration Overrides:</strong> You can override any Airflow configurations that you set in airflow.cfg. Examples are name: AIRFLOW__VAR__FOO and value: BAR. For more information, see Airflow configurations.
   * <strong>Kubernetes secrets:</strong> You can create a custom Kubernetes secret for your Airflow environment. An example is Private registry credentials to pull images for KubernetesPodOperator.
   * <strong>Enable Triggers:</strong> Allows the Airflow Tasks to run in deferrable mode.


### Synchronize your GitHub Repository

Specify the git repository you want to sync your Data workflows with.

1. Click on 'Sync with Git' Card, you are navigated to 'File Storage'.

:::image type="content" source="media/data-workflows/git-sync.png" lightbox="media/data-workflows/git-sync.png" alt-text="Screenshot to synchronize GitHub repository.":::

2. Fill out the following fields:

* <strong>Git service type</strong>: Supported service types:
    * GitHub
    * ADO: Azure DevOps
    * GitLab
    * BitBucket

* <strong>Git Credential type</strong>: Supported credential types:
    * None: Choose this credential type, if the repository is public.
    * Personal Access token: A personal access token from the Git service used to authenticate with repository.
      * Fill out the fields:
         * Username: Username of GitHub.
         * Personal Access token
    * Service Principal: Select this credential when you choose Git Service as Azure Devops:
        * Fill out the fields:
            * Service principal app ID: Client ID of your Service Principal that has access to Azure Devops Repository.
            * Service principal secret: Client secret with access to Azure DevOps repository.
            * Service principal tenant ID: Tenant ID of your Service Principal.

* <strong>Repo</strong>: The clone URL to the repository you want to sync.
* <strong>Branch</strong>: Name of the repository’s branch you want to sync.

3. Click on 'Apply'.

#### Supported Git Repository Structure

```
|── dags/
|   |-- *.py
|-- plugins
|    |-- executors/
|    |   ├-- __init__.py
|    |   └-- *.py
|    |-- hooks/
|    |   ├-- __init__.py
|    |   └-- *.py
|    |-- operators/
|    |   ├-- __init__.py
|    |   └-- *.py
|    |-- transfers/
|    |   ├-- __init__.py
|    |   └-- *.py
|    |-- triggers/
|    |    ├-- __init__.py
|    |    └-- *.py
```

### Start Apache Airflow Environment

Click on Start Apache Airflow Environment to configure the Airflow Runtime. (It should take about 5 mins for the configuration).

:::image type="content" source="media/data-workflows/start-apache-airflow.png" lightbox="media/data-workflows/start-apache-airflow.png" alt-text="Screenshot to start Apache Airflow Project.":::

## Related Content

* [Install Private Package in Data workflows](data-workflows-install-private-package.md)
