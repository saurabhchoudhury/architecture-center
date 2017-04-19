# Compute options

lorem ipsum...

## Hosting model

| Criteria |  Virtual Machines |  Cloud Service |  Service Fabric |  App Service |  Azure Functions |  Azure Container Service |  Azure Batch |
|---------------|-------------------|----------------|-----------------|--------------|------------------|--------------------------|-------------|
| Application composition | Agnostic | Roles | Services | Application | Function | Agnostic | Scheduled jobs  |
| Density | 1 application per VM | One role instance per VM | Multiple services per VM | Multiple apps per instance | No dedicated instances <a href="#note1">[1]</a> | Multiple containers per VM | Multiple apps per VM |
| Minimum number of instances | 1 <a href="#note2">[2]</a> | 2 | 5 <a href="#note3">[3]</a> | 1 | N/A <a href="#note1">[1] | 3 | 1  <a href="#note4">[4]</a> |
| State management | Stateless or Stateful | Stateless | Stateless or stateful | Stateless | Stateless | Stateless or Stateful | Stateless |
| Web hosting | Agnostic | Built-in (IIS) | Self-host<br/>IIS in containers | Built in | Not applicable | Agnostic | None |
| OS | Windows, Linux | Windows | Windows, Linux [preview] | Windows, Linux [preview] | N/A | Windows, Linux | Windows, Linux |
| Dedicated network | Supported | Supported | Supported | Supported <a href="#note5">[5] | Not supported | Supported | Supported |
| Hybrid connectivity | Supported | Supported | Supported | Supported <a href="#note6">[6] | Not supported | Supported | Supported |

## DevOps

| Criteria |  Virtual Machines |  Cloud Service |  Service Fabric |  App Service |  Azure Functions |  Azure Container Service |  Azure Batch |
|---------------|-------------------|----------------|-----------------|--------------|------------------|--------------------------|-------------|
| Programming model | Agnostic | Web role, worker role | Guest executable, Service model, Actor model, Containers | Web application, WebJobs for background tasks | Functions with triggers | Agnostic | Command line application |
| Local debugging | Agnostic | Local emulator | Local node cluster | IIS Express, others <a href="#note7">[7] | Azure Functions CLI | Local container runtime | Not supported |
| Deployment | Resource Manager | Resource manager, Classic | Resource Manager | Resource Manager | Resource Manager | Resource Manager | Resource Manager |
| Application update | No built-in support | VIP swap or rolling update<td>Rolling upgrade (per service) | Deployment slots | No built-in support | Depends on orchestrator. Most support rolling updates. | N/A |

## Scalability

| Criteria |  Virtual Machines |  Cloud Service |  Service Fabric |  App Service |  Azure Functions |  Azure Container Service |  Azure Batch |
|---------------|-------------------|----------------|-----------------|--------------|------------------|--------------------------|-------------|
| Auto-scaling | VM scale sets | Built-in service | VM Scale Sets. Built-in for application scaling. | Built-in service | Built-in service | Not supported | N/A |
| Load balancer | Azure Load Balancer | Integrated | Azure Load Balancer | Integrated | Integrated | Azure Load Balancer | Azure Load Balancer |
| Scale limit | Platform image: 1000 nodes per VMSS<br/>Custom image: 100 nodes per VMSS | No defined limit. 200 maximum recommended | 100 nodes per VMSS | 20 instances<br/>50 with App Service Environment | Infinite <a href="#note8">[8]</a> |
| 100 | 20 core limit by default. Contact customer service for increase. |



<tr><td colspan="8">Availability |
| SLA | SLA for Virtual Machines |
| SLA for Cloud Services | SLA for Service Fabric | SLA for App Service | SLA for Functions | SLA for Azure Container Service | SLA for Azure Batch |
| Multi region failover | Traffic manager | Traffic manager | Traffic manager |
| Multi-Region Cluster | Traffic manager | Not supported	 | Traffic manager | Not Supported |
| Security |
<tr></tr>
| SSL | Configured in VM | Supported |
| Supported  | Supported | Supported | Configured in VM | Supported |
| Supports RBAC? | Yes | No | Yes | Yes | Yes | Yes | Yes |
| Security Center | Supported | Supported | Not supported | Not supported  | Not supported  | Not supported  | Not supported  |
| Others | Suitable architecture styles | Lift and Shift |
| N-Tier+ | Web Queue Worker | Microservices |
| EDA | Web Queue Worker | Microservices |
| EDA | Microservices |
| EDA | Asynchronous Task Batch Processing |
| Limitations | VM requires more management tasks such as patching OS, antimalware/antivirus updates, etc... | Cloud services  |
| require a gateway to communicate with applications deployed via ARM. RBAC is not supported.  |
| ASP.NET applications.must be self-hosted or run on IIS in a container. |
| It requires ASE for dedicated VNet. Application can scale up to 20 instance. It requires ASE to go beyond that.  | Don’t use to run long running operations. Decompose it into smaller functions that work together. |
| It supports these triggers  | Orchestrator upgrade is not supported. | (Limits on # of nodes  |
</table>

<span id=note1>1.</span> If using Consumption plan. If using App Service plan, functions run on the VMs allocated for your App Service plan. For more information, see .

<span id=note2>2.</span> Higher SLA with 2 or more instances

<span id=note3>3.</span> For production environments

<span id=note4>4.</span> Can scale down to zero after job completes

<span id=note5>5.</span> Requires ASE

<span id=note6>6.</span> Requires ASE or BizTalk Hybrid Connections

<span id=note7>7.</span> Options include: IIS Express for ASP.NET or node.js (iisnode); PHP web server; Azure Toolkit for IntelliJ, Azure Toolkit for Eclipse. App Service also supports remote debugging of deployed web app.
