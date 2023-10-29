---
title: Service tags
description: Learn how to use service tags in Microsoft Fabric.
author: KesemSharabi
ms.author: kesharab
ms.topic: concept-article
ms.custom: build-2023
ms.date: 10/29/2023
---

# Service tags

[!INCLUDE [preview-note](../includes/preview-note.md)]

You can use Azure [service tags](/azure/virtual-network/service-tags-overview) to enable connections to and from Microsoft Fabric. In Azure, a service tag is a defined group of IP addresses that you can configure to be automatically managed, as a group, to minimize the complexity of updates or changes to network security rules.

## Which service tags are supported?

In Microsoft Fabric, you can use the service tags listed in the table below. There's no service tag for untrusted code which is used in Data Engineering items.

| Tag | Purpose | Can use inbound or outbound? | Can be regional? | Can use with Azure Firewall? |
|--|--|--|--|--|
| DataFactory | Azure Data Factory | Both | No | Yes |
| EventHub | Azure Event Hubs | Outbound | Yes | Yes |
| PowerBI | Power BI and Microsoft Fabric | Both | No | Yes |
| PowerQueryOnline | Power Query Online | Both | No | Yes |
| KustoAnalytics | Real-Time Analytics | Both | No | No |

## How to enable service tags?

To enable service tags in Fabric, you can follow the instructions in [Use service tags with Power BI](/power-bi/enterprise/service-premium-service-tags).

You can also follow the example in this section, for enabling service tags in SQL Managed Instance.

1. [Enable a public endpoint](/power-bi/enterprise/service-premium-service-tags#enable-a-public-endpoint) in the SQL Managed Instance.

2. [Create a Network Security Group rule](/power-bi/enterprise/service-premium-service-tags#create-a-network-security-group-rule) to allow inbound traffic.

3. [Enter the credentials](/power-bi/enterprise/service-premium-service-tags#enter-the-credentials-in-power-bi) in Microsoft Fabric.

## Next steps

* [Private endpoints](/power-bi/enterprise/service-security-private-links)

* [Azure IP Ranges and Service Tags – Public Cloud](https://www.microsoft.com/download/details.aspx?id=56519)
