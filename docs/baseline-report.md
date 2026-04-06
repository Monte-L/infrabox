# InfraBox - Baseline Report

## Project Identity

### Project Name
InfraBox

### Current Hostname
Kiroshi

### Host Context
This InfraBox project is being built on a reused Debian system whose current hostname remains 'Kiroshi'.

---

## System Identity

### User
lucas

### Hardware Model
ThinkPad T480

### Operating System
Debian GNU/Linux 13 (trixie)

---

## Network Configuration

### Network Interfaces
 - enp0s31f6
 - wlp3s0

### Local IP Addresses
 - 192.168.10.10/24 on enp0s31f6
 - 10.197.254.125/24 on wlp3s0

### Default Route
 - via 10.197.254.177 dev wlp3s0

### Notes
The system currently has both Ethernet and Wi-Fi interfaces active.
The default outbound route is using the Wi-Fi interface.

---

## SSH Configuration

### Authentication Model
 - PermitRootLogin no
 - PubkeuAuthentication yes
 - PasswordAuthentication no
 - UsePAM yes

### Service Status
 - ssh.service active
 - ssh.service enabled

### Notes
SSH is already hardened from a previus project and currently accepts public key authentication only.

---

## Firewall Configuration

### UFW Status
active

### Default Policy
 - deny incoming
 - allow outgoiing
 - disable routed

### Allowed Rules
 - 22/tcp
 - 80/tcp (Nginx HTTP)
 - 137,138/udp (Samba)
 - 139,445/tcp (Samba)

### Notes
The firewall is active and already configured. Some rules were inherited from a previous project.

---

## Nginx Review

### Service Status
 - nginx.service active
 - nginx.service enabled

### Listening Ports
 - 0.0.0.0:80
 - [::]:80

### Existing Site Configuration
 - default
 - lab.local

### Assessment
Nginx is active and serving on port 80. It contains inherited site configuration from a previous project
and is currently under review for reuse or replacement within the InfraBox architecture.

---

## Samba Review

### Service Status
 - smbd.service active
 - nmbd.service active
 - samba-ad-dc.service inactive

### Server Role
 - ROLE_STANDALONE

### Existing Share
 - [labshare]
 - path = /home/lucas/lab/share
 - valid users = lucas

### Assessment
Samba is functional and currently configured as a standalone file sharing serivce. It will be kept as an
auxiliary service during the InfraBox project.

### Addiotional Note
The 'samba-ad-dc' service is present but inactive and does not appear to be required for the current
standalone file sharing setup.

---

## Enabled Inherited Services

 - nginx.service
 - smbd.service
 - nmbd.service
 - samba-ad-dc.service
 - ssh.service
 - ufw.service
 - cron.service
 - NetworkManager.service

### Additional Desktop-Related Services
 - lightdm.service
 - bluetooth.service
 - cups-browsed.service
 - avahi-daemon.service
 - ModemManager.service

---

## Project Structure

 - /opt/infrabox/backups
 - /opt/infrabox/compose
 - /opt/infrabox/docs
 - /opt/infrabox/scripts

---

## Assessment
This system is not a clean baseline. It is a reused Debian workstation/server environment inherited from a
previous Linux project.

### Reused Components Worth Keeping
 - SSH hardening
 - UFW baseline
 - cron
 - NetworkManager
 - existing projet structure
 - Samba auxiliary file sharing service

### Services Under Review
 - nginx
 - samba-ad-dc
 - desktop-related convenience services

### Current Decision
Samba will be kept for now as an optional auxiliary service.
Nginx will remain under review for future reuse or replacement.
The current hostname 'Kiroshi' will be intentionally maintained.
