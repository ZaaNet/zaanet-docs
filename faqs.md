# Frequently Asked Questions (FAQ)

This section addresses common questions about ZaaNet, covering general, business, and technical aspects of the decentralized WiFi sharing platform.

## General Questions

### What happens if my Linux-based device loses power?
ZaaNet is configured to automatically restart on boot. When power is restored, the captive portal resumes operation, and user sessions and firewall rules are restored from the database. For business-critical installations, we recommend using an Uninterruptible Power Supply (UPS) to ensure continuous operation.

## Business Questions

### How do I receive payments?
Payments are processed daily to your registered wallet address via the _**ZaaNetPayment**_ smart contract on the Arbitrum One mainnet. You can monitor real-time earnings through your host dashboard. ZaaNet deducts a transparent platform fee from each transaction, recorded on the blockchain for full visibility.

### Can I set my own prices?
Yes, hosts have full control over pricing. You can set hourly or session-based rates and offer different packages. The system supports flexible pricing, allowing adjustments based on demand or local market conditions.

### What are the ongoing costs?
Ongoing costs include your internet bill for providing WiFi and electricity for running your Linux-based device (e.g., a laptop or Raspberry Pi) and any optional USB WiFi adapter for extended capacity. ZaaNet charges a small percentage-based platform fee on each transaction, with no monthly fees, setup costs, or hidden charges. You only pay when you earn.

## Technical Questions

### What hardware do I need?
To set up a ZaaNet host, you need:
- A Linux-based device (e.g., Raspberry Pi 4 with 4GB+ RAM recommended, or a laptop).
- A microSD card (32GB+ Class 10, for Raspberry Pi setups).
- A power supply (official Raspberry Pi adapter or equivalent for your device).
- A USB WiFi adapter (recommended for extended capacity).
- An Ethernet cable for connecting the device to your router.

The Linux-based device connects to your router via Ethernet and creates a WiFi hotspot for customers.

### Do I need technical knowledge?
No technical expertise is required. ZaaNet provides a one-command installer that automatically configures the system. Simply run the installation commands, provide your WiFi name (SSID) and contract ID, and the system handles the rest. Management commands are straightforward and designed for ease of use.

### How does the captive portal work?
The captive portal runs on the Linux-based device, utilizing a Node.js application to intercept user traffic and display the payment portal. When a user connects to the WiFi network, they are redirected to the portal to pay for access using mobile money or a card. Upon payment confirmation, the user's IP address is whitelisted in the firewall, granting internet access.

### What if I encounter issues?
To troubleshoot, use the _**sudo zaanet logs**_ command to view real-time system logs. You can also join the ZaaNet Telegram support group for community assistance or consult the detailed troubleshooting guides in the [ZaaNet documentation](https://github.com/ZaaNet). For smart contract-related issues, refer to the [ZaaNet Smart Contracts repository](https://github.com/ZaaNet/zaanet-smart-contracts.git).