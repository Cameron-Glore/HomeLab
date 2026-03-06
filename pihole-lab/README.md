# Pi-hole DNS Filtering Lab

## Overview

This lab documents the deployment of Pi-hole on a Raspberry Pi Zero 2 W to provide network-wide DNS filtering. Pi-hole acts as a DNS sinkhole that blocks advertisements, tracking domains, and malicious sites across a home network.

This project demonstrates practical experience with Linux administration, DNS configuration, and network security.

---

## Lab Objectives

• Deploy Pi-hole on a Raspberry Pi  
• Configure a DNS filtering server for a home network  
• Monitor DNS traffic and blocked domains  
• Gain experience with Linux server administration

---

## Hardware

- Raspberry Pi Zero 2 W
- 16GB MicroSD card
- Power supply
- Home WiFi network

---

## Software

- Raspberry Pi OS Lite
- Pi-hole DNS filtering software
- SSH for remote administration

---

## Network Architecture

Device → Router → Pi-hole DNS Server → Internet

All DNS requests are routed through Pi-hole, allowing it to filter unwanted domains.

---

## Installation Steps

### 1 Install Raspberry Pi OS Lite

Using Raspberry Pi Imager:

1. Insert MicroSD card
2. Select Raspberry Pi OS Lite
3. Enable SSH
4. Configure WiFi
5. Write image to SD card

---

### 2 Boot the Raspberry Pi

Insert the SD card and power on the device.

Locate the Pi's IP address through the router or network scan.

---

### 3 Connect via SSH

ssh username@raspberrypi_ip

---

### 4 Update the system

sudo apt update  
sudo apt upgrade -y

---

### 5 Install Pi-hole

curl -sSL https://install.pi-hole.net | bash

During installation:

- Choose upstream DNS provider
- Enable the web admin interface
- Record the admin password

---

## Accessing the Dashboard

Open a browser and navigate to:

http://raspberrypi_ip/admin

The dashboard provides:

- DNS query statistics
- Blocked domain reports
- Client activity monitoring

---

## Results

After configuring a test device to use the Pi-hole server as its DNS provider, the system successfully blocked advertising and tracking domains.

The dashboard provides real-time visibility into DNS queries and filtering performance.

---

## Skills Demonstrated

Linux server administration  
DNS configuration  
Network troubleshooting  
Security filtering and monitoring

---

## Future Improvements

- Add custom blocklists
- Implement network-wide DNS configuration
- Integrate monitoring tools
- Add network traffic analysis

---

## Screenshots

Screenshots of the Pi-hole dashboard and DNS query logs are stored in the screenshots folder.
