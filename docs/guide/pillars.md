# Pillars of Software Quality 

## Scalability

Scalability is the ability of a system to handle increased load. There are two main ways that an application can scale:

- Scaling up, also called vertical scaling, means increasing the capacity of a resource. For example, using a larger VM size or a larger database.
- Scaling out, also called horizontal scaling, means adding new instances of a resource, whether VMs, message queues, or database replicas. 

Horizontal scaling has significant advantages over vertical scaling:

- True cloud scale. Applications can be designed to run on hundreds or even thousands of nodes, reaching scales that are not possible on a single node.
- Horizontal scale is elastic, meaning you can add more instances if load increases, or remove them during quieter periods.
- Scaling out can be triggered automatically, either on a schedule or in response to changes in load. 
- Scaling out may be cheaper than scaling up. Running several small VMs can cost less than a single large VM. 
- Horizontal scaling can also improve resiliency, by adding redundancy. If an instance goes down, the application keeps running.

An advantage of vertical scaling is that you can do it without making any changes to the application. But at some point you'll hit a limit, where you can't scale any up any more. At that point, any further scaling must be horizontal. 

Horizontal scale must be designed into the system from the start. For example, you can scale out VMs by placing them behind a load balancer. But then each VM in the pool must be able to handle any client request, so the application must be stateless or store state externally (say, in a distributed cache). Managed PaaS services often have horizontal scaling and auto-scaling built in. The ease of scaling these services is a  major advantages of using managed services.

Just adding more instances doesn't mean an application will scale, however. It may simply push the bottleneck somewhere else. For example, if you scale a web front-end to handle more client requests, that might trigger lock contentions in the back-end database. You would then need to consider additional measures, such as optimistic concurrency or data partitioning, to enable more throughput to the database.

Always conduct performance and load testing to find these potential bottlenecks. The stateful parts of a system, such as databases, are the most common cause of bottlenecks, and require careful design in order to scale horizontally. Resolving one bottleneck may reveal other bottlenecks elsewhere.

### Scalability guidance


- [Design patterns for scalability and performance][scalability-patterns]
- Performance anti-patterns
- [Best practices: Autoscaling][autoscale]
- [Best practices: Background jobs][background-jobs]
- [Best practices: Caching][caching]
- [Best practices: CDN][cdn]
- [Best practices: Data partitioning][data-partitioning]
- [Scalability checklist][scalability-checklist] 

## Availability

Availability is the proportion of time that the system is functional and working. It is usually measured as a percentage of uptime.  Application errors, infrastructure problems, malicious attacks, and system load can all reduce availability. Resiliency, described in the next section, is closely related to availability.

A cloud application should have a service level objective (SLO) that clearly defines the expected availability, and how the availability is measured. When defining availability, look at the critical path. If the web front-end is handling client requests, but every transaction fails because it can't connect to the database, the application is not available to users. 

Availability is ofen described in terms of "9s" &mdash; for example, "four 9s" means 99.99% uptime. The following table shows the potential cumulative downtime at different availability levels.

| % Uptime | Downtime per week | Downtime per month | Downtime per year |
|----------|-------------------|--------------------|-------------------|
| 99% | 1.68 hours | 7.2 hours | 3.65 days |
| 99.9% | 10.1 minutes | 43.2 minutes | 8.76 hours |
| 99.95% | 5 minutes | 21.6 minutes | 4.38 hours |
| 99.99% | 1.01 minutes | 4.32 minutes | 52.56 minutes |
| 99.999% | 6 seconds | 25.9 seconds | 5.26 minutes |

Notice that 99% uptime could translate to an almost 2-hour service outage per week. For many applications, especially consumer-facing applications, that is not an acceptable SLO. On the other hand, five 9s (99.999%) means no more than 5 minutes of downtime in a *year*. It's challenging enough just detecting an outage that quickly, let alone resolving the issue. To get very high availability (99.99% or higher), you can't rely on manual intervention to recover from failures. The application must be self-diagnosing and self-healing, which is where resiliency becomes crucial.

In Azure, the Service Level Agreement (SLA) describes Microsoft's commitments for uptime and connectivity. If the SLA for a particular service is 99.9%, it means you should expect the service to be available 99.9% of the time.

### Availability guidance

- [Design patterns: Availability][availability-patterns]
- [Best practices: Autoscaling][autoscale]
- [Best practices: Background jobs][background-jobs]
- [Availability checklist][availability-checklist] 

## Resiliency

Resiliency is the ability of the system to recover from failures and continue to function. The goal of resiliency is to return the application to a fully functioning state after a failure occurs.

In traditional application development, there has been a focus on reducing mean time between failures (MTBF). Effort was spent trying to prevent the system from failing. In cloud computing, a different mindset is required. 

- Distributed systems are complex, and a failure at one point can potentially cascade throughout the system.
- Costs for cloud environments are kept low through the use of commodity hardware, so occasional hardware or network failures must be expected. 
- Applications depend on external services, which may become temporarily unavailable or throttle high-volume users. 

Moreover, in an online world, users expect an application to be available 24/7 without ever going offline. All of these factors mean that cloud applications must be designed to expect occasional failures and recover from them.  

When designing an application to be resilient, you must understand your availability requirements. How much downtime is acceptable? This is partly a function of cost. How much will potential downtime cost your business? How much should you invest in making the application highly available?

Resiliency can be applied at all levels of the architecture. Some mitigations can be describes as more tactical in nature &mdash; for example, retrying a remote call after a transient network failure. Other mitigations are more strategic, such as failing over the entire application to a secondary region. Tactical mitigations can make a big difference. It's rare for an entire region to experience a disruption. Transient issues such as network congestion are more common &mdash; target these first. Having the right monitoring and diagnostics is also important, both to detect failures when they happen, and to find the root causes.

### Implementing resiliency

Resiliency guidance - provides a structured approach to planning and implementing resiliency
Design principles:
- Design for self healing
- Make all things redundant
- Design for operations
- Build for the needs of the business

Design patterns

Best practices
- Transient fault handling
- Retry guidance

Resiliency checklist

## Manageability / DevOps


Design for operations
Best practices:
Monitoring and diagnostics
Naming conventions
Management and monitoring patterns
DevOps Checklist

<!-- links -->

<!-- principles -->
[coordination]: ./design-principles/minimize-coordination.md
[needs-of-business]: ./design-principles/build-for-business.md
[partition]: ./design-principles/partition.md
[redundant]: ./design-principles/redundancy.md
[scale-out]: ./design-principles/scale-out.md
[self-healing]: ./design-principles/self-healing.md


<!-- patterns -->
[scalability-patterns]: ../patterns/category/performance-scalability.md
[availability-patterns]: ../patterns/category/availability.md

<!-- practices -->
[autoscale]: ../best-practices/auto-scaling
[background-jobs]: ../best-practices/background-jobs.md
[caching]: ../best-practices/caching.md
[cdn]: ../best-practices/cdn.md
[data-partitioning]: ../best-practices/data-partitioning.md

<!-- checklist -->
[availability-checklist]: ../checklist/availability.md
[scalability-checklist]: ../checklist/scalability.md