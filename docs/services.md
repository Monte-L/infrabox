# InfraBox - Service Review

## Host Context
This InfraBox project is being built on a reused Debian system whose current hostname remains 'Kiroshi'.

## Primary Project Focus
THe main objective of InfraBox is to build a private Linux infraestructure server with monitoring,
containerized services, backup routines, and secure remote access.

## Auxiliary Services

### Samba
Status: kept for now

Reason:
Samba may still be used as an auxiliary file sharing service during the project.

Role:
Optional file sharing service inherited from a previous Linux project.

Current state:
Samba is active and configured as an standalone server with an existing shared directory.

Decision: Samba will not be removed at this stage. Its long-term role will be reviewed later based on
actual usage.

### Nginx
Status: under review

Reason:
Nginx was inherited from a previous project and may be replaced or reconfigured later as part of the
InfraBox architecture.

Current state:
Nginx is active, enabled, and listening on port 80. Existing inherited site configuration includes
'default' and 'lab.local'.

Decision:
Nginx will not be removed at this stage. It remains under review and may later be reconfigured
or replaced as part of the InfraBox architecture.

### samba-ad-dc
Status: inherited but not in use

Reason:
The service exists in the system but is inactive and does not appear to be required for the current
standalone Samba setup.

Decision:
No action will be taken at this stage. The service may be disabled or removed later if confirmed 
unnecessary.
