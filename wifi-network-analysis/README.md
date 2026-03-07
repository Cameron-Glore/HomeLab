# Wireless Network Analysis Lab

## Overview

This lab analyzes a home wireless network using a Flipper Zero with an AWOK Dual ESP32 Wi-Fi board running ESP32 Marauder firmware.

Instead of using a smartphone Wi-Fi analyzer app, dedicated wireless testing hardware was used to scan nearby networks and evaluate signal strength, channel usage, and security settings.

This project demonstrates practical wireless networking analysis and basic RF troubleshooting concepts.

---

## Lab Objectives

- Scan nearby wireless networks
- Identify the operating channel of the home network
- Analyze signal strength (RSSI)
- Review wireless security configuration
- Identify possible improvements for performance and security

---

## Hardware Used

- Flipper Zero
- AWOK Dual ESP32 Wi-Fi board
- ESP32 Marauder firmware

---

## Network Scan

A wireless scan was performed using ESP32 Marauder.

The scan identified my home wireless network and displayed the following information:

Channel: 10  
Frequency Band: 2.4 GHz  
Signal Strength (RSSI): −66 dBm  
Security Type: WPA2  

The scan also detected **23 frames of activity**, indicating that the network was actively transmitting data during the scan.

---

## Scan Results Screenshot

![WiFi Scan Results](screenshots/wifi-scan-results1.png)
(screenshots/wifi-scan-results2.png)
(screenshots/wifi-scan-results3.png)

---

## Signal Strength Analysis

RSSI (Received Signal Strength Indicator) measures the power level received from the wireless access point.

Typical signal strength values:

| Signal Strength | Quality |
|----------------|--------|
| −30 dBm | Excellent |
| −50 dBm | Very good |
| −67 dBm | Reliable |
| −70 dBm | Minimum usable |

The measured signal strength of **−66 dBm** indicates that the connection to the wireless network is strong and stable.

---

## Channel Analysis

The network is currently operating on **Channel 10** in the 2.4 GHz band.

However, the 2.4 GHz spectrum contains overlapping channels. The recommended non-overlapping channels are:

- Channel 1
- Channel 6
- Channel 11

Using Channel 10 may create potential interference with nearby networks. Switching to one of the non-overlapping channels could improve performance.

---

## Security Analysis

The network is configured with **WPA2 encryption**, which remains secure for most home networks.

However, many modern routers support **WPA3**, which provides improved encryption and better protection against certain wireless attacks.

Upgrading to WPA3 would further strengthen network security if supported by the router.

---

## Results

The wireless analysis indicates that the network is functioning properly:

- Strong signal strength
- Active network traffic detected
- Secure WPA2 encryption enabled

Potential improvements include:

- Switching to a non-overlapping channel (1, 6, or 11)
- Upgrading wireless security to WPA3 if available

---

## Skills Demonstrated

- Wireless network scanning
- Signal strength analysis
- Channel interference evaluation
- Wireless security assessment
- Use of specialized wireless testing hardware

---

## Future Improvements

Future testing could include:

- scanning neighboring networks for interference
- comparing signal strength at different distances
- analyzing 5 GHz wireless networks
- testing performance after changing channels
