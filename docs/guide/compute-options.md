# Compute options

## Hosting model

| Criteria | Virtual Machine | App Service | Service Fabric | Azure Functions | Azure Container Service | Cloud Services | Azure Batch |
|----------|-----------------|-------------|----------------|-----------------|-------------------------|----------------|-------------|
| Application composition | Agnostic | Applications | Services | Functions | Agnostic | Roles | Scheduled jobs  |
| Density | 1 application per VM | Multiple apps per instance via app plans | Multiple services per VM | No dedicated instances <a href="#note1">[1]</a> | Multiple containers per VM | One role instance per VM | Multiple apps per VM |
| Minimum number of nodes | 1 <a href="#note2">[2]</a>  | 1 | 5 <a href="#note3">[3]</a> | No dedicated nodes <a href="#note1">[1]</a> | 3 | 2 | 1 <a href="#note4">[4]</a> |
| State management | Stateless or Stateful | Stateless | Stateless or stateful | Stateless | Stateless or Stateful | Stateless | Stateless |
| Web hosting | Agnostic | Built in | Self-host, IIS in containers | Not applicable | Agnostic | Built-in (IIS) | No |
| OS | Windows, Linux | Windows, Linux  | Windows, Linux | Windows, Linux | Windows,  Linux | Windows | Windows, Linux |
| Dedicated network | Supported | Supported <a href="#note5">[5]</a> | Supported | Not supported | Supported | Supported <a href="#note6">[6]</a> | Supported |
| Hybrid connectivity | Supported | Supported <a href="#note1">[7]</a>  | Supported | Not supported | Supported | Supported <a href="#note8">[8]</a> | Supported |

Notes

<span id="note1">1. If using Consumption plan. If using App Service plan, functions run on the VMs allocated for your App Service plan. See [Choose the correct service plan for Azure Functions][function-plans].</a>

<span id="note2">2. Higher SLA with two or more instances.</a>

<span id="note3">3. For production environments.</a>

<span id="note4">4. Can scale down to zero after job completes.</a>

<span id="note5">5. Requires App Service Environment (ASE).</a>

<span id="note6">6. Classic VNet only.</a>

<span id="note7">7. Requires ASE or BizTalk Hybrid Connections</a>

<span id="note8">8. Classic VNet, or Resource Manager VNet via VNet peering</a>


Notes

1. <span id="note1">If using Consumption plan. If using App Service plan, functions run on the VMs allocated for your App Service plan. See [Choose the correct service plan for Azure Functions][function-plans].</a>
2. <span id="note2">Higher SLA with two or more instances.</a>
3. <span id="note3">For production environments.</a>
4. <span id="note4">Can scale down to zero after job completes.</a>
5. <span id="note5">Requires App Service Environment (ASE).</a>
6. <span id="note6">Classic VNet only.</a>
7. <span id="note7">Requires ASE or BizTalk Hybrid Connections</a>
8. <span id="note8">Classic VNet, or Resource Manager VNet via VNet peering</a>


| Criteria | Virtual Machine | App Service | Service Fabric | Azure Functions | Azure Container Service | Cloud Services | Azure Batch |
|----------|-----------------|-------------|----------------|-----------------|-------------------------|----------------|-------------|
| Local debugging | Agnostic | IIS Express, others <a href="#note1b">[1]</a> | Local node cluster | Azure Functions CLI | Local container runtime | Local emulator | Not supported |
| Programming model | Agnostic | Web application, WebJobs for background tasks | Guest executable, Service model, Actor model, Containers | Functions with triggers | Agnostic | Web role / worker role | Command line application |
| Application update | No built-in support | Deployment slots | Rolling upgrade (per service) | No built-in support | Depends on orchestrator. Most support rolling updates | VIP swap or rolling update | N/A |

| Criteria | Virtual Machine | App Service | Service Fabric | Azure Functions | Azure Container Service | Cloud Services | Azure Batch |
|----------|-----------------|-------------|----------------|-----------------|-------------------------|----------------|-------------|
| Auto-scaling | VM scale sets | Built-in service | VM Scale Sets, Built-in for application scaling. | Built-in service | Not supported | Built-in service | N/A |
| Load balancer | Azure Load Balancer | Integrated | Azure Load Balancer | Integrated | Azure Load Balancer | Integrated | Azure Load Balancer |
| Scale limit | Platform image: 1000 nodes per VMSS, Custom image: 100 nodes per VMSS | 20 instances, 50 with App Service Environment | 100 nodes per VMSS | Infinite <a href="#note1c">[1]</a> | 100 | No defined limit (200 maximum recommended | 20 core limit by default. Contact customer service for increase. |

| Criteria | Virtual Machine | App Service | Service Fabric | Azure Functions | Azure Container Service | Cloud Services | Azure Batch |
|----------|-----------------|-------------|----------------|-----------------|-------------------------|----------------|-------------|
| SLA | SLA for Virtual Machines | SLA for App Service | SLA for Service Fabric | SLA for Functions | SLA for Azure Container Service | SLA for Cloud Services | SLA for Azure Batch |
| Multi region failover | Traffic manager | Traffic manager | Traffic manager, Multi-Region Cluster | Not supported	 | Traffic manager | Traffic manager | Not Supported |

| Criteria | Virtual Machine | App Service | Service Fabric | Azure Functions | Azure Container Service | Cloud Services | Azure Batch |
|----------|-----------------|-------------|----------------|-----------------|-------------------------|----------------|-------------|
| SSL | Configured in VM | Supported | Supported  | Supported | Configured in VM | Supported  Supported |
| RBAC | Supported | Supported | Supported | Supported | Supported | Not supported | Supported |
| Security Center | Supported | Not supported  | Not supported | Not supported  | Not supported  | Supported | Not supported  |
| Suitable architecture styles | Lift-and-shift, N-Tier | Web Queue Worker | Microservices, Event driven architecture (EDA) | Microservices, EDA | Microservices, EDA | Web Queue Worker | Big Compute |
| Limitations |  | | | | | | |


[function-plans]: /azure/azure-functions/functions-scale