# Windows Gaming Metrics

An observability and telemetry project for monitoring a Windows gaming PC
and, eventually, dedicated game servers.

## Goals

- Learn Prometheus and Grafana through gaming-focused examples
- Monitor Windows system and gaming performance
- Build dashboards and alerts incrementally
- Keep infrastructure reproducible
- Develop through versioned milestones

## Initial architecture

- Windows exporters collect host metrics
- Prometheus stores and queries metrics
- Grafana visualizes the collected data
- Docker Compose runs the monitoring services

## Roadmap

- `v0.1.0` — Basic Windows metrics with Prometheus and Grafana
- `v0.2.0` — Provisioned dashboards
- `v0.3.0` — Gaming-oriented hardware and network metrics
- `v0.4.0` — Alerts and recording rules
- `v0.5.0` — Game and process telemetry
- `v1.0.0` — Reproducible gaming observability stack