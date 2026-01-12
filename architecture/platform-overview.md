# Platform Overview

## Purpose
This document describes the high-level architecture of the SRE Platform Lab,
including core components, responsibilities, and interaction boundaries.

## High-Level Components
The platform is composed of the following major layers:

- Infrastructure Layer
- Kubernetes Platform Layer
- Platform Services Layer
- Application Workloads
- Operations & Reliability Tooling

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
Shared services consumed by application teams.

Examples:
- Ingress and traffic management
- Certificate management
- Image registry access
- Observability components

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


## Responsibility Boundaries

| Area | Platform Team | Application Team |
|------|---------------|------------------|
| Cluster availability | Yes | No |
| Node OS patching | Yes | No |
| Namespace management | Yes | Partial |
| Application scaling | No | Yes |
| Backup of platform services | Yes | No |
| Application data backup | No | Yes |
