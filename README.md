# Windows Gaming Metrics

A gaming-focused observability and telemetry project for monitoring a Windows
gaming PC and, eventually, dedicated game servers.

This repository focuses on Windows-side telemetry, gaming metrics, PromQL
learning, verification procedures and future gaming-specific integrations.

## Observability platform

Metrics from this project are collected, stored and visualized by the shared
Prometheus and Grafana stack maintained in
[Platforms Lab](https://github.com/Xeals-Senpai/platforms-lab).

Platforms Lab is the source of truth for:

- Prometheus deployment and scrape configuration
- Grafana deployment and data-source provisioning
- Grafana dashboard provisioning
- Persistent monitoring storage
- Shared alerting infrastructure

This repository does not deploy a separate Prometheus or Grafana instance.

## Architecture

```text
Windows gaming PC
    |
    | Windows Exporter metrics
    | http://localhost:9182/metrics
    v
Platforms Lab Prometheus
    |
    | PromQL
    v
Platforms Lab Grafana
    |
    v
Windows Gaming dashboards
```

Prometheus runs inside Docker and reaches Windows Exporter through:

```text
host.docker.internal:9182
```

## Repository responsibilities

### Windows Gaming Metrics

This repository owns:

- Windows gaming telemetry documentation
- Windows Exporter requirements and collector information
- Gaming-focused PromQL examples
- Host-side verification procedures
- Future gaming and process telemetry integrations
- Future Windows-side scripts and utilities

### Platforms Lab

The Platforms Lab repository owns:

- Prometheus and Grafana infrastructure
- Prometheus scrape targets
- Grafana data sources
- Provisioned dashboards and dashboard folders
- Monitoring data persistence
- Shared alerting configuration

The repositories remain independent and are connected operationally through
the Windows Exporter HTTP endpoint. They do not use a Git submodule.

## Current environment

The initial Windows gaming PC uses:

- Windows 11 Home
- AMD Ryzen 7 5800
- AMD Radeon RX 6800 XT
- Docker Desktop with WSL 2
- Windows Exporter on port `9182`

The following Windows Exporter collectors are currently enabled:

- `cpu`
- `logical_disk`
- `memory`
- `net`
- `os`
- `physical_disk`
- `service`
- `system`

## Current status

Verified:

- Windows Exporter runs as an automatically started Windows service
- The local metrics endpoint returns HTTP `200`
- Docker containers can reach the exporter through `host.docker.internal:9182`
- Required CPU, memory, disk and network collectors complete successfully
- Platforms Lab contains an existing Prometheus scrape target for Windows
- Platforms Lab provisions Prometheus as the default Grafana data source

Still to complete:

- Verify the Windows target is `UP` in the running Prometheus instance
- Develop and test gaming-focused PromQL queries
- Create a separate provisioned `Windows Gaming` Grafana folder
- Create the initial Windows gaming dashboard
- Add persistent storage for Prometheus and Grafana
- Complete end-to-end verification and troubleshooting documentation

## Planned work

The project will grow incrementally through:

1. CPU, memory, disk and network monitoring
2. Gaming-focused Grafana dashboards
3. AMD GPU and hardware temperature telemetry
4. Network latency and packet-loss monitoring
5. Prometheus recording rules and alerting
6. Game and process telemetry
7. Dedicated game-server monitoring
8. Reproducible setup, recovery and upgrade procedures

Semantic version numbers will be assigned when creating verified GitHub
release tags.

## Related project

See [Platforms Lab](https://github.com/Xeals-Senpai/platforms-lab) for the
infrastructure that deploys and provisions the shared Prometheus and Grafana
stack.