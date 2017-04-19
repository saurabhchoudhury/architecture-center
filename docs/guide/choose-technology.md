# Choose the right technologies for Azure applications

## Choosing a compute option

The term *compute* refers to the hosting model for the computing resources that your application runs on. 

At one end of the spectrum is **Intrastructure-as-a-Service** (IaaS). With IaaS, you provision the VMs that you need, along with associated network and storage components. Then you deploy whatever software and applications you want onto those VMs. This model is the closest to a traditional on-premises environment, except that Microsoft manages the infrastructure. You still manage the individual VMs.  

**Platform-as-a-Service** (PaaS) provides a managed hosting environment, where you can deploy your application without needing to manage VMs or networking resources. For example, instead of creating individual VMs, you would just specify an instance count, and the service will provision, configure, and manage the necessary resources. Azure App Service is an examlple of a PaaS service.

**Functions-as-a-Service** (FaaS) goes even further in removing the need to worry about the hosting environment. Instead of creating compute instances and deploying code to those instances, you simply deploy your code, and the managed service automatically runs it. You don’t need to administer the compute resources. These services make use of serverless architecture, and seamlessly scale up or down to whatever level necessary to handle the traffic. Azure Functions are a FaaS service.

IaaS gives the most control, flexibility, and portability. FaaS provides simplicity, elastic scale, and potential cost savings, because you pay only for the time your code is running. PaaS falls somewhere between the two.



 

Each compute options aligns well to certain architecture styles, so choosing an architecture style will guide your choice of compute options.

	- N tier = IaaS
	- W-Q-W = App Service or Cloud Services
	- Event streaming = IoT Hub or Event Hub
	- MSA = ACS, Service Fabric, or Functions
	- Big Compute = Azure Batch



### Comparing compute services

Knowing if a service is IaaS, PaaS, or FaaS will give you some general information about how the service is managed, but there's still many details you need to weigh when considering which service is right for your goals.

- Hosting model - How is the service hosted? What requirements and limitations are imposed by this hosting environment?
- DevOps - How does the compute service integrate into DevOps processes and workflows? What are the automation, support, and operations options available?
- Scalability - Cloud solutions need to adapt to traffic and usage increases and decreases. How does each service handle adding new instances? Can it auto-scale based on load and other metrics? 
- Availability - How do the services compare on handling outages and downtime?
- Security - What kind of security is supported by the service? How is access and permissions managed?
- Other criteria - What are the overall limitations of each service? What kind of architectures are applicable to the service 
- Cost - How do the costs of operating and maintaining solutions hosted on one service compare to another? 




Choosing storage
Selecting the most appropriate set of datastores to match your requirements is a critical design decision in most cloud applications. Azure supports many different types of datastores, and choosing the best types requires understanding the capabilities of each offering.
Data services can be broken up into these major types:
Relational Database Management Systems (RDBMS)
Relational databases base their structure on two-dimensional tables comprising rows and columns. Most provide some form of SQL for performing query and data manipulation tasks. 
Key/Value Stores
A key/value store is essentially a large hash table, where each piece of data is a BLOB associated with a unique key. These stores can handle very flexible types of data and are easily scalable.
Document Databases
Document databases also use a key/value lookup mechanism, but store documents instead of BLOB data. Documents in this context consist of structured data, which the datastore makes accessible to the data consumer.
Column-Family Databases
Column-family databases organize data into rows and columns in similar manner to relational databases. However, column-family databases provide additional structure by grouping columns into logical families, which can be manipulated independently of the rest of the row.
Graph Databases
A graph database stores two types of information: nodes that you can think of entities, and edges which specify the relationships between nodes. The purpose of a graph database is to enable an application to efficiently perform queries that traverse the network of nodes and edges, and to analyze the relationships between entities.
Parallel Data Warehouses
A parallel data warehouse (PDW) provides a massively parallel solution for ingesting, storing, and analyzing data. PDWs are optimized for processing very large amounts of data in various formats.
Search Engine Databases
Search engine databases rapidly index large amounts of data from external data stores, enabling fast searching through the result set. 
Time Series Databases
Time series databases are optimized for dealing with data organized from time, such as telemetry data. These databases are designed to support large numbers of write operations, as the individual data points stored are small, but the overall amount of data sent to these databases can be quite large.
Shared Files
A shared file data store is simply a location where flat files can be stored and used by consuming applications and services. 

Some technologies may span multiple types. The technologies are changing quickly and the lines will continue to blur even more.

Comparing compute services 
There are multiple services available for each of these storage types, so once you've figured out the type of storage your solution requires, you should still look at additional details about the specific services:
•	Managed / Unmanaged services - Is the service managed? Can your solution benefit from using a managed data store, or do you need the control available from unmanaged services?
•	Development - Can you access the service using the development stack you plan on using?
•	Security / Authentication - How is data secured? How is it accessed?
•	Size / Scalability - What are the limits of the service? How easy is it to scale up capacity?
•	Other issues - Are there specific features your solution will need? What overall limitations or other restrictions apply to a particular service?
•	Cost - What are costs for using each of the service options?
