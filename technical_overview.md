# Technical Overview

## How ZaaNet Works

This section provides a detailed overview of the system architecture and operational flow of ZaaNet, a decentralized WiFi sharing platform that enables hosts to create and manage WiFi hotspots using Linux-based devices, such as laptops or Raspberry Pi units.

### System Architecture

#### WiFi Hotspot
The ZaaNet platform creates an isolated WiFi network on a Linux-based device, operating on the `192.168.100.x` subnet. This network serves as the access point for users connecting to the host's WiFi.

#### Firewall Control
ZaaNet employs a firewall `FILTER` method to block internet access by default. Only users who have completed payment are whitelisted, granting them access to the internet.

#### Captive Portal
A Node.js application powers the captive portal, which serves the user interface, processes payments, and manages user sessions to ensure seamless connectivity and access control.

### Payment Processing Flow

The payment processing flow outlines how users gain internet access through ZaaNet:

1. **User Connects**: A user's device joins the ZaaNet WiFi network but is initially blocked by the firewall.
2. **Portal Redirect**: DNS hijacking redirects the user to the captive portal.
3. **Payment Process**: The user completes payment using mobile money or a card through the secure payment gateway.
4. **Access Granted**: Upon successful payment, the user's IP address is whitelisted, enabling internet access.

### Network Configuration Details

#### Default Network Settings
- **Portal IP**: `192.168.100.1`
- **DHCP Range**: `192.168.100.100` - `192.168.100.200`
- **WiFi SSID**: `ZaaNet-Portal` (customizable)