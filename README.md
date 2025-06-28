# Managing-Billing-records
Cost Optimisation:
Blob Storage:
Automate Tiering with Lifecycle Management:
Set up lifecycle management policies to automatically move blobs between tiers based on last access or modification dates (e.g., move to Cool after 30 days, Archive after 180 days)
Recently created = Hot
3 months old = Cool
Much older or rarely accessed = Archive

exchange for discounted prices compared to pay-as-you-go pricing.
Cost Savings:
   Storage Type
Pay-as-you-go
Reserved (1-year)
Reserved (3-year)
Hot Tier
₹1.61/GB/mo
₹1.14/GB/mo
₹1.00/GB/mo
Cool Tier
₹0.86/GB/mo
₹0.64/GB/mo
₹0.56/GB/mo

Optimize Blob Design
Use data compression and deduplication to minimize storage size and costs.
Monitor and Analyze Usage
Use Azure Storage inventory and monitoring tools to track usage patterns and identify cost-saving opportunities

**Azure functions**
Use the Consumption Plan
The default pay-per-execution model ensures you only pay for what you use; avoid premium or dedicated plans unless necessary for performance or VNET integration.
Optimize Function Code
Minimize execution time and memory allocation to reduce billed duration.
Avoid unnecessary dependencies and keep functions lightweight.
Consolidate Functions
Group related operations in a single function app to reduce cold start and resource overhead.
Set Timeout and Concurrency Limits
Prevent runaway executions by setting appropriate timeouts.
Monitor and Analyze Execution
Use Application Insights to identify inefficient code or high-frequency triggers that drive up costs.
Leverage Durable Functions Only When Needed
Durable Functions can be more expensive due to orchestration overhead; use only for complex workflows.
**Additional Cost Controls**
Reserved Capacity:
If your workload is predictable, purchase reserved capacity for Cosmos DB to get significant discounts.
Regional Replication:
Only replicate data to regions where it’s actually needed to avoid unnecessary bandwidth and storage costs.
Minimize Data Transfer:
Place your Cosmos DB account in the same region as your application to reduce inter-region data transfer charges





References:
https://www.perplexity.ai/search/role-cloud-architect-architect-rlPV0qeYSuCa4Aoxs433Kg

