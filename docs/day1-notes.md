#Infrabox - Day 1

## Project Name
InfraBox

## Hostname
Kiroshi

## User
lucas

## Hardware Model
ThinkPad T480

## Operation System
Debian GNU/Linux 13 (trixie)

## Network Interface
 - enp0s31f6
 - wlp3s0

## Local IP Address
 - 192.168.10;10
 - 10.197.254.125

## Default Route
 - wlp3s0 via 10.197.254.177

## SSH Authentication
 - PermitRootLogin no
 - PubkeyAuthentication yes
 - PasswordAuthentication no
 - UsePAM yes

## SSH Service Status
 - active
 - enabled

## Firewall Status
UFW active

## Allowed Firewall Rules
 - 22/tcp
 - 80/tcp (Nginx HTTP)
 - 137,138/udp (Samba)
 - 139,455/tcp (Samba)

## Project Structure
 - /opt/infrabox/backups
 - /opt/infrabox/compose
 - /opt/infrabox/docs
 - /opt/infrabox/scripts

## Notes
This system is not a clean baselina. It already contains inherited configuration from a previus Linux project, including SSH hardening,
UFW rules, Nginx, and Samba-related services.
The InfraBox project will continue from this reused baseline instead of starting from scratch.
Samba will be kept for now as an optional auxilary service.
