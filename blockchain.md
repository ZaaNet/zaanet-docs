# Blockchain Integration

ZaaNet operates on the Arbitrum One mainnet, utilizing a modular smart contract architecture to deliver a secure, transparent, and automated platform for decentralized WiFi sharing. This section outlines the core smart contracts, their functionalities, and the key benefits of ZaaNet's blockchain integration.

## Core Smart Contracts

### ZaaNetStorage Contract
- **Purpose**: Serves as the centralized data repository for the ZaaNet ecosystem, securely storing all contract states.
- **Key Functions**:
  - `setNetwork(uint256 id, Network calldata net)`: Creates or updates a network (authorized callers only).
  - `getNetwork(uint256 id)`: Retrieves network details by ID.
  - `getHostNetworks(address hostAddress)`: Returns all network IDs for a specific host.
  - `increaseHostEarnings(address hostAddress, uint256 amount)`: Updates host earnings.
  - `getZaaNetEarnings()`: Retrieves total platform earnings.
- **Access Control**: Restricted to authorized contracts (`ZaaNetAdmin`, `ZaaNetNetwork`, `ZaaNetPayment`) for read/write operations.

### ZaaNetNetwork Contract
- **Purpose**: Manages WiFi network nodes and their operations.
- **Key Functions**:
  - `registerNetwork(uint256 pricePerSession, string mongoDataId, string status)`: Registers a new WiFi network with a hosting fee payment.
  - `updateNetwork(...)`: Modifies pricing and network settings.
  - `getHostedNetworkById(string nodeId)`: Retrieves details of a specific network.
  - `deactivateNetwork(string nodeId)`: Deactivates a network node.
- **Dependencies**: Interacts with `ZaaNetStorage` for data storage and retrieval.

### ZaaNetPayment Contract
- **Purpose**: Handles USDT-based payment processing for voucher redemptions.
- **Key Functions**:
  - `processPayment(uint256 _contractId, uint256 _grossAmount, bytes32 _voucherId)`: Processes individual voucher payments to hosts.
  - `processBatchPayments(BatchPayment[] calldata payments)`: Processes up to 50 payments in a single transaction, achieving up to 90% gas savings.
  - `getRemainingDailyLimit()`: Returns the available daily withdrawal limit for hosts.
  - `isVoucherProcessed(bytes32 _voucherId)`: Prevents double-spending by checking if a voucher has been processed.
- **Token Support**: Uses USDT on Arbitrum Sepolia (`0x438C411f9aEFDd02D90C31Dc24bC1380c08934Cd`).

### ZaaNetAdmin Contract
- **Purpose**: Provides administrative control over platform configuration and governance.
- **Key Functions**:
  - `setPlatformFee(uint256 newFeePercent)`: Sets the platform's revenue-sharing percentage (1% to 20%).
  - `setHostingFee(uint256 newFee)`: Adjusts network registration fees (0 to 100 USDT).
  - `setTreasuryAddress(address newTreasury)`: Updates the treasury wallet address.
  - `emergencyDeactivateNetwork(uint256 networkId)`: Allows emergency deactivation of a network.
- **Configuration Parameters**:
  - Platform Fee: 10% (configurable).
  - Hosting Fee: 2 USDT (configurable).
  - Treasury Address: `0x2652164707AA3269C83FEAA9923b0e19CacFA906`.

## Key Benefits
- **Transparent Earnings**: All transactions are recorded on-chain, providing real-time visibility into payments and earnings.
- **Automated Payouts**: USDT is automatically transferred to host wallets upon voucher redemption, streamlining the payment process.
- **Gas Optimization**: Batch payment processing reduces transaction costs by up to 90%, enhancing efficiency.
- **Robust Security**: Features include daily withdrawal limits (10,000 USDT), emergency pause functionality, multi-operator governance, and role-based access control to ensure platform reliability and security.

For detailed review, refer to the [ZaaNet Smart Contracts repository](https://github.com/ZaaNet/zaanet-smart-contracts.git).