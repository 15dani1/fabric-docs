---
title: Overview of Fabric git integration 
description: An introduction to git integration the Fabric Application lifecycle management (ALM) tool
author: mberdugo
ms.author: monaberdugo
ms.reviewer: NimrodShalit
ms.topic: conceptual
ms.custom: contperf-fy21q1, build-2023
ms.date: 05/30/2023
ms.search.form: 
---

# Introduction to git integration

[!INCLUDE [preview-note](../../includes/preview-note.md)]

> [!NOTE]
> This articles in this section are about version control using git integration. To manage deployment of your app, see the [deployment pipelines](../deployment-pipelines/intro-to-deployment-pipelines.md) documentation.

Git integration in Microsoft Fabric enables developers to integrate their development processes, tools, and best practices straight into the Fabric platform. It allows developers who are developing in Fabric to:

* Backup and version their work
* Revert to previous stages as needed
* Collaborate with others or work alone using Git branches
* Leverage the capabilities of familiar source control tools to manage Fabric items.

:::image type="content" source="./media/intro-to-git-integration/git-flow.png" alt-text="Flowchart showing the connection between the remote git repo and the Fabric workspace.":::

The integration with source control is on a workspace level. Developers can version items they develop within a workspace in a single process, with full visibility to all their items. Currently, in Preview, only a few items are supported, but the list of [supported items](#supported-items) is growing.

* Read up on [version control](/devops/develop/git/what-is-version-control) and [Git](/devops/develop/git/what-is-git) to make sure you’re familiar with basic git concepts.  

* Read more about the [git integration process](./git-integration-process.md).

* Read about the best way to manage your [git branches](./manage-branches.md).

## Privacy concerns

Before you enable git integration, make sure you understand the following possible privacy concerns:

* [Azure DevOps Services Data protection overview](/azure/devops/organizations/security/data-protection)
* [Microsoft privacy statement](https://go.microsoft.com/fwlink/?LinkId=521839)
<!--- * [Microsoft services agreement](https://www.microsoft.com/servicesagreement/default.aspx) -->

## Supported items

The following items are currently supported:

* Reports (except paginated reports)
* Datasets (except push datasets, live connections, and model v1)

If the workspace or git directory has unsupported items, it can still be connected, but the unsupported items are ignored. They aren’t saved or synced, but they’re not deleted either. They appear in the source control pane but you can't commit or update them.

<!--
## Workflow

A typical workflow for a developer using Fabric git integration may look like this:

1. [Connect](./git-get-started.md#connect-a-workspace-to-an-azure-repo) the Fabric developer workspace to a Git repository
1. Checkout branch
1. [Edit and commit](./git-get-started.md#commit-changes-to-git) changes​
1. Start a pull request and merge changes to ‘main’ branch​
1. [Update](./git-get-started.md#update-workspace-from-git) the IT developer workspace
1. [Resolve conflicts](./conflict-resolution.md)
-->

## Considerations and limitations

* Currently, only [Git in Azure Repos](/en-us/azure/devops/user-guide/code-with-git) is supported.  
* If the workspace and git repo are in two different geographical regions, [cross-geo exports must be enabled](../../admin/git-integration-admin-settings.md#enable-git-actions-on-workspaces-residing-in-other-geographical-locations) by the tenant admin.  
* Azure DevOps **on-prem** is not supported.

## Next steps

* [Get started with git integration](./git-get-started.md)
* [Understand the git integration process](./git-integration-process.md)
