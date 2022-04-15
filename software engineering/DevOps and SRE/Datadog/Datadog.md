# Datadog
## Modern Infrastructure
In most cases, the servers, containers and other cloud resources can be thought of as *cattle*. We should focus on aggregate health and performance of services rather than isolated datapoints from your hosts.

Monitoring allows engineering teams to identify and resolve performance issues before they cause problems for end users.

## Collecting the Right Data
Collecting data is cheap, but not having it when you need it can be expensive. We should therefore instrument everything, and collect all the useful data you reasonably can.

Most monitoring data falls into two categories - **metrics** and **events**.

## Metrics
Metrics capture a value pertaining to the system at a specific point in time. They are usually collected at regular intervals to monitor a system's evolution through time.

### Work Metrics
Work metrics indicate the top-level health of your system by measuring its useful output. Examples are query per second, query errors and read query latency.

### Resource Metrics
A sever's resource include CPU, memory, disk and network interfaces. A higher level component such as database can also be a resource if another system requires that component to produce work.

### Events
In contrast to metrics, events are discrete and infrequent occurrences. Example events are **changes** (code release, builds), **alerts** (notifications) and **scaling events** (adding or subtracting hosts).

### Tagging
Because modern infrastructure is a constant flux (auto-scaling servers and containers die as quickly as they are spawned). Instead of monitoring your servers as unique entities, we can aggregate metrics to focus on different services, availability zones, instance types or any other relevant dimensions.

**Tags** are metadata that declare all the scopes attached to a datapoint. They allow us to filter or aggregate your metrics to extract meaningful views.



## Implementations
### [[Datadog Metrics Query with Ruby]]