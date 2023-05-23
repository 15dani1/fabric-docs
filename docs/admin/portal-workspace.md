---
title: Workspace admin settings
description: Learn how to configure workspace admin settings.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.custom: tenant-setting, build-2023
ms.topic: how-to
ms.service: azure
ms.date: 05/23/2023
LocalizationGroup: Administration
---

# Workspace tenant settings

[!INCLUDE [preview-note](../includes/preview-note.md)]

These settings are configured in the tenant settings section of the Admin portal. For information about how to get to and use tenant settings, see [About tenant settings](/power-bi/admin/service-admin-portal-about-tenant-settings).

## Create workspaces

Workspaces are places where users collaborate on dashboards, reports, and other content. [!INCLUDE [product-name](../includes/product-name.md)] admins can use the **Create workspaces** setting to designate which users in the organization can create workspaces. Admins can let everybody or nobody in an organization create workspaces. Workspace creation can also be limited to members of specific security groups. Learn more about [workspaces](../get-started/workspaces.md).

:::image type="content" source="media/portal-workspace/power-bi-admin-workspace-settings.png" alt-text="Screenshot showing Create a workspace.":::

For classic workspaces based on Microsoft 365 Groups, administration continues to occur in admin portal and Azure Active Directory.

> [!NOTE]
> The **Create workspaces** setting defaults to allowing only users who can create Microsoft 365 Groups to create the new [!INCLUDE [product-name](../includes/product-name.md)] workspaces. Be sure to set a value in the [!INCLUDE [product-name](../includes/product-name.md)] admin portal to ensure appropriate users can create them.

**List of workspaces**

The admin portal has another section of settings about the workspaces in your tenant. In that section, you can sort and filter the list of workspaces and display the details for each workspace. See [Workspaces](portal-workspaces.md) in this article for details.

**Publish content packs and apps**

In the admin portal, you also control which users have permissions to distribute apps to the organization. See [Publish content packs and apps to the entire organization](/power-bi/admin/service-admin-portal-content-pack-app#publish-content-packs-and-apps-to-the-entire-organization) in this article for details.

## Use datasets across workspaces

Admins can control which users in the organization can use datasets across workspaces. When this setting is enabled, users still need the required Build permission for a specific dataset.

:::image type="content" source="media/portal-workspace/power-bi-admin-datasets-workspaces.png" alt-text="Use datasets across workspaces":::

For more information, see [Intro to datasets across workspaces](/power-bi/connect-data/service-datasets-across-workspaces).

## Block scheduled upgrade of empty workspaces

To reduce the impact of maintaining empty classic workspaces that were automatically created, empty classic workspaces are deleted by default as part of the upgrade process. However, admins can prevent deleting empty workspaces by disabling the following setting in the Admin portal.

:::image type="content" source="media/portal-workspace/block-upgrade-empty-workspaces.png" alt-text="Screenshot of using admin portal to allow or prevent upgrade of empty workspaces.":::

Additional notes on deletion of empty workspaces:

- Only empty v1 workspaces will be deleted during upgrade. Empty v2 workspaces will not be deleted. Deletion of empty workspaces can be prevented by using the tenant setting described previously in this article.
- Office 365 groups associated with empty v1 workspaces aren't deleted. Read more about [workspaces](../get-started/workspaces.md).

## Users can reassign personal workspaces 

Personal workspaces are the My workspaces that every user has for their personal content. [!INCLUDE [product-name](../includes/product-name.md)] and capacity admins can [designate a preferred capacity for My workspaces](/power-bi/enterprise/service-admin-premium-manage#designate-a-default-capacity-for-my-workspaces). By default, however, My workspace owners can still change the capacity assignment of their workspace. If a [!INCLUDE [product-name](../includes/product-name.md)] or capacity admin designates a Premium capacity as the default capacity for My workspaces, but a My workspace owner then changes that capacity assignment back to shared capacity, this could result in non-compliance with data residency requirements.

To prevent such a scenario, the [!INCLUDE [product-name](../includes/product-name.md)] admin can turn off the **Users can reassign personal workspaces** tenant setting. When this setting is off, My workspace owners can't change the capacity assignment of their My workspace.

To turn off the setting:
1. Go to the [!INCLUDE [product-name](../includes/product-name.md)] Admin portal and select **Tenant settings**.
1. In the tenant settings, scroll down to the **Workspace settings** section.
1. Find the setting called **Users can reassign personal workspaces**. By default, this setting is on, which means that any My workspace owner can reassign their My workspace capacity. To prevent users from being able to reassign the capacity of their My workspace, turn the setting off.

For more information, see [Prevent My workspace owners from reassigning their My workspaces to a different capacity](./portal-workspaces.md#prevent-my-workspace-owners-from-reassigning-their-my-workspaces-to-a-different-capacity).

## Next steps

[About tenant settings](/power-bi/admin/service-admin-portal-about-tenant-settings)
