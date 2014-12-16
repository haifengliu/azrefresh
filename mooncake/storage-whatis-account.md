<properties linkid="manage-services-what-is-a-storage-account" urlDisplayName="What is a Storage Account" pageTitle="What is a storage account? | Microsoft Azure" metaKeywords="" description="Learn about the different types of storage accounts available in Azure, and get definitions for key storage terms." metaCanonical="" services="storage" documentationCenter="" title="What is a Storage Account?" authors="tamram" solutions="" manager="mbaldwin" editor="cgronlun" />





#What is a Storage Account?

Azure Storage includes three services: Blob storage, Table storage, and Queue storage. These services are included in every storage account. A storage account provides your unique namespace for working with blobs, queues, and tables.

A storage account can contain up to 200TB of blob, queue, and table data if it was created June 8th, 2012, or later; for storage accounts created before that date, total capacity is 100TB. You can create up to 20 uniquely named storage accounts beneath a single subscription. For more information about storage accounts, see [Azure Storage Scalability and Performance Targets](http://msdn.microsoft.com/zh-cn/library/dn249410.aspx).

All of the information about your storage account, including when it was created, is available in the Management Portal, on the **Dashboard** page for **Storage**.

Storage costs are based on four factors: storage capacity, replication scheme, storage transactions, and data egress. Storage capacity refers to how much of your storage account allotment you are using to store data. The cost of simply storing your data is determined by how much data you are storing, and how it is replicated. Transactions refer to all read and write operations to Azure Storage. Data egress refers to data transferred out of an Azure region. When the data in your storage account is accessed by an application that is not running in the same region, whether that application is a cloud service or some other type of application, then you are charged for data egress. (For Azure services, you can take steps to group your data and services in the same data centers to reduce or eliminate data egress charges.)  

The [Storage Pricing Details](http://www.windowsazure.cn/zh-cn/pricing/overview/#storage) page provides detailed pricing information for storage capacity, replication, and transactions. The [Data Transfers Pricing Details](http://www.windowsazure.cn/zh-cn/pricing/overview/#data_transfer) provides detailed pricing information for data egress.

##Concepts
<!--
- **geo-redundant storage (GRS)**   Geo-redundant storage provides the highest level of storage durability by seamlessly replicating your data to a secondary location within the same region. This enables failover in case of a major failure in the primary location. The secondary location is hundreds of miles from the primary location. GRS is implemented through a feature called *geo-replication*, which is turned on for a storage account by default, but can be turned off if you don't want to use it (for example, if company policies prevent its use). For more information, see [Introducing Geo-Replication for Azure Storage](http://blogs.msdn.com/b/windowsazurestorage/archive/2011/09/15/introducing-geo-replication-for-windows-azure-storage.aspx). 
-->

- **locally redundant storage (LRS)**   Locally redundant storage provides highly durable and available storage within a single location. For locally redundant storage, account data is replicated three times within the same data center. All storage in Azure is locally redundant. For added durability, you can turn on geo-replication. Locally redundant storage is offered at a discount. For pricing information, see [Pricing Details](http://www.windowsazure.cn/zh-cn/pricing/overview/#storage).

- **affinity group**   An *affinity group* is a geographic grouping of your cloud service deployments and storage accounts within Azure. An affinity group can improve service performance by locating computer workloads in the same data center or near the target user audience. Also, no charges are incurred for data egress when data in your storage account is accessed by a service running in the same affinity group.

- **storage account endpoints**   The *endpoints* for a storage account represent the highest level of the namespace for accessing blobs, tables, or queues. The default endpoints for a storage account have the following formats: 

    - Blob service: http://*mystorageaccount*.blob.core.chinacloudapi.cn

    - Table service: http://*mystorageaccount*.table.core.chinacloudapi.cn

    - Queue service: http://*mystorageaccount*.queue.core.chinacloudapi.cn

- **storage account URLs**   The URL for accessing an object in a storage account is formed by appending the object's location in the storage account to the endpoint. For example, a blob address might have this format: http://*mystorageaccount*.blob.core.chinacloudapi.cn/*mycontainer*/*myblob*.

- **storage access keys**   When you create a storage account, Azure generates two 512-bit storage access keys, which are used for authentication when the storage account is accessed. By providing two storage access keys, Azure enables you to regenerate the keys with no interruption to your storage service or access to that service.

- **minimal vs. verbose metrics**   You can configure minimal or verbose metrics in the monitoring settings for your storage account. *Minimal metrics* collects metrics on data such as ingress/egress, availability, latency, and success percentages, which are aggregated for the Blob, Table, and Queue services. *Verbose metrics* collects operations-level detail in addition to service-level aggregates for the same metrics. Verbose metrics enable closer analysis of issues that occur during application operations. For the full list of available metrics, see [Storage Analytics Metrics Table Schema](http://msdn.microsoft.com/zh-cn/library/azure/hh343264.aspx). For more information about storage monitoring, see [About Storage Analytics Metrics](http://msdn.microsoft.com/zh-cn/library/azure/hh343258.aspx).

- **logging**   Logging is a configurable feature of storage accounts that enables logging of requests to read, write, and delete blobs, tables, and queues. You configure logging in the Azure Management Portal, but you can't view the logs in the Management Portal. The logs are stored and accessed in the storage account, in the $logs container. For more information, see [About Storage Analytics Logging](http://msdn.microsoft.com/zh-cn/library/azure/hh343262.aspx).
