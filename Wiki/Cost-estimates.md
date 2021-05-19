
# Cost estimates 
## Assumptions 
The estimate below assumes: 
- Tenant has 1 team containing 1000 users. 
- Each user performs approximately 73 calls per month. 

## SKU recommendations 
The recommended SKU for a production environment is: 
- App Service: Standard (S1) 

## Estimated load 

**Data storage**: up to 1 GB usage of Azure table storage. 

**Table data operations (monthly)**: 
|Activities|Operations|Monthly calls| 
|--|--|--| 
|Submit New Hire Introduction|Write|1 requests * 1000 users/month| 
|Review New Hire Introduction|Read|1 requests * 1000 users/month| 
|New Hire Introduction approve/revert request|Write|calls 2 requests * 1000 users/month = 2000| 
|Submit User feedback|Write|calls 1 requests * 1000 users/month| 
|Total calls from User configuration|Read|calls 1000 users/request * 30 calls = 30000| 
|Total calls from Team configuration|Read|1000 users/request * 30 calls = 30000| 
|Request submitted for learning plan|Read|1000 users * 4 week = 4000| 
|Request submitted for learning plan|Read|1000 users * 4 week = 4000| 
|Resubmit request for learning plan|Read|1 request * 30 = 30 request/month| 
||Total estimated write operations|4000 calls/month| 
||Total estimated read operations|69030 calls/month| 

 
## Estimated cost 

**IMPORTANT:** This is only an estimate, based on the assumptions above. Your actual costs may vary. 

Prices were taken from the [Pricing](https://azure.microsoft.com/en-us/pricing/) on 23 Sept 2020, for the West US 2 region. 

Use the [Azure Pricing Calculator](https://azure.com/e/5ecec0ec5f644e5facce29c4e9dfa737) to model different service tiers and usage patterns. 
|**Resource**|**Tier**|**Load**|**Monthly price**| 
|--------------------------|-----------------|-------------------------|-------------------------------------- 
|Bot Channels Registration|F0|N/A|Free| 
|App Service Plan|S1 |744 hours|$74.40| 
|Application Insights (Bot)|||(free up to 5 GB)| 
|Storage account (Table, Blob)| Standard_LRS|< 1GB data & 182,004 operations| $0.05 + $1.06 = $1.14 | 
|Total|||**$75.51**| 