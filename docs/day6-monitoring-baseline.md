# InfraBox - Day 6

## Project Name
InfraBox

## Current Hostname
Kiroshi

## Monitoring Objective
Establish a simple and reliable service availability baseline for the host system.

## Active Baseline Monitors

### Local SSH
 - Monitor Type: TCP Port
 - Target: 192.169.10.10:22
 - Reason: Validates that the SSH service is reachable on the host.

### Local Nginx HTTP
 - Monitor Type: HTTP(s)
 - Target: http://192.168.10.10
 - Reason: Validates that the local web service is responding over HTTP.

### Local Samba SMB
 - Monitor Type: TCP Port
 - Target: 192.168.10.10:445
 - Reason: Validates that the Samba service is reachable over the SMB port.

## Deferred Monitor

### Uptime Kuma Self-Monitor
 - Status: deferred
 - Reason: self-monitoring through the same instance was not considered reliable for the
current baseline and created unnecessary noise.

## Notes
Day 6 focused on defining a clean monitoring baseline, selecting the correct monitor type
for each service, and organizing the initial service availability checks for the InfraBox
project.

## Monitor Timing Configuration

### Baseline Values
 - Heartbeat Interval: 60 seconds
 - Retries: 1
 - Heartbeat Retry Inverval: 30 seconds

### Rationale
These values were selected to keep the monitoring lightweight, reduce false positives,
and reflect the expected quick response time of local host services.

## Availability vs Performance

### Current Layer
The current monitoring setup focuses on service availability

This means the baseline monitors are designed to anser questions such as:
 - Is the service reachable?
 - Is the port accepting connections?
 - Is the web service responding over HTTP?

### Not Covered Yet
This current monitoring setup does not provide deep host performance metrics such as:
 - CPU utilization
 - memory usage
 - disk usage
 - network throughput
 - historical resource trends

### Future Monitoring Expansion
Deeper host and system performance monitoring will be added later with Prometheus,
Node Exporter, and Grafana.

## Notes
Day 6 focused on defining a clean monitoring baseline, selecting the correct monitor type
for each service, organizing the initial service availability checks, and understanding the
difference between availability checks and deeper performance monitoring.
