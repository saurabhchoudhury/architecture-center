# Compute options

<table>
<tr><th>Criteria</td><th>Virtual Machines</th><th>Cloud Service</th><th>Service Fabric</th><th>App Service</th><th>Azure Functions</th><th>Azure Container Service</th><th>Azure Batch</th></tr>
<tr><th colspan="8">Hosting model</th></tr>
<tr><td>Application composition</td><td>Agnostic</td><td>Roles</td><td>Services</td><td>Application</td><td>Function</td><td>Agnostic</td><td>Scheduled jobs </td></tr>
<tr><td>Density</td><td>1 application per VM</td><td>One role instance per VM</td><td>Multiple services per VM</td><td>Multiple apps per instance</td><td>No dedicated instances <a href="#note1">[1]</a></td><td>Multiple containers per VM</td><td>Multiple apps per VM</td></tr>
<tr><td>Minimum number of instances</td><td>1 <a href="#note2">[2]</a></td><td>2</td><td>5 <a href="#note3">[3]</a></td><td>1</td><td>N/A <a href="#note1">[1]</td><td>3</td><td>1  <a href="#note4">[4]</a></td></tr>
<tr><td>State management</td><td>Stateless or Stateful</td><td>Stateless</td><td>Stateless or stateful</td><td>Stateless</td><td>Stateless</td><td>Stateless or Stateful</td><td>Stateless</td></tr>
<tr><td>Web hosting</td><td>Agnostic</td><td>Built-in (IIS)</td><td>Self-host<br/>IIS in containers</td><td>Built in</td><td>Not applicable</td><td>Agnostic</td><td>None</td></tr>
<tr><td>OS</td><td>Windows, Linux</td><td>Windows</td><td>Windows, Linux [preview]</td><td>Windows, Linux [preview]</td><td>N/A</td><td>Windows, Linux</td><td>Windows, Linux</td></tr>
<tr><td>Dedicated network</td><td>Supported</td><td>Supported</td><td>Supported</td><td>Supported <a href="#note5">[5]</td><td>Not supported</td><td>Supported</td><td>Supported</td></tr>
<tr><td>Hybrid connectivity</td><td>Supported</td><td>Supported</td><td>Supported</td><td>Supported <a href="#note6">[6]</td><td>Not supported</td><td>Supported</td><td>Supported</td></tr>
<tr><td colspan="8">DevOps</td></tr>
<tr><td>Programming model</td><td>Agnostic</td><td>Web role, worker role</td><td>Guest executable, Service model, Actor model, Containers</td><td>Web application, WebJobs for background tasks</td><td>Functions with triggers</td><td>Agnostic</td><td>Command line application</td></tr>
<tr><td>Local debugging</td><td>Agnostic</td><td>Local emulator</td><td>Local node cluster</td><td>IIS Express, others <a href="#note7">[7]</td><td>Azure Functions CLI</td><td>Local container runtime</td><td>Not supported</td></tr>
<tr><td>Deployment</td><td>Resource Manager</td><td>Resource manager, Classic</td><td>Resource Manager</td><td>Resource Manager</td><td>Resource Manager</td><td>Resource Manager</td><td>Resource Manager</td></tr>
<tr><td>Application update</td><td>No built-in support</td><td>VIP swap or rolling update<td>Rolling upgrade (per service)</td><td>Deployment slots</td><td>No built-in support</td><td>Depends on orchestrator. Most support rolling updates.</td><td>N/A</td></tr>
<tr><th colspan="8">Scalability</th></tr>
<tr><td>Auto-scaling</td><td>VM scale sets</td><td>Built-in service</td><td>VM Scale Sets. Built-in for application scaling.</td><td>Built-in service</td><td>Built-in service</td><td>Not supported</td><td>N/A</td></tr>
<tr><td>Load balancer</td><td>Azure Load Balancer</td><td>Integrated</td><td>Azure Load Balancer</td><td>Integrated</td><td>Integrated</td><td>Azure Load Balancer</td><td>Azure Load Balancer</td></tr>
<tr><td>Scale limit</td><td>Platform image: 1000 nodes per VMSS<br/>Custom image: 100 nodes per VMSS</td><td>No defined limit. 200 maximum recommended</td><td>100 nodes per VMSS</td><td>20 instances<br/>50 with App Service Environment</td><td>Infinite <a href="#note8">[8]</a></td></tr>
<tr><td>100</td><td>20 core limit by default. Contact customer service for increase.</td></tr>
<tr><td colspan="8">Availability</td></tr>
<tr><td>SLA</td><td>SLA for Virtual Machines</td></tr>
<tr><td>SLA for Cloud Services</td><td>SLA for Service Fabric</td><td>SLA for App Service</td><td>SLA for Functions</td><td>SLA for Azure Container Service</td><td>SLA for Azure Batch</td></tr>
<tr><td>Multi region failover</td><td>Traffic manager</td><td>Traffic manager</td><td>Traffic manager</td></tr>
<tr><td>Multi-Region Cluster</td><td>Traffic manager</td><td>Not supported	</td><td>Traffic manager</td><td>Not Supported</td></tr>
<tr><td>Security</td></tr>
<tr></tr>
<tr><td>SSL</td><td>Configured in VM</td><td>Supported</td></tr>
<tr><td>Supported </td><td>Supported</td><td>Supported</td><td>Configured in VM</td><td>Supported</td></tr>
<tr><td>Supports RBAC?</td><td>Yes</td><td>No</td><td>Yes</td><td>Yes</td><td>Yes</td><td>Yes</td><td>Yes</td></tr>
<tr><td>Security Center</td><td>Supported</td><td>Supported</td><td>Not supported</td><td>Not supported </td><td>Not supported </td><td>Not supported </td><td>Not supported </td></tr>
<tr><td>Others</td><td>Suitable architecture styles</td><td>Lift and Shift</td></tr>
<tr><td>N-Tier+</td><td>Web Queue Worker</td><td>Microservices</td></tr>
<tr><td>EDA</td><td>Web Queue Worker</td><td>Microservices</td></tr>
<tr><td>EDA</td><td>Microservices</td></tr>
<tr><td>EDA</td><td>Asynchronous Task Batch Processing</td></tr>
<tr><td>Limitations</td><td>VM requires more management tasks such as patching OS, antimalware/antivirus updates, etc...</td><td>Cloud services </td></tr>
<tr><td>require a gateway to communicate with applications deployed via ARM. RBAC is not supported. </td></tr>
<tr><td>ASP.NET applications.must be self-hosted or run on IIS in a container.</td></tr>
<tr><td>It requires ASE for dedicated VNet. Application can scale up to 20 instance. It requires ASE to go beyond that. </td><td>Don’t use to run long running operations. Decompose it into smaller functions that work together.</td></tr>
<tr><td>It supports these triggers </td><td>Orchestrator upgrade is not supported.</td><td>(Limits on # of nodes </td></tr>
</table>

<span id=note1>1.</span> If using Consumption plan. If using App Service plan, functions run on the VMs allocated for your App Service plan. For more information, see .

<span id=note2>2.</span> Higher SLA with 2 or more instances

<span id=note3>3.</span> For production environments

<span id=note4>4.</span> Can scale down to zero after job completes

<span id=note5>5.</span> Requires ASE

<span id=note6>6.</span> Requires ASE or BizTalk Hybrid Connections

<span id=note7>7.</span> Options include: IIS Express for ASP.NET or node.js (iisnode); PHP web server; Azure Toolkit for IntelliJ, Azure Toolkit for Eclipse. App Service also supports remote debugging of deployed web app.
