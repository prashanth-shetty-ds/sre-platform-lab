# Platform Overview

## Purpose
This platform enables multiple application teams to deploy reliable, scalable workloads with:

- Predictable change control
- Secure multi-tenant isolation
- Robust life-cycle and disaster recovery support

## High-Level Components
The platform is composed of the following major layers:

- Infrastructure Layer
- Kubernetes Platform Layer
- Platform Services Layer
- Application Workloads
- Operations & Reliability Tooling

## Context Diagram

         +------------------------------+
         |  Platform Control Plane      |
         | (K8s API, etcd, auth, etc.)   |
         +-------------+----------------+
                       |
       +---------------+------------------+
       | Kubernetes Worker Nodes (Pods)   |
       | - Platform services              |
       | - App workloads                  |
       +---------------+------------------+
                       |
        +-------------------------------+
        | External Traffic (Ingress)     |
        | Internal Services / APIs       |
        +-------------------------------+

## Infrastructure Layer
The infrastructure layer provides compute, storage, and networking resources.
It is designed to support high availability, predictable performance, and
safe maintenance operations.

Responsibilities:
- Compute and storage provisioning
- Network connectivity and isolation
- Hardware and hypervisor lifecycle management

## Kubernetes Platform Layer
This layer provides the container orchestration and scheduling capabilities.

Responsibilities:
- Cluster lifecycle management
- Node health and availability
- Resource isolation and quotas
- Secure API access

## Platform Services Layer

Shared services offered to teams with operational SLAs:

- Ingress Controller (managed TLS termination)
- Central logging (aggregated to Grafana/Loki)
- Metrics collection (Prometheus)
- Internal image registry (with vulnerability scanning)

**Non-Goals for this layer**
- Hosting customer workloads outside the cluster
- Arbitrary tooling without documented ownership

## Application Workloads
Business and platform workloads deployed by application teams.

Responsibilities:
- Application logic
- Service-level objectives
- Application-specific scaling policies

## Operations & Reliability Tooling
Tooling used by the platform team to ensure reliability.

Examples:
- Monitoring and alerting
- Backup and recovery
- Incident response workflows

## Non-Functional Requirements

| Category | Requirement |
|----------|-------------|
| Reliability | 99.95% platform uptime |
| Performance | API latency < 150ms p95 |
| Security | All TLS > 1.2, CIS Benchmarks enforced |
| Scalability | Support 50+ teams/namespaces |
| Observability | Defined SLIs/SLAs |

## Responsibility Boundaries

| Responsibility                   | Platform Team | App Team |
|----------------------------------|:-------------:|:--------:|
| Cluster provisioning             | ✓             |          |
| Automated patching               | ✓             |          |
| Namespace provisioning           | ✓             |          |
| App config / scaling policies    |               | ✓        |
| App data backup                  |               | ✓        |
| Platform service alerts/SLIs     | ✓             |          |
| App specific error budgets       |               | ✓        |

