# RealGoTopUpGateway 🔐💰
RealGoTopUpGateway is a secure smart contract for native currency and ERC20 token deposits. It features role-based access control, token whitelist management, pause and emergency stop mechanisms, and rescue functions to protect funds in Web3 applications.

> A secure gateway contract for handling **native currency** and **ERC20 token deposits**, with role-based access control, whitelist management, and emergency stop features.

---

## 🚀 Features
- ✅ **Native currency deposits** (ETH/BNB) with treasury forwarding  
- ✅ **ERC20 token deposits** with whitelist control  
- ✅ **Role-based access control** (`DEFAULT_ADMIN_ROLE`, `ADMIN_ROLE`)  
- ✅ **Pause & emergency stop** mechanisms for safety  
- ✅ **Rescue functions** for mistakenly sent tokens or native currency  
- ✅ **Event logging** for all deposits and management actions  

---

## 🛠️ Tech Stack
- Solidity `^0.8.20`  
- OpenZeppelin libraries:  
  - AccessControl  
  - ReentrancyGuard  
  - SafeERC20  
  - Address  

---

## 📦 Installation
Clone the repository and install dependencies:

```bash
git clone https://github.com/your-org/RealGoTopUpGateway.git
cd RealGoTopUpGateway
npm install
```

Compile contracts:

```bash
npx hardhat compile
```

---

## 📜 Contract Overview

### Roles
- **DEFAULT_ADMIN_ROLE**: Full control, can trigger emergency stop and rescue funds.  
- **ADMIN_ROLE**: Can pause/unpause and manage token whitelist.  

### Key Functions
- **depositNative(userId, orderId)** → Deposit ETH/BNB to treasury  
- **depositToken(token, amount, userId, orderId)** → Deposit ERC20 tokens to treasury  
- **setWhitelist(token, allowed)** → Manage token whitelist  
- **setPaused(v)** → Pause/unpause deposits  
- **triggerEmergencyStop()** → Permanently stop deposits  
- **rescueToken(token, amount)** → Rescue ERC20 tokens sent by mistake  
- **rescueNative(amount)** → Rescue native currency sent by mistake  

---

## 📊 Events
- **DepositNative**: Logs native currency deposits  
- **DepositToken**: Logs ERC20 deposits  
- **WhitelistUpdated**: Logs whitelist changes  
- **PausedChanged**: Logs pause state changes  
- **EmergencyStopped**: Logs emergency stop  
- **RescueToken / RescueNative**: Logs rescue operations  

---

## 💻 Example Usage

### Native Currency Deposit
```solidity
RealGoTopUpGateway gateway = RealGoTopUpGateway(gatewayAddress);

// User deposits 1 ETH/BNB
gateway.depositNative{value: 1 ether}("user123", "order456");
```

### ERC20 Token Deposit
```solidity
IERC20 token = IERC20(tokenAddress);

// Approve before deposit
token.approve(gatewayAddress, 1000 * 1e18);

// Deposit tokens
gateway.depositToken(tokenAddress, 1000 * 1e18, "user123", "order789");
```

### Whitelist Management
```solidity
// Admin adds token to whitelist
gateway.setWhitelist(tokenAddress, true);
```

### Pause & Emergency Stop
```solidity
// Admin pauses deposits
gateway.setPaused(true);

// Default admin triggers emergency stop
gateway.triggerEmergencyStop();
```

### Rescue Funds
```solidity
// Rescue mistakenly sent ERC20
gateway.rescueToken(tokenAddress, 500 * 1e18);

// Rescue mistakenly sent native currency
gateway.rescueNative(2 ether);
```

---

## 🔒 Security Notes
- Always restrict **DEFAULT_ADMIN_ROLE** to a secure multisig wallet.  
- Use **ADMIN_ROLE** for day-to-day operations.  
- Emergency stop is **irreversible** — once triggered, deposits cannot resume.  

---

## 📬 Contact
For inquiries or integration support:  
📧 **gm@realgo.game**

---

## 🏷️ Badges
![Solidity](https://img.shields.io/badge/Solidity-%5E0.8.20-blue?style=for-the-badge&logo=solidity)
![OpenZeppelin](https://img.shields.io/badge/OpenZeppelin-Library-green?style=for-the-badge&logo=openzeppelin)
![BNB Smart Chain](https://img.shields.io/badge/Built%20on-BNB%20Smart%20Chain-yellow?style=for-the-badge&logo=binance)
![Web3 Ready](https://img.shields.io/badge/Web3-Ready-orange?style=for-the-badge&logo=ethereum)
```
