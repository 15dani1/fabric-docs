---
title: Fabric Workload Hub Validation Guidelines and Requirements
description: Learn about the requirements for publishing Fabric workload.
author: rasala, gesaur
ms.author: rasala, gesaur
ms.reviewer: gesaur
ms.topic: how-to
ms.custom:
ms.date: 04/17/2024
---

# Fabric Workload Hub Validation Guidelines and Requirements
This article describes in details all the functional and nonfunctional requirements that are required for a custom workload to be listed in Fabric Workload Hub. These requirements help you create a new workload with seamless user experience that will delight your customers. Make sure your workload complies with these requirements before you submit your workload for publication. 

# Business requirements
1. Building applications in Fabric is more like creating documents in office than provisioning resources in Azure. While we don’t expect every user to be able to take advantage of every workload in Fabric due to obvious skill gaps, each of the workloads must make an effort to appeal to the broadest set of users.
2. Fabric is designed to support the largest Tier 1 projects and data sizes.
3. The Fabric platform provides a common set of services that the workload shouldn't replace with their own proprietary one. The consistent use of the platform services across all the workloads ensures a consistent experience and functionality throughout the system.
4. OneLake is the storage that brings together all data into a single integrated product that includes the management of data security.
Infrastructure level security, compliance, and governance are managed by expert administrators on a tenant level.

| **Requirement Category** | **Detailed Description** | **Applicable Domain**  | **Reference Links**  |
|--| -- |--| -- |
| **Singificant value** | Your offers must provide enough value to justify the investment it takes to learn and use them. Your offer should provide significant benefits such as enhanced efficiency, innovative features, or strategic advantages. | Functional, SaaS Submission | [More information about offer value](https://learn.microsoft.com/legal/marketplace/certification-policies#1008-significant-value) |
| **Trials** | We expect that partners are providing an easy and fast trial experience on the platform. This experience should be available to the customer without waiting time (less than 5 seconds) and give the them a free and easy way to explore the offered workload. | Functional |  [More information](../monetization.md) |
| **Monetization** | Partners need to enlist a SaaS - offer within the Azure Marketplace. This offer can just be a contact-us listing to get leads from the platform. Idealy we expect partners to also transact over the Marketplace. In addition, they can build Bring your own License (BYOL) capabilities into their integration. | Functional | [More information](../monetization.md) |

# Design requirements

There are two different resources you can use to get familiar with the Design requirements for Fabric: 
 * [Fabric UX System](https://aka.ms/fabricux) This provides you with an overview of the Patterns and Components that are available in Fabric UX to accelerate your work. It also includes Fabric UX React and Angular wrapper libraries that integrate with Fluent web components.

 * [Figma File](https://www.figma.com/file/jC5Qmzuazv7TKTRVndOmOZ/Item-creation-guidance?type=design&node-id=1516-354449&mode=design&t=fT3hdhjk8nVNh4UR-0) Provides another context and guidelines on the different interaction flows within Fabric. 

| **Requirement Category** | **Detailed Description** | **Applicable Domain**  | **Reference Links**  |
|--| -- |--|--|
| **Loading Times** |  Users in fabric are expecting that the UX is loading fast. This is also a requirement for extension workloads. Independent of the technical implementation and regional hosting the extension should load fast within all Regions Fabric customers are able to use it. |  |  |



# non-Functional and SaaS Submission Requirements

Before [publishing your Software as a Service (SaaS) offer on the Azure Marketplace](https://learn.microsoft.com/partner-center/marketplace/plan-saas-offer), it's essential to prepare and meet the following requirements and the full guidelines of [the marketplace's general policies](https://learn.microsoft.com/legal/marketplace/certification-policies#100-general) and [SaaS specific policies](https://learn.microsoft.com/legal/marketplace/certification-policies#1000-software-as-a-service-saas).

> [!NOTE]
> The requirements for the Workload package metadata and the SaaS submission offer metadata should be identical to ensure consistency. The applicable domain will state "SaaS submission and Workload package metadata" to reflect this necessity.


| **Requirement Category** | **Detailed Description** | **Applicable Domain**  | **Reference Links**  |
|--|--|--|--|
| **Engineering Contact** | Engineering contact email domain must match the email domain of the publisher who reaches our team with the Workload package (step number 4 in the publishing flow article) |  SaaS submission | | 
| **Title Accuracy** | Must have accurate and descriptive title, including the seller’s name. If the offer is promoted on another website both titles should match.	| SaaS submission, Workload package metadata | [More information about the title](https://learn.microsoft.com/legal/marketplace/certification-policies#10011-title)  |
| **Concise Summary** | The summary appears in the Azure commercial marketplace search results and must be limited to 100 characters, and effectively convey the essence of the SaaS offer. | SaaS submission, Workload package metadata | [More information about the summary](https://learn.microsoft.com/legal/marketplace/certification-policies#10012-summary) |
| **Comprehensive Description** | The description should comprehensively detail any limitations, conditions, or exceptions to the functionality, features, and deliverables. It must articulate the value proposition and requirements clearly and distinctly represent the product. For non-English content, the description must start or end with the phrase, "This application is available in [languages]." | SaaS submission, Workload package metadata | [More information about the description](https://learn.microsoft.com/legal/marketplace/certification-policies#10013-description) |
| **Marketplace Visibility** | Each SaaS offer must feature at least one public plan, such as Contact Me, BYOL, or Get It Now (Transact). Private plans aren't permitted without an accompanying public plan to ensure active marketplace engagement. | SaaS Submission | [More information about the Marketplace visibility](https://learn.microsoft.com/legal/marketplace/certification-policies#10015-active-and-visible-presence) |
| **Graphic Elements** | Graphic elements must be current, and related to your offer. Logo: Appear on the offer listing page and must be uploaded as a `.png` file between 216-350 pixels square Images: must be 1280c720 pixel `.png` files. Videos: must be hosted on YouTube or Vimeo. No short URLs, "human readable" redirects may be used. | SaaS Submission | [More information about graphic elements](https://learn.microsoft.com/legal/marketplace/certification-policies#1003-graphic-elements) |
| **Pricing Model Compliance** | The pricing for the SaaS offer must align with the [marketplace-supported pricing models](https://learn.microsoft.com/azure/marketplace/plans-pricing), ensuring transparency and consistency for customers. | SaaS Submission |  [More information about pricing](https://learn.microsoft.com/legal/marketplace/certification-policies#1004-acquisition-pricing-and-terms) |
| **Essential Offer Details** | Include relevant offer information such as terms and conditions, privacy policy, supporting documentation and "Learn more" links | SaaS Submission, Workload package metadata, Legal & Privacy Compliance | [More information about offer information](https://learn.microsoft.com/legal/marketplace/certification-policies#1005-offer-information)  and the [personal information](https://learn.microsoft.com/legal/marketplace/certification-policies#1006-personal-information) |
| **Inappropraie content** | Customers expect offers to be free of inappropriate, harmful, or offensive content. | SaaS Submission, Workload package metadata, Legal Compliance| [More information about content](https://learn.microsoft.com/legal/marketplace/certification-policies#10010-inappropriate-content) |
| **Security** | Customers want to be confident that offers are safe and secure. Your offer must not jeopardize or compromise user, Azure service, or related services or systems security. If your offer collects credit card information, or uses a third-party payment processor that collects credit card information, the payment processing must meet the current PCI Data Security Standard (PCI DSS). | SaaS Submission, Security Compliance | [More Information about Security](https://learn.microsoft.com/legal/marketplace/certification-policies#10011-security) |
| **Authentication and fulfillment APIs for translatable SaaS through Microsoft** | Your offer must support Entra AAD SSO for marketplace activation and independent transactions, and must be integrated with the SaaS Fulfilment APIs. | SaaS Submission | [More information about the authentication options](https://learn.microsoft.com/legal/marketplace/certification-policies#10003-authentication-options) and [fulfillment and metering APIs](https://learn.microsoft.com/legal/marketplace/certification-policies#10004-saas-fulfillment-and-metering-apis) |
| **Advertising** | Fabric Workload may not include advertising. | non-Functional | |



# Workload package requirements 
Metadata must be identical in the Workload package manifest and the SaaS offer submission in Partner Center.
Such as: Title, Summary and icon. Add all the assets of the Workload such as icons and screenshots under fe/assests directory.
Your [Workload package](https://nam06.safelinks.protection.outlook.com/?url=https%3A%2F%2Fgithub.com%2Fmicrosoft%2FMicrosoft-Fabric-developer-sample%2Fblob%2Fmain%2FBackend%2Fdocs%2FNuget-Structure.md&data=05%7C02%7CRanin.Salameh%40microsoft.com%7Cd4afc3531dd24b9b0e4708dc6f48998a%7C72f988bf86f141af91ab2d7cd011db47%7C1%7C0%7C638507604807029314%7CUnknown%7CTWFpbGZsb3d8eyJWIjoiMC4wLjAwMDAiLCJQIjoiV2luMzIiLCJBTiI6Ik1haWwiLCJXVCI6Mn0%3D%7C0%7C%7C%7C&sdata=UqrhN4HlCO9K4wVzXZve%2F2Z105iEQHSa0SrgS9K80TY%3D&reserved=0) should comply to both [Frontend manifest requirmenets](https://github.com/microsoft/Microsoft-Fabric-developer-sample/blob/dev/idgoldfa/addProductDetailsSectionToManifest/Frontend/frontendManifest.md) and [Backend manifest requirmenets](https://github.com/microsoft/Microsoft-Fabric-developer-sample/blob/main/Backend/README.md).
   

# Technical requirements
| **Requirement Category** | **Detailed Description** | **Applicable Domain**  | **Reference Links**  |
|--| -- |--| -- |
| **SaaS in Azure Marketplace** | For your SaaS offer to be listed on Azure Marketplace, it must be primarily platform on Microsoft Azure. | SaaS submission, Azure Requirements, Functional | [More information about the SaaS Azure Requirements](https://learn.microsoft.com/legal/marketplace/certification-policies#10001-value-proposition-and-offer-requirements) |
| **OneLake** | OneLake is the hard to store data within Fabric. Extensions need to integrate with it to store data in the standard formats supported by the platform that other services can take advantage of it. | Functional | [More information about the OneLake](https://learn.microsoft.com/fabric/onelake/onelake-overview) |
| **Multi Tenant / Multi Region** | tbd |  |

# Compliance requirements
| **Requirement Category** | **Detailed Description** | **Applicable Domain**  | **Reference Links**  |
|--| -- |--| -- |
| **Publisher Attestation** | Publisher attestation should be listed on partner hosted website. The Publisher attestation document is a way for Workload developers to show customers how their app handles security, data, and compliance. It's a self-assessment where the Workload developer attested the Workload’s security attributes and data-handling practices. The Publisher attestation document should be hosted in the partner website. Publisher must add the link in the Workload metadata manifest under `supportLink`, feild `certification`. This link will also appear in the Workload product page in the Workload Hub | Compliance | |
| **Terms & Conditions** | You need to provide your customers with Terms and conditions for the offer you provide on the platform. In these Terms you also need to highlight the compliancy aspects of your solution (for example, what happens to data at Rest vs. Transit. Where are the services available that you provide to Azure customers, ...)  | Compliance, SaaS Submission | [More information on Fabric Compliancy](https://learn.microsoft.com/fabric/governance/governance-compliance-overview) |
| **ISO 27001:2013** | Your Fabric Workload must comply with ISO 27001:2013. | Compliance, Security | [More information about the ISO 27001:2013](https://www.iso.org/contents/data/standard/05/45/54534.html) |
| **SOC 2 Type 2** | Your Fabric Workload should comply with SOC 2 Type 2. | Compliance, Security | [More information about the SOC 2 Type 2] |
| **Optional/recommended certifications** | If applicable to your customers you want to align with additional certifications Fabric provides today.   | Compliance, Security | [Fabric Certifications](https://learn.microsoft.com/fabric/governance/governance-compliance-overview) |

 



