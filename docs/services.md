# InfraBox - Service Review

## Host Context
InfraBox is being built on a reused Debian host whose current hostname intentionally remains **Kiroshi**.

## Primary Project Focus
The main goal of InfraBox is to build a private Linux infrastructure lab focused on:
- service validation
- monitoring and observability
- containerized infrastructure tools
- structured troubleshooting documentation

## Active Host Services

### OpenSSH
**Status:** active and in use

**Role:** remote administration and secure shell access to the Debian host.

**Current state:** SSH is enabled, running, listening on port 22, and validated through both local checks and Uptime Kuma monitoring.

**Decision:** keep enabled as a core infrastructure service.

---

### Nginx
**Status:** active and in use

**Role:** local HTTP service used for web service validation and monitoring practice.

**Current state:** Nginx is enabled, running, listening on port 80, and responding correctly to local HTTP requests. It is also monitored through Uptime Kuma.

**Decision:** keep enabled as a validated HTTP service in the lab.

---

### Samba
**Status:** active and kept as auxiliary service

**Role:** optional SMB file sharing service for local network access and monitoring validation.

**Current state:** Samba remains active as a standalone service and is currently included in monitoring checks.

**Decision:** keep for now as an auxiliary service while it remains useful in the lab.

---

### Node Exporter
**Status:** active and in use

**Role:** expose host-level metrics for Prometheus collection.

**Current state:** Node Exporter runs directly on the Debian host, listens on port 9100, and provides metrics successfully scraped by Prometheus.

**Decision:** keep enabled as a core observability component.

## Active Containerized Services

### Uptime Kuma
**Status:** active and in use

**Role:** service availability monitoring.

**Current state:** Uptime Kuma runs in Docker and monitors local SSH, Nginx HTTP, and Samba SMB through the host IP.

**Decision:** keep enabled as the availability monitoring layer of the project.

---

### Prometheus
**Status:** active and in use

**Role:** metrics scraping and time-series storage.

**Current state:** Prometheus runs in Docker, scrapes Node Exporter successfully, and shows the `node` target in `UP` state.

**Decision:** keep enabled as the metrics collection layer of the project.

---

### Grafana
**Status:** active and in use

**Role:** metrics visualization and dashboarding.

**Current state:** Grafana runs in Docker, uses Prometheus as a data source, and provides the **InfraBox Host Overview** dashboard.

**Decision:** keep enabled as the visualization layer of the project.

## Inherited But Not Used

### samba-ad-dc
**Status:** inherited but not in use

**Role:** none in the current InfraBox design.

**Current state:** the service exists in the system but is not part of the active standalone Samba usage model.

**Decision:** leave untouched for now, with possible later removal if confirmed unnecessary.

## Summary
InfraBox currently uses a mixed service model:

- **host services** for core local infrastructure functions
- **containerized services** for monitoring and observability tooling

At the current stage, the active service stack is considered valid and aligned with the project goals.
