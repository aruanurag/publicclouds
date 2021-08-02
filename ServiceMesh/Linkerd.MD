---
layout: page
title: Service Mesh - Linkerd
---

# Linkerd

## What Does Linkerd Actually Do?

Linkerd provides a lot of features, which can be categorized into three basic categories. These three category make up the key "value props" of a service mesh:

- Observability
Collecting real-time telemetry from the system to infer the health of each of the services.
- Security
Ensuring that communication between services is confidential, authenticated, and authorized.
- Reliability
Ensuring that overall application health is maximized, even in the face of partial failures.

### Observability

The term "observability" has become a common part of any conversation that involves distributed systems and applications. But what exactly does it mean? Wikipedia sums it up quite nicely in its definition:

"... observability is a measure of how well internal states of a system can be inferred from knowledge of its external outputs."

With this definition in mind, we can derive that a service mesh uses the external outputs of the services in a distributed application to infer the state of those services. One common characterization of the operational state of a service is the concept of "The Four Golden Signals", as popularized by Google. Those signals include:

- Latency
The length of time it takes to respond to a request. Since each request can have a different latency, the overall latency for a service is usually characterized by the percentiles of the distribution of the latencies of all requests: P50, P95, P99, etc. For example, the P50 of a service is the 50th percentile, or median, latency of its response times, i.e. the latency at which 50% of responses in the time period were equal to or faster than.
- Traffic
The rate of requests being sent to the service, often displayed as requests-per-second (RPS).
- Errors
The portion of successful responses, measured as a percentage of the overall number of requests.
- Saturation
The amount of resource capacity currently consumed by the application.
