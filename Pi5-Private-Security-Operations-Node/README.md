# Pi 5 Private Security Operations Node

## Overview

Built a Raspberry Pi 5 private security operations node for container management, log visibility, host and container log analysis, and private administration.

The goal of this project was to create a more security-focused homelab platform than a basic mini server. Instead of deploying a single service, this lab turned the Pi 5 into a small internal operations node that could support Dockerized tools, security monitoring, and private administration from trusted devices.

This lab demonstrates practical skills in Linux administration, Docker deployment, container management, log analysis, private remote access, and security-focused homelab design.

* * *

## Architecture

Raspberry Pi 5  
↓  
Raspberry Pi OS 64-bit  
↓  
Docker Engine + Docker Compose  
↓  
Portainer + Dozzle + CrowdSec  
↓  
Tailscale private admin access  
↓  
Windows desktop and MacBook administration

Component | Description
--- | ---
Server Hardware | Raspberry Pi 5
Operating System | Raspberry Pi OS 64-bit
Container Platform | Docker Engine
Container Management | Portainer
Log Visibility | Dozzle
Detection Tool | CrowdSec
Private Access | Tailscale
Admin Devices | Windows 11 desktop and MacBook Air
Primary Goal | Build a private internal security/admin node

## Objectives

- Install Docker Engine on a Raspberry Pi 5
- Deploy Portainer for container management
- Deploy Dozzle for real-time log visibility
- Deploy CrowdSec for host and container log analysis
- Install Tailscale for private administration
- Validate secure management from Windows and macOS devices

* * *

## Step 1 — Initial System Preparation

The project began on a Raspberry Pi 5 running Raspberry Pi OS 64-bit. Initial preparation focused on confirming SSH access, updating the operating system, and verifying the platform architecture before installing Docker.

Initial setup included:

- connecting to the Pi 5 through SSH
- updating the operating system
- confirming 64-bit architecture
- preparing the system for Docker installation

### First SSH Login
![First SSH Login](screenshots/01-pi5-first-ssh-login.png)

### System Update
![System Update](screenshots/02-system-update.png)

### OS and Architecture Check
![OS and Architecture Check](screenshots/03-os-and-architecture-check.png)

* * *

## Step 2 — Docker Engine Installation

Docker Engine was installed using Docker’s Debian repository, which is the correct installation path for 64-bit Raspberry Pi OS using Debian arm64 packages.

This phase included:

- removing conflicting packages
- adding Docker’s official GPG key
- adding the Docker apt source
- installing Docker Engine, Buildx, and the Compose plugin
- validating the installation with `hello-world`


### Docker Install Finished
![Docker Install Finished](screenshots/05-docker-install-finished.png)

### Docker Validation
![Docker Validation](screenshots/06-docker-validation.png)

* * *

## Step 3 — Non-Root Docker Access

To improve day-to-day administration, the user account was added to the Docker group so containers could be managed without requiring `sudo` for every command.

### Non-Root Docker Test
![Non-Root Docker Test](screenshots/07-docker-nonroot-test.png)

* * *

## Step 4 — Project Structure

A dedicated project directory was created to organize the node and keep service data and Compose files grouped cleanly.

### Project Folder Structure
![Project Folder Structure](screenshots/08-project-folder-structure.png)

* * *

## Step 5 — Multi-Service Docker Stack

A single Docker Compose file was created to run the core services for the node:

- Portainer
- Dozzle
- CrowdSec

This made the Pi 5 act more like a reusable private operations platform rather than a one-service device.

### Docker Compose File
![Docker Compose File](screenshots/09-docker-compose-file.png)

### Containers Running
![Containers Running](screenshots/10-containers-running.png)

* * *

## Step 6 — Portainer Deployment

Portainer was used as the primary container management interface for the node.

This phase included:

- launching Portainer with persistent storage
- completing first-run setup
- connecting the local Docker environment
- reviewing the management dashboard

### Portainer First Login
![Portainer First Login](screenshots/11-portainer-first-login.png)

### Portainer Dashboard
![Portainer Dashboard](screenshots/12-portainer-dashboard.png)

* * *

## Step 7 — Dozzle Deployment

Dozzle was deployed to provide lightweight real-time visibility into container logs.

This phase included:

- launching the Dozzle container
- mounting the Docker socket
- validating log visibility from running services

### Dozzle Dashboard
![Dozzle Dashboard](screenshots/13-dozzle-dashboard.png)

* * *

## Step 8 — CrowdSec Deployment

CrowdSec was deployed to add a defensive monitoring layer to the node.

This phase included:

- launching CrowdSec in Docker
- persisting CrowdSec data
- mounting host logs
- mounting the Docker socket
- enabling Docker log acquisition
- reviewing `cscli metrics`

### CrowdSec Docker Acquisition
![CrowdSec Docker Acquisition](screenshots/14-crowdsec-docker-acquisition.png)

### CrowdSec Metrics
![CrowdSec Metrics](screenshots/15-cscli-metrics.png)

* * *

## Step 9 — Tailscale Installation on the Pi 5

Tailscale was installed on the Pi 5 to provide a private administration path from trusted client devices.

This phase included:

- installing Tailscale on Linux
- running `tailscale up`
- authenticating through the browser
- verifying private tailnet connectivity

### Tailscale Install
![Tailscale Install](screenshots/16-tailscale-install.png)

### Tailscale Login URL
![Tailscale Login URL](screenshots/17-tailscale-login-url.png)

### Tailscale Status
![Tailscale Status](screenshots/18-tailscale-status.png)

* * *

## Step 10 — Cross-Platform Admin Access

Tailscale was also installed on a Windows desktop and a MacBook Air so both devices could privately administer the Pi 5 over the same tailnet.

This phase included:

- installing the Tailscale client on Windows
- installing the Tailscale client on macOS
- confirming all three devices appeared in the Tailscale Machines page
- validating private SSH access to the Pi 5


### Tailscale Machines Page
![Tailscale Machines Page](screenshots/21-tailscale-machines-page.png)

### Windows SSH to Pi 5 over Tailscale
![Windows SSH to Pi 5 over Tailscale](screenshots/22-windows-ssh-to-pi5-over-tailscale.png)


* * *

## Step 11 — Final Validation

Final validation confirmed that Docker, Portainer, Dozzle, CrowdSec, and Tailscale were all working together as intended on the Pi 5 private security operations node.

### Final Terminal Validation
![Final Terminal Validation](screenshots/24-final-terminal-validation.png)

* * *

## Why This Project Stands Out

This project goes beyond a basic Raspberry Pi server by combining:

- container hosting
- container management
- live log visibility
- host and container log analysis
- private administration

Instead of acting as a single-purpose box, the Pi 5 became a reusable internal security/admin node that can support future homelab services and workflows.

It also creates a stronger separation between:

- internal/private services on the Pi 5
- public/internet-facing services on a VPS

That makes the project feel more intentional and more aligned with real infrastructure and security design.

* * *

## Challenges / Troubleshooting

A few areas required extra attention during the build:

- choosing the correct Docker installation path for Raspberry Pi OS 64-bit
- validating Docker and Compose support on arm64
- organizing persistent service data cleanly
- understanding Docker socket exposure for Portainer and Dozzle
- mounting the correct log sources into CrowdSec
- confirming Tailscale enrollment and private SSH access from multiple devices

These troubleshooting steps helped reinforce Linux administration, Docker operations, service deployment, and private access design concepts.

* * *

## What I Learned

- Raspberry Pi 5 is capable of acting as a practical always-on internal security/admin node
- Docker on Raspberry Pi OS 64-bit should follow the Debian arm64 path
- Portainer and Dozzle work well together for container management and visibility
- CrowdSec adds a strong security-focused layer by analyzing host and container logs
- Tailscale creates a strong private administration path across devices
- A multi-service private node tells a stronger cybersecurity story than a basic one-service server

* * *

## Skills Demonstrated

- Linux server administration
- Docker Engine installation
- Docker Compose support
- Container deployment and management
- Log visibility and troubleshooting
- Security log analysis
- Private remote administration
- Cross-platform SSH validation
- Security-focused homelab design

* * *

## Outcome

Successfully built a Raspberry Pi 5 private security operations node using Docker, Portainer, Dozzle, CrowdSec, and Tailscale. This project improved hands-on experience with Linux administration, container visibility, defensive monitoring, and private access design while creating a reusable platform for future cybersecurity-focused homelab growth.

* * *

## Future Improvements

Planned future enhancements include:

- restrict Portainer and Dozzle to Tailscale-only access
- add Discord or ntfy alerting for CrowdSec events
- add a Wazuh agent later for broader SOC-style monitoring
- move Docker data to external SSD-backed storage
- add additional internal security tools
- integrate the node with the VPS for private/public service separation
