# Host Installation Guide

## Setting Up Your ZaaNet Host

This guide provides step-by-step instructions for setting up your ZaaNet host on a Linux-based device, such as a laptop or Raspberry Pi, to create a WiFi hotspot and monetize your internet connection.

### Hardware Setup

#### Required Hardware
- Linux-based device (e.g., Raspberry Pi 4 with 4GB+ RAM recommended, or a laptop)
- MicroSD card (32GB+ Class 10, if using a Raspberry Pi)
- Power supply (official Raspberry Pi adapter or equivalent for your device)
- Ethernet cable for internet connection
- Dual-Band Wireless USB Adapter (recommended for improved connection capacity)

#### Network Architecture
- **Internet** → **Router** → **Linux-based device** (via Ethernet)
- The Linux-based device creates a WiFi hotspot (wlan0)
- Users connect to the device's WiFi network
- A captive portal controls internet access

### Installation Commands

ZaaNet provides a zero-configuration installer that automatically sets up everything needed for your captive portal. Follow these steps to install ZaaNet on your Linux-based device:

```bash
# Download the ZaaNet installation script
curl -sSL https://get.zaanet.xyz | sudo bash
```

The installer will automatically detect your Linux-based device, identify network interfaces, and configure the system. You will only need to provide your hosted WiFi network name and contract ID during the setup process.

### Management Commands

After installation, use the following commands to manage your ZaaNet host:

```bash
# Start captive portal mode
sudo zaanet start

# Check current status
sudo zaanet status

# View live logs
sudo zaanet logs

# Stop captive portal (return to normal internet)
sudo zaanet stop

# Restart services
sudo zaanet restart

# Enable auto-start on boot
sudo zaanet enable

# Show configuration details
sudo zaanet config

# Update to the latest version
sudo zaanet update
```

### Firewall & User Management

#### Firewall Commands

The following commands allow you to manage firewall settings and user access:

```bash
# Show authenticated users
sudo zaanet firewall status

# Manually grant internet access to an IP
sudo zaanet firewall allow 192.168.100.105

# Revoke internet access for an IP
sudo zaanet firewall block 192.168.100.105

# List all firewall rules
sudo zaanet firewall list
```

#### Automatic Operation
User IP addresses are automatically whitelisted for internet access upon successful voucher redemption through the captive portal. Manual firewall commands are intended for troubleshooting purposes only.