# InfraBox - Day 7

## Project Name
InfraBox

## Current Hostname
Kiroshi

## Component Installed
Prometheus Node Exporter

## Installation Method
APT package installation on the Debian host

# Service Status
 - prometheus-node-exporter.service active
 - prometheus-node-exporter.service enabled

## Listening Port
 - 9100/tcp

## Metrics Endpoint Validation
 - 'http://127.0.0.1:9100/metrics' responded successfully
 - 'http://192.168.10.10:9100/metrics' responded successfully

## Metrics Reviewed

### Memory Metric
 - 'node_memory_MemAvailable_bytes'
 - Type: gauge
 - Meaning: currently available memory in bytes

### CPU Metric
 - 'node_cpu_seconds_total'
 - Type: counter
 - Meaning: cumulative CPU times spent in each mode

### Filesystem Metric
 - 'node_filesystem_avail_bytes'
 - Type: gauge
 - Meaning: available filesystem space in bytes

## Notes
Day 7 introduced host-level metrics collection through Node Exporter. The '/metrics' endpoint was validated successfully, 
and sample memory, CPU, and filesystem metrics were reviewed in Prometheus text exposition format.

## Prometheus Scrape Connectivity Issue
The initial Prometheus scrape target remained down even though Node Exporter was active and reachable from the host.

### Root Cause
The host firewall rule initially allowed the wrong Docker source network.

### Resolution
The firewall was updated to allow TCP port 9100 from the actual Docker network used by the Prometheus container.

### Result
After correcting the firewall rule, the Prometheus 'node' target changed to 'UP'.

## Prometheus Validation

### Target Status
 - 'node' target reached 'UP' state after correcting the firewall rule for the actual Docker bridge network.

### Basic Queries Tested
 - 'up'
 - 'node_memory_MemAvailable_bytes'
 - 'node_filesystem_avail_bytes'
 - 'node_cpu_seconds_total'
 - 'node_filesystem_avail_bytes{mountpoint="/"}'
 - 'up{job="node"}'

### Query Learning Outcome
These initial queries confirmed that:
 - Prometheus was scraping the host metrics successfully
 - labels provided context for each metric series
 - filesystem and CPU metrics exposed multiple labeled series
 - filtering by label reduced the result set to more specific values
