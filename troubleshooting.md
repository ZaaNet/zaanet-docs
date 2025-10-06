# Troubleshooting

This section provides solutions to common issues encountered while operating a ZaaNet host on a Linux-based device, such as a laptop or Raspberry Pi. Follow these steps to diagnose and resolve problems effectively.

## Common Issues & Solutions

### WiFi Network Not Visible
If users cannot see your ZaaNet WiFi network:

- **Restart ZaaNet**:
  ```bash
  sudo zaanet restart
  ```
  This command restarts the ZaaNet services to refresh the WiFi hotspot.

- **Check WiFi Interface Status**:
  ```bash
  ip addr show wlan0
  ```
  Verify that the `wlan0` interface is active and configured correctly. Ensure it is up and assigned an IP address in the `192.168.100.x` subnet.

### Portal Not Loading
If the captive portal does not appear when users connect:

- **Check Portal Application Status**:
  ```bash
  sudo systemctl status zaanet-manager
  ```
  Ensure the ZaaNet manager service is running.

- **Test Portal Directly**:
  ```bash
  curl -I http://192.168.100.1
  ```
  This checks if the portal is accessible at the default IP address. A `200 OK` response indicates the portal is operational.

### Internet Access Issues
If paid users cannot access the internet:

- **Check Firewall Rules**:
  ```bash
  sudo zaanet firewall status
  ```
  Confirm that the user's IP address is whitelisted after successful payment.

- **Test Internet Connectivity**:
  ```bash
  ping -c 3 8.8.8.8
  ```
  Verify that the Linux-based device has an active internet connection by pinging Google's DNS server.

- **Restart Firewall**:
  ```bash
  sudo systemctl restart zaanet-manager
  ```
  Restarting the ZaaNet manager service can resolve firewall-related issues.

### Payment Issues
If payment processing fails:

- **Check API Connectivity**:
  ```bash
  curl -I https://api.zaanet.xyz/health
  ```
  Ensure the ZaaNet API is reachable. A `200 OK` response confirms the API is operational.

- **View Payment Logs**:
  ```bash
  sudo tail -f /var/log/zaanet/payments.log
  ```
  Review the payment logs to identify any errors during transaction processing.

- **Test Database Connection**:
  ```bash
  sudo zaanet config test
  ```
  Verify that the database connection is functioning correctly.

## Need More Help?
For additional assistance:
- Run `sudo zaanet logs` to view real-time system logs for detailed diagnostics.
- Join the ZaaNet Telegram support group for community support.
- Refer to the detailed troubleshooting guides in the [ZaaNet documentation](https://github.com/ZaaNet) or the [ZaaNet Smart Contracts repository](https://github.com/ZaaNet/zaanet-smart-contracts.git) for blockchain-related issues.