# Pi-hole DNS Filtering Lab

## Overview

This project documents my planned deployment of Pi-hole on a Raspberry Pi Zero 2 W for network-wide DNS filtering on my home network.

Pi-hole will act as a DNS sinkhole to block ads, tracking domains, and potentially malicious domains while giving visibility into DNS traffic across connected devices.

This lab is being documented in phases. The planning and design are being completed first, with deployment and testing to follow once the Raspberry Pi hardware arrives.

---

## Objective

- Deploy Pi-hole on a Raspberry Pi Zero 2 W
- Configure it for DNS filtering on a home network
- Monitor DNS requests and blocked domains
- Build hands-on experience with Linux, DNS, and network security

---

## Hardware

- Raspberry Pi Zero 2 W
- MicroSD card
- Power supply
- Home WiFi network

---

## Software

- Raspberry Pi OS Lite
- Pi-hole
- SSH for remote access

---

## Planned Network Design

Device → Router → Pi-hole DNS Server → Internet

In this setup, client devices will send DNS requests to Pi-hole. Pi-hole will filter unwanted requests and forward approved DNS traffic to an upstream DNS provider.

---

## Deployment Plan

Once the Raspberry Pi arrives, the deployment plan is:

1. Flash Raspberry Pi OS Lite to the MicroSD card
2. Enable SSH and configure WiFi
3. Boot the Raspberry Pi Zero 2 W
4. Find the Pi’s IP address on the network
5. Connect to the Pi with SSH
6. Update the system
7. Install Pi-hole
8. Enable the web admin interface
9. Configure a test device to use Pi-hole for DNS
10. Validate DNS filtering and review dashboard statistics

---

## Planned Installation Commands

After connecting to the Raspberry Pi:

```bash
sudo apt update
sudo apt upgrade -y
curl -sSL https://install.pi-hole.net | bash
