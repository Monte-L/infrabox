# InfraBox - Day 5

## Project Name
InfraBox

## Current Hostname
Kiroshi

## Service Deployed
Uptime Kuma

## Deployment Method
Docker Compose

## Compose File Location
/opt/infrabox/compose/uptime-kuma/docker-compose.yml

## Persistent Data Directory
/opt/infrabox/data/uptime-kuma

## Port Mapping
 - host: 3001
 - container: 3001

## Validation Performed
 - compose stack created
 - container started successfully
 - local HTTP access tested
 - container logs reviewed
 - persistent data directory checked

## Notes
Day 5 deployed the first real InfraBox service using Docker Compose. Uptime Kuma was
selected as the first monitoring service because it is simple to validate, useful for
infraesctructure monitoring, and suitable as a baseline service for future monitoring
expansion.

## Self-Monitoring Note

An additional self-monitor was tested for the Uptime Kuma service itself.

Altough the service was confirmed operational through:
 - Docker container health status
 - local port validation
 - direct HTTP response from the host

the self-monitor inside the same monitoring instance was not considered reliable
for the Day 5 baseline and was therefore deferred.

For the current project stage, Uptime Kuma service validation is considered
complete based on container health, local port exposure, and direct HTTP testing from the
host.
