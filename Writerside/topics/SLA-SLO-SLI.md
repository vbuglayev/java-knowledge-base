# SLA, SLO, SLI

In software architecture, **SLA**, **SLO**, and **SLI** are crucial concepts for managing and maintaining service reliability and performance. Each has a specific role in defining and tracking service levels.

## 1. SLA (Service Level Agreement)

A **Service Level Agreement** is a formal contract between a service provider and the end user that defines the level of service expected. It specifies the measurable metrics and guarantees for performance and availability, and often includes penalties or remedies if these levels aren't met.

- **Key Elements of SLA:**
    - **Availability:** Uptime percentage (e.g., 99.9% availability over a month).
    - **Performance:** Metrics like response times, throughput, etc.
    - **Support:** Expected response and resolution times for incidents.
    - **Penalties:** Financial or service credits if the service provider fails to meet the agreed levels.

  **Example:** An SLA might guarantee 99.9% uptime for a cloud service. If that is not met, the provider may offer service credits.

## 2. SLO (Service Level Objective)

A **Service Level Objective** is a specific measurable goal within an SLA. It defines the target performance level a service provider aims to achieve. While the SLA is a contract, the **SLO** is the internal performance benchmark.

- **Key Elements of SLO:**
    - **Target Level:** Defines the performance goal, such as 99.9% uptime or an average response time of 200ms.
    - **Measurement Period:** The period over which the SLO is measured, such as monthly or quarterly.
    - **Scope:** Can apply to specific aspects like uptime, error rate, or latency.

  **Example:** An SLA might require 99.9% uptime, while an SLO could set a stricter internal goal of 99.95% uptime for a critical service within the same period.

## 3. SLI (Service Level Indicator)

A **Service Level Indicator** is the actual measured value of a system’s performance or reliability. SLIs track real-time metrics that assess how well the service is performing in relation to the SLO.

- **Key Elements of SLI:**
    - **Measurable Metric:** Metrics like response time, error rate, availability, or throughput.
    - **Observed Performance:** SLIs reflect the real-time performance of the system, which can be evaluated against the SLO.

  **Example:** A metric like "average response time over the last hour was 180ms" is an SLI. This data can be compared against the SLO, which might require the response time to be below 200ms 99% of the time.

## Relationship Between SLA, SLO, and SLI

- **SLI**: Measures the performance of the system in real time.
- **SLO**: Defines a target threshold for SLIs over a specific time period.
- **SLA**: The contractual agreement outlining the overall expectations and consequences.

### Example Scenario:

Let’s assume you're running a cloud service:
- **SLI**: The system records 99.93% uptime over the last month.
- **SLO**: The internal goal is to achieve 99.95% uptime.
- **SLA**: The contract guarantees 99.9% uptime to the customer.

In this case, you met the **SLA** (99.93% > 99.9%) but failed to meet the **SLO** (99.93% < 99.95%).

## Usage in Software Architecture

1. **Monitoring & Observability**: SLIs are tracked in real-time to monitor system performance. Tools like Prometheus, Grafana, or CloudWatch can be used to measure SLIs.
2. **Defining Acceptable Performance**: SLOs are used internally to define acceptable performance. They help development teams and Site Reliability Engineers (SREs) prioritize work.
3. **Contracts with Clients**: SLAs are customer-facing contracts that ensure mutual understanding and accountability between service providers and customers.

## Summary

- **SLAs** are customer-facing contracts.
- **SLOs** are internal goals to achieve the SLA.
- **SLIs** are real-time metrics to track whether the SLOs and SLAs are being met.
