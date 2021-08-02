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

### Security
Security is a crucial consideration for any application. For cloud native applications especially, there are some particular concerns:

- The application may run on a shared resource environment, like a cloud provider, where there is no direct control of the underlying hardware or network.
- The application may transmit sensitive data, including Personally Identifiable Information (PII), between services.
- The application may be subject to regulatory requirements around confidentiality of data at rest and in transit.
- There may be other internal requirements around security best practices.
One increasingly common approach to communication security in a cloud environment is the "zero-trust" approach. While a full treatment of zero-trust security is outside the scope of this class, the core goal is to shrink the security boundary of the application to as small and granular a level as possible. For example, rather than having a firewall around a datacenter that enforces security of incoming security, each application in the datacenter might enforce this itself. This zero-trust approach is a natural fit for cloud environments, where the underlying hardware and network infrastructure is not under your control.

The Linkerd security model follows the zero-trust approach by providing transparent mutual TLS communication between services. Mutual TLS (mTLS) is a form of transport security that provides both confidentiality and authentication of communication. In other words, not only is the communication encrypted, but the identity is validating on both sides of the connection. Linkerd implements this at the level of individual Kubernetes pods, allowing each pod to create its own security boundary.

There's a lot more to say about security and we will cover it in greater detail later in the course. For now, it's enough to know that Linkerd will automatically encrypt and decrypt the communication between your services when it is responsible for handling the traffic, will authenticate the identity of both, and will do so in a way that requires no configuration on your part—it's on by default.

One final benefit of this feature is that the business logic in the services no longer has the burden of managing certificates and TLS connections. That means less code to write!

### Reliability

Every distributed system must deal with the concept of failure: components can die, networks can "partition" (lose connectivity between nodes), and so on. Generally speaking, a reliable application is one that can successfully serve responses even in the presence of partial failures of some of its components or underlying platform.

Linkerd provides several mechanisms for automatically enhancing the reliability of applications:

- Retries
Linkerd can be configured to automatically retry requests that have failed for a particular request.
- Timeouts
When a service takes too long to reply, Linkerd will use a configurable timeout to send an error back to the client instead of waiting indefinitely for the service to respond.
- Load balancing
Linkerd uses an exponentially weighted moving average algorithm (EWMA) to load balance requests across instances of services, based on latency. We'll explore this in detail later. The main idea to take away is that this functionality distributes traffic evenly across all instances of a service, based on the latency in the response times from each service, thereby ensuring that no one service receives more requests than it can handle.
- Traffic shifting
Linkerd provides tools that allow operators to employ sophisticated deployment strategies such as canary releases and blue-green deploys. These techniques can help reduce the risk of introducing new code into a production environment.

