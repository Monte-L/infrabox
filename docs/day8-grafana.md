# InfraBox - Day 8

## Project Name
InfraBox

## Current Hostname
Kiroshi

## Component Installed
Grafana

## Deployment Method
Docker Compose with persistent host volume

## Listening Port
 - 3000/tcp

## Startup Issue
The Grafana container initially entered a restart loop due to insufficient write permissions on the host-mounted data directory.

## Resolution
Ownership/permissions of the persistent Grafana data directory were corrected, allowing the service to start successfully.

## Data Source Configuration
 - Prometheus added as Grafana data source
 - connection validated successfully

## Dashboard Created

### InfraBox Host Overview

### Panels
 - Available Memory
 - Root Filesystem Available
 - CPU Busy
 - Host Uptime

## Notes
Day 8 completed the first full observability visualization layer of the project. Host metrics exposed by Node Exporter
and collected by Prometheus were successfully visualized in Grafana through a basic host overview dashboard.
