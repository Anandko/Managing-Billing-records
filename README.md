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


 
Azure functions
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
Cosmos DB:
1. Throughput (RU) Optimization
Use Autoscale Provisioned Throughput:
Autoscale adjusts RU/s automatically based on demand, scaling up during peaks and scaling down during off-peak times, so you only pay for what you use.
Shell Example:
text
**az cosmosdb sql container throughput update --account-name <account> --database-name <db> --name <container> --max-throughput <maxRU>**
Right-size RU/s :
Monitor your actual RU consumption and adjust provisioned throughput to avoid over-provisioning.
Shell Example: 

Text:
**az cosmosdb sql container throughput show --account-name <account> --database-name <db> --name <container>**


Review Partition Key Design:
Ensure even data distribution across partitions to avoid “hot” partitions, which can force you to over-provision RU/s for a small subset of data.
Shell Example:
text
**az cosmosdb sql container show --account-name <account> --database-name <db> --name <container> --query "partitionKey"**


2. Query and Data Access Optimization
Optimize Queries:
Retrieve only necessary fields (project columns).
Use efficient filters and avoid cross-partition queries when possible.
Monitor RU charge for queries and refactor high-cost queries.
Shell Example:
Text:
# Use Azure Data Explorer or Azure Portal to review RU charges for queries
Colocate Related Data:
Store related entities in the same container to minimize cross-container joins and lower query costs.
Use Indexing Policies Wisely:
Exclude large, infrequently queried properties from indexing to reduce write costs and storage overhead.
Shell Example:
Text:

**az cosmosdb sql container update --account-name <account> --database-name <db> --name <container> --idx <indexingPolicy.json>**

3. Storage and Data Lifecycle Management
Implement Time-to-Live (TTL):
Automatically delete obsolete or expired records to save on storage and improve query performance.
Shell Example:
Text:
**az cosmosdb sql container update --account-name <account> --database-name <db> --name <container> --ttl <seconds>**
Archive Old Data:
Move rarely accessed historical records to cheaper storage (e.g., Azure Blob Storage) if regulatory requirements allow.
Shell Example:
Export data using Azure Data Factory or custom scripts.
Data Compression:
Compress large records before storage to reduce storage costs (implement at the application layer).
4. Monitoring and Continuous Tuning
Monitor RU Consumption and Latency:
Use Azure Monitor and built-in metrics to track usage, identify spikes, and tune accordingly.
Shell Example:
Text:
**az monitor metrics list --resource <cosmosdb-resource-id> --metric "TotalRequestUnits"**
Analyze Usage Patterns:
Identify peak and off-peak periods and adjust throughput or autoscale settings accordingly.


5. Additional Cost Controls
Reserved Capacity:
If your workload is predictable, purchase reserved capacity for Cosmos DB to get significant discounts.
Regional Replication:
Only replicate data to regions where it’s actually needed to avoid unnecessary bandwidth and storage costs.
Minimize Data Transfer:
Place your Cosmos DB account in the same region as your application to reduce inter-region data transfer charges





References:
https://www.perplexity.ai/search/role-cloud-architect-architect-rlPV0qeYSuCa4Aoxs433Kg

