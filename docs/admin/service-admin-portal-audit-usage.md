---
title: Audit and usage admin settings
description: Learn how to configure Fabric audit and usage admin settings.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.custom: tenant-setting
ms.topic: how-to
ms.date: 08/29/2023
LocalizationGroup: Administration
---

# Audit and usage tenant settings

These settings are configured in the tenant settings section of the Admin portal. For information about how to get to and use tenant settings, see [About tenant settings](/power-bi/admin/service-admin-portal-about-tenant-settings).

## Usage metrics for content creators

When this setting is on, users in the organization can see usage metrics for dashboards, reports, and datasets for which they have appropriate permissions.

To learn more, see [Monitor usage metrics in the workspaces](/power-bi/collaborate-share/service-modern-usage-metrics).

## Per-user data in usage metrics for content creators

Per-user data is enabled for usage metrics by default. Content creator account information, such as user name and email address, is included in the metrics report. If you don't wish to gather this information for all users, you can disable the feature for specified security groups or for an entire organization. Account information for the excluded users then shows in the report as *Unnamed*.

To learn more, see [Exclude user information from usage metrics reports](/power-bi/collaborate-share/service-modern-usage-metrics#exclude-user-information-from-usage-metrics-reports).

## Azure Log Analytics connections for workspace administrators

Power BI integration with [Azure Log Analytics](/power-bi/transform-model/log-analytics/desktop-log-analytics-overview) enables Fabric administrators and Premium workspace owners to connect their Premium workspaces to Azure Log Analytics to monitor the connected workspaces.

When the switch is on, administrators and Premium workspace owners can [configure **Azure Log Analytics for Power BI**](/power-bi/transform-model/log-analytics/desktop-log-analytics-configure).

## Next steps

* [About tenant settings](/power-bi/admin/service-admin-portal-about-tenant-settings)