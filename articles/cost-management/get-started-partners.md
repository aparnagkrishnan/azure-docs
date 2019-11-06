---
title: Get started with Azure Cost Management for partners
description: This article explains how partners use Azure Cost Management features and how they enable Cost Management access for their customers.
services: cost-management
keywords:
author: bandersmsft
ms.author: banders
ms.date: 11/04/2019
ms.topic: conceptual
ms.service: cost-management
manager: aparnag
ms.custom: secdec18
---

# Get started with Azure Cost Management for partners

Azure Cost Management is natively available for partners who have onboarded their customers to a Microsoft Customer Agreement and have purchased an Azure Plan. This article explains how partners use [Azure Cost Management](https://docs.microsoft.com/azure/cost-management/) features. It also describes how partners enable Cost Management access for their customers. Customers can use Cost Management features when enabled by their CSP partner.

CSP partners use Cost Management to:

- Understand invoiced costs and associate the costs to the customer, subscriptions, resource groups, and services.
- Get an intuitive view of Azure costs in [cost analysis](quick-acm-cost-analysis.md) with capabilities to analyze costs by customer, subscription, resource group, resource, meter, service, and many other dimensions.
- View resource costs that have Partner Earned Credit (PEC) applied in Cost Analysis.
- Set up notifications and automation using programmatic [budgets](tutorial-acm-create-budgets.md) and alerts when costs exceed budgets.
- Enable the Azure Resource Manager policy that provides customer access to Cost Management data. Customers can then view consumption cost data for their subscriptions using [pay-as-you-go rates](https://azure.microsoft.com/pricing/calculator/).

Here's an example showing costs for all customers.
![Example showing costs for all customers](./media/get-started-partners/customer-costs1.png)

Here's an example showing costs for a single customer.
![Example showing costs for a single customer](./media/get-started-partners/customer-costs2.png)

All functionality available in Azure Cost Management is also available with REST APIs. Use the APIs to automate cost management tasks.

## Prerequisites

Azure Cost Management requires read access to your billing account or subscription. Access can be granted at any level above your resources, from the billing account or a management group down to individual resource groups where you manage your apps. For more information about enabling and assigning access to Azure Cost Management for a billing account, see [Assign users roles and permissions](/partner-center/permissions-overview). The **Global admin** and **Admin agent** roles can manage costs for a billing account.

To view a full list of supported account types, see [Understand Cost Management data](understand-cost-mgt-data.md).


## How Cost Management uses scopes

Scopes are where you manage billing data, have roles specific to payments, view invoices, and conduct general account management. Billing and account roles are managed separately from scopes used for resource management, which use RBAC. To clearly distinguish the intent of the separate scopes, including the access control differences, they are referred to as billing scopes and RBAC scopes, respectively.

To understand billing scopes and RBAC scopes and how cost management works with scopes, see [Understand and work with scopes](understand-work-scopes.md).

## Manage costs with partner tenant billing scopes

After you've onboarded your customers to a Microsoft Customer Agreement, the following _billing scopes_ are available in your tenant. Use the scopes to manage costs in Cost Management.

### Billing account scope

Use the billing account scope to view pre-tax costs across all your customers and billing profiles. Invoice costs are only shown for customer's consumption-based products on the Microsoft Customer Agreement. However, invoice costs are shown for purchased-based products for customers on both the Microsoft Customer Agreement and the CSP offer. Currently, the default currency to view costs in the scope is US dollars. Budgets set for the scope are also in USD.

Regardless of different customer-billed currencies, partners use Billing account scope to set budgets and manage costs in USD across their customers, subscriptions, resources, and resource groups.

Partners also filter costs in a specific billing currency across customers in the cost analysis view. Select the **Actual cost** list to view costs in supported customer billing currencies.

![Example showing Actual cost selection for currencies](./media/get-started-partners/actual-cost-selector.png)

Use the [amortized cost view](quick-acm-cost-analysis.md#customize-cost-views) in billing scopes to view reserved instance amortized costs across a reservation term.

### Billing profile scope

Use the billing profile scope to view pre-tax costs in the billing currency across all your customers for all products and subscriptions included in an invoice. You can filter costs in a billing profile for a specific invoice using the **InvoiceID** filter. The filter shows the consumption and product purchase costs for a specific invoice. You can also filter the costs for a specific customer on the invoice to see pre-tax costs.

After you onboard customers to a Microsoft Customer Agreement, you receive an invoice that includes all charges for all products (consumption, purchases, and entitlements) for these customers on the Microsoft Customer Agreement. When billed in the same currency, these invoices also include the charges for entitlement and purchased products such as SaaS, Azure Marketplace, and reservations for customers who are still in the CSP offer.

To help reconcile charges against the customer invoice, the billing profile scope enables you to see all costs that accrue for an invoice for your customers. Like the invoice, the scope shows costs for every customer in the new Microsoft Customer Agreement. The scope also shows every charge for customer entitlement products still in the current CSP offer.

The billing profile and billing account scopes are the only applicable scopes that show charges for entitlement and purchase-based products like Azure Marketplace and reservation purchases.

Billing profiles define the subscriptions that are included in an invoice. Billing profiles are the functional equivalent of an enterprise agreement enrollment. A billing profile is the scope where invoices are generated.

Currently, the customer's billing currency is the default currency when viewing costs in the billing profile scope. Budgets set at the billing profile scope are in the billing currency.

Partners can use the scope to reconcile to invoices. And, they use the scope to set budgets in the billing currency for the following items:

- Specific filtered invoice
- Customer
- Subscription
- Resource group
- Resource
- Azure service
- Meter
- ResellerMPNID

### Customer scope

Partners use the scope to manage costs associated to customers that are onboarded to the Microsoft Customer Agreement. The scope allows partners to view pre-tax costs for a specific customer. You can also filter the pre-tax costs for a specific subscription, resource group, or resource.

The customer scope doesn't include customers who are on the current CSP offer. The scope only includes customers who have a Microsoft Customer Agreement. Entitlement costs, not Azure usage, for current CSP offer customers are available at the billing account and billing profile scopes when you apply the customer filter.

## Partner access to billing scopes in Cost Management

Only the users with **Global admin** and **Admin agent** roles can manage and view costs for billing accounts, billing profiles, and customers directly in the partner's Azure tenant. For more information about partner center roles, see [Assign users roles and permissions](/partner-center/permissions-overview).

## Enable cost management in the customer tenant

Partners may enable access to Cost Management after customers are onboarded to a Microsoft Customer Agreement. Then partners can then enable a policy allowing customers to view their costs computed at pay-as-you-go retail rates. Costs are shown in the customer's billing currency for their consumed usage at RBAC subscription and resource groups scopes.

When the policy for cost visibility is enabled by the partner, any user with Azure Resource Manager access to the subscription can manage and analyze costs at pay-as-you-go rates. Effectively, resellers and customers that have the appropriate RBAC access to the Azure subscriptions can view cost.

Regardless of the policy, partners can also view the costs if they have access to the subscription and resource group.

### Enable the policy to view Azure usage charges

Partners use the following information to enable to the policy to view Azure usage charges for their customers.

In the Azure portal, sign in to the partner tenant and click **Cost Management + Billing**. Select a billing account and then click **Customers**. The list of customers is associated with the billing account.

In the list of customers, select the customer that you want to allow to view costs.

![Select customers in Cost Management](./media/get-started-partners/customer-list.png)

Under **Settings**, click **Policies**.

The current cost visibility policy is shown for **Azure Usage** charges associated to the subscriptions for the selected customer.
![Policy to allow customers to view pay-as-you-go charges](./media/get-started-partners/cost-management-billing-policies.png)

When the policy is set to **No**, Azure Cost Management isn't available for subscription users associated to the customer. Unless enabled by a partner, the cost visibility policy is disabled by default for all subscription users.

When the cost policy is set to **Yes**, subscription users associated to the customer tenant can see usage charges at pay-as-you go rates.

When the cost visibility policy is enabled, all services that have subscription usage show costs at pay-as-you-go rates. Reservation usage appears with zero charges for actual and amortized costs. Purchases and entitlements are not associated to a specific subscription. So, purchases aren't displayed at the subscription scope.

To view costs for the customer tenant, open Cost Management + Billing and then click Billing accounts. In the list of billing accounts, click a billing account.

![Select a billing account](./media/get-started-partners/select-billing-account.png)

Under **Billing**, click **Azure subscriptions**, and then click a customer.

![Select an Azure subscription customer](./media/get-started-partners/subscriptions-select-customer.png)

Click **Cost analysis** and start reviewing costs.
Cost analysis, budgets, and alerts are now available for the subscription and resource group RBAC scopes at pay-as-you-go rate-based costs.

![View cost analysis as a customer ](./media/get-started-partners/customer-tenant-view-cost-analysis.png)

Amortized views and actual costs for reserved instances in the RBAC scopes show zero charges. Reserved instance costs are only showing in billing scopes where the purchases were made.

## Analyze costs in cost analysis

Partners can explore and analyze costs in cost analysis across customers for a specific customer or for an invoice.

The following fields are found in usage detail files and Cost Management APIs. For the following bold fields, you can use filter and group by features in cost analysis to analyze costs by multiple fields.

| **Field name** | **Description** |
| --- | --- |
| invoiceId | Invoice ID shown on the invoice for the specific transaction. |
| previousInvoiceID | Reference to an original invoice there is a refund (negative cost). Populated only when there is a refund. |
| billingAccountName | Name of the billing account representing the partner. It accrues all costs across the customers who have onboarded to a Microsoft customer agreement and the CSP customers that have made entitlement purchases like SaaS, Azure Marketplace, and reservations. |
| billingAccountID | Identifier for the billing account representing the partner. |
| billingProfileID | Identifier for the billing profile that groups costs across invoices in a single billing currency across the customers who have onboarded to a Microsoft customer agreement and the CSP customers that have made entitlement purchases like SaaS, Azure Marketplace, and reservations. |
| billingProfileName | Name of the billing profile that groups costs across invoices in a single billing currency across the customers who have onboarded to a Microsoft customer agreement and the CSP customers that have made entitlement purchases like SaaS, Azure Marketplace, and reservations. |
| invoiceSectionName | Name of the project that is being charged in the invoice. Not applicable for Microsoft Customer Agreements onboarded by partners. |
| invoiceSectionID | Identifier of the project that is being charged in the invoice. Not applicable for Microsoft Customer Agreements onboarded by partners. |
| **CustomerTenantID** | Identifier of the Azure Active Directory tenant of the customer&#39;s subscription. |
| **CustomerName** | Name of the Azure Active Directory tenant for the customer&#39;s subscription. |
| **CustomerTenantDomainName** | Domain name for the Azure Active Directory tenant of the customer&#39;s subscription. |
| **PartnerTenantID** | Identifier for the partner&#39;s Azure Active Directory tenant. |
| **PartnerName** | Name of the partner Azure Active Directory tenant. |
| **ResellerMPNID** | MPNID for the reseller associated with the subscription. |
| costCenter | Cost center associated to the subscription. |
| billingPeriodStartDate | Billing period start date, as shown on the invoice. |
| billingPeriodEndDate | Billing period end date, as shown on the invoice. |
| servicePeriodStartDate | Start date for the rating period when the service usage was rated for charges. The prices for Azure services are determined for the rating period. |
| servicePeriodEndDate | End date for the period when the service usage was rated for charges. The prices for Azure services are determined based on the rating period. |
| date | For Azure consumption data, it shows date of usage as rated. For reserved instance, it shows the purchased date. For recurring charges and one-time charges such as Marketplace and support, it shows the purchase date. |
| productID | Identifier for the product that has accrued charges by consumption or purchase. It is the concatenated key of productID and SKuID, as shown in the Partner Center. |
| product | Name of the product that has accrued charges by consumption or purchase, as shown on the invoice. |
| serviceFamily | Shows the service family for the product purchased or charged. For example, Storage or Compute. |
| productOrderID | The identifier of the asset or Azure plan name that the subscription belongs to. For example, Azure Plan. |
| productOrderName | The name of the Azure plan that the subscription belongs to. For example, Azure Plan. |
| consumedService | Consumed service (legacy taxonomy) as used in legacy EA usage details. |
| meterID | Metered identifier for measured consumption. |
| meterName | Identifies the name of the meter for measured consumption. |
| meterCategory | Identifies the top-level service for usage. |
| meterSubCategory | Defines the type or subcategory of Azure service that can affect the rate. |
| meterRegion | Identifies the location of the datacenter for certain services that are priced based on datacenter location. |
| subscription ID | Unique Microsoft generated identifier for the Azure subscription. |
| subscriptionName | Name of the Azure subscription. |
| Term | Displays the term for the validity of the offer. For example, reserved instances show 12 months of a yearly term of the reserved instance. For one-time purchases or recurring purchases, the term displays one month for SaaS, Azure Marketplace, and support. Not applicable for Azure consumption. |
| publisherType (firstParty, thirdPartyReseller, thirdPartyAgency) | Type of publisher that identifies the publisher as first party, third-party reseller, or third-party agency. |
| partNumber | Part number for the unused reserved instance and Azure Marketplace services. |
| publisherName | Name of the publisher of the service including Microsoft or third-party publishers. |
| reservationId | Identifier for the reserved instance purchase. |
| reservationName | Name of the reserved instance. |
| reservationOrderId | OrderID for the reserved instance. |
| frequency | Payment frequency for a reserved instance. |
| resourceGroup | Name of the Azure resource group used for lifecycle resource management. |
| instanceID (or) ResourceID | Identifier of the resource instance. |
| resourceLocation | Name of the resource location. |
| Location | Normalized location of the resource. |
| effectivePrice | The effective unit price of the service, in pricing currency. Unique for a product, service family, meter, and offer. Used with pricing in the price sheet for the billing account. When there is tiered pricing or an included quantity, it shows the blended price for consumption. |
| Quantity | Measured quantity purchased or consumed. The amount of the meter used during the billing period. |
| unitOfMeasure | Identifies the unit that the service is charged in. For example, GB and hours. |
| pricingCurrency | The currency defining the unit price. |
| billingCurrency | The currency defining the billed cost |
| chargeType | Defines the type of charge that the cost represents in Azure Cost Management like purchase and refund. |
| costinBillingCurrency | ExtendedCost or blended cost before tax in the billed currency. |
| costinPricingCurrency | ExtendedCost or blended cost before tax in pricing currency to correlate with prices. |
| **costinUSD** | Estimated ExtendedCost or blended cost before tax in USD. |
| **paygCostInBillingCurrency** | Shows costs if pricing is in retail prices. Shows pay-as-you-go prices in the billing currency. Available only at RBAC scopes. |
| **paygCostInUSD** | Shows costs if pricing is in retail prices. Shows pay-as-you-go prices in USD. Available only at RBAC scopes. |
| exchangeRate | Exchange rate used to convert from the pricing currency to the billing currency. |
| exchangeRateDate | The date for the exchange rate that&#39;s used to convert from the pricing currency to the billing currency. |
| isAzureCreditEligible | Indicates whether the cost is eligible for payment by Azure credits. |
| serviceInfo1 | Legacy field that captures optional service-specific metadata. |
| serviceInfo2 | Legacy field that captures optional service-specific metadata. |
| additionalInfo | Service-specific metadata. For example, an image type for a virtual machine. |
| tags | Tag that you assign to the meter. Use tags to group billing records. For example, you can use tags to distribute costs by the department that uses the meter. |
| **partnerEarnedCreditRate** | Rate of discount applied if there is a partner earned credit (PEC) based on partner admin link access. |
| **partnerEarnedCreditApplied** | Indicates whether the partner earned credit has been applied. |

In the [cost analysis](quick-acm-cost-analysis.md) view, you can also [save views](quick-acm-cost-analysis.md#saving-and-sharing-customized-views) and export data to [CSV and PNG files](quick-acm-cost-analysis.md#automation-and-offline-analysis).

## View Partner Earned Credit (PEC) resource costs

In Azure Cost Management, partners can use cost analysis to view costs that received the PEC benefits.

In the Azure portal, sign in to the partner tenant and select **Cost Management + Billing**. Under **Cost Management**, click **Cost analysis**.

The Cost analysis view shows costs of the billing account for the partner. Select the **Scope** as needed for the partner, a specific customer, or a billing profile to reconcile invoices.

In a donut chart, click the drop-down list and select **PartnerEarnedCreditApplied** to drill into PEC costs.

![Example showing how to view partner-earned credit](./media/get-started-partners/cost-analysis-pec1.png)

When the **PartnerEarnedCreditApplied** property is _True_, the associated cost has the benefit of the partner earned admin access.

When the **PartnerEarnedCreditApplied** property is _False_, the associated cost hasn't met the required eligibility for the credit. Or, the service purchased isn't eligible for partner earned credit.

Service usage data normally takes 8-24 hours to appear in Cost Management. For more information, see [Usage data update frequency varies](understand-cost-mgt-data.md#usage-data-update-frequency-varies). PEC credits appear within 48 hours from time of access in Azure Cost Management.


You can also group and filter by the **PartnerEarnedCreditApplied** property using the **Group by** options. Use the options to examine costs that do and don't have PEC.

![Group or filter by partner-earned credit](./media/get-started-partners/cost-analysis-pec2.png)

## Cost Management REST APIs

Partners and customers can use Cost Management APIs described in the following sections for common tasks.

### Azure Cost Management APIs - Direct and indirect providers

Partners with access to billing scopes in a partner tenant can use the following APIs to view invoiced costs.

APIs at the subscription scope can be called by a partner regardless of the cost policy if they have access to the subscription. Other users with access to the subscription, like the customer or reseller, can call the APIs only after the partner enables the cost policy for the customer tenant.


#### To get a list of billing accounts

```
GET https://management.azure.com/providers/Microsoft.Billing/billingAccounts?api-version=2019-10-01-preview
```

#### To get a list of customers

```
GET https://management.azure.com/providers/Microsoft.Billing/billingAccounts/{billingAccountName}/customers?api-version=2019-10-01-preview
```

#### To get a list of subscriptions

```
GET https://management.azure.com/providers/Microsoft.Billing/billingAccounts/{billingAccountName}/billingSubscriptions?api-version=2019-10-01-preview
```

#### To get the policy for customers to view costs

```
GET https://management.azure.com/providers/Microsoft.Billing/billingAccounts/{billingAccountName}/customers/{customerID}/policies/default?api-version=2019-10-01-preview
```

#### To set the policy for customers to view costs

```
PUT https://management.azure.com/providers/Microsoft.Billing/billingAccounts/{billingAccountName}/customers/{customerID}/policies/default?api-version=2019-10-01-preview
```

#### To get Azure service usage for a billing account

```
GET https://management.azure.com/providers/Microsoft.Billing/BillingAccounts/{billingAccountName}/providers/Microsoft.Consumption/usageDetails?api-version=2019-10-01
```

#### To download a customer's Azure service usage

The following get call is an asynchronous operation.

```
GET https://management.azure.com/Microsoft.Billing/billingAccounts/{billingAccountName}/customers/{customerID}/providers/Microsoft.Consumption/usageDetails/download?api-version=2019-10-01 -verbose
```

Call the `Location` URI returned in the response to check the operation status. When the status is *Completed*, the `downloadUrl` property contains a link that you can use to download the generated report.


#### To get or download the price sheet for consumed Azure services

First, use the following post.

```
POST https://management.azure.com/providers/Microsoft.Billing/BillingAccounts/{billingAccountName}/billingProfiles/{billingProfileID}/pricesheet/default/download?api-version=2019-10-01-preview&format=csv" -verbose
```

Then, call the asynchronous operation property value. For example:

```
GET https://management.azure.com/providers/Microsoft.Billing/billingAccounts/{billingAccountName}/billingProfiles/{billingProfileID}/pricesheetDownloadOperations/{operation}?sessiontoken=0:11186&api-version=2019-10-01-preview
```
The preceding get call returns the download link containing the price sheet.


#### To get aggregated costs

```
POST https://management.azure.com/providers/microsoft.billing/billingAccounts/{billingAccountName}/providers/microsoft.costmanagement/query?api-version=2019-10-01
```

#### Create a budget for a partner

```
PUT https://management.azure.com/providers/Microsoft.Billing/billingAccounts/{billingAccountName}/providers/Microsoft.CostManagement/budgets/partnerworkshopbudget?api-version=2019-10-01
```

#### Create a budget for a customer

```
PUT https://management.azure.com/providers/Microsoft.Billing/billingAccounts/{billingAccountName}/customers/{customerID}/providers/Microsoft.Consumption/budgets/{budgetName}?api-version=2019-10-01
```

#### Delete a budget

```
PUT
https://management.azure.com/providers/Microsoft.Billing/billingAccounts/{billingAccountId}/providers/Microsoft.CostManagement/budgets/{budgetName}?api-version=2019-10-01
```


## Next steps
- [Start analyzing costs](quick-acm-cost-analysis.md) in Cost Management
- [Create and manage budgets](tutorial-acm-create-budgets.md) in Cost Management
