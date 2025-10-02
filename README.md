# 🚀 Core - Foundry Starter Kit

This project demonstrates how to compile, deploy, and interact with smart contracts on the Core Blockchain using Foundry. It supports multiple Core networks, including Core Mainnet and Core Testnet2.

✅ **Recommended for developers building and testing smart contracts on Core Blockchain.**

## ⚙️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/coredao-org/Core-Foundry-Kit.git
cd Core-Foundry-Kit
```

### 2. Install Foundry

#### Install Foundry on Unix-based systems:

```bash
curl -L https://foundry.paradigm.xyz | bash
```

#### Verify the Installation:

```bash
forge --version
```

#### Update Foundry:

```bash
foundryup
```

---

### 3. Configure Environment Variables

Create a `.env` file in the project root directory and add the following variables:

```bash
RPC_URL="https://rpc.test2.btcs.network"
PRIVATE_KEY="your_core_wallet_private_key"
CORESCAN_API_KEY="your_corescan_api_key"
API_URL="https://api.test2.btcs.network/api"

```

All the above configurations are specific to Core Testnet2. If you're deploying to a different network, please make sure to update the values accordingly.

#### Source the .env File

To make the environment variables available in your shell, run the following command:

```bash
source .env
```

⚠️ **Important:** Never expose your private key or commit the `.env` file to version control.

---

## 🛠 Foundry Commands

### Compile Contracts

```bash
forge build
```

### Run Tests

```bash
forge test
```

### Deploy Contracts

#### Using `forge create`:

```bash
forge create --rpc-url $RPC_URL --private-key $PRIVATE_KEY src/YourContract.sol:YourContract --broadcast --legacy
```

#### Using Deployment Scripts:

```bash
forge script script/YourScript.s.sol:YourScript --rpc-url $RPC_URL --private-key $PRIVATE_KEY --broadcast --legacy
```

If you're working with Rev+ contracts or encountering a `gas underpriced` issue, try using the `--gas-estimate-multiplier` flag in your Foundry deploy script.

**Note** `--gas-estimate-multiplier` flag does not work with the `forge create` command, it only works with the `forge script` command.

---

## 🔍 Contract Verification

Verify deployed contracts with CoreScan:

```bash
forge verify-contract 0xDeployedContractAddress YourContract --verifier-url $API_URL --api-key $CORESCAN_API_KEY --watch
```

---

## 🌐 Network Configuration

Example network configurations for Core Mainnet and Testnet2:

- **Mainnet:**
  - RPC URL: `https://rpc.coredao.org`
  - Chain ID: `1116`
  - API URL: `https://openapi.coredao.org/api`
- **Testnet2:**
  - RPC URL: `https://rpc.test2.btcs.network`
  - Chain ID: `1114`
  - API URL: `https://api.test2.btcs.network/api`

Update these values in your `.env` file as needed.

---

### 🧠 Compiler Notes

The EVM version and Solidity compiler settings for this project are configured in the foundry.toml file.

#### Default Configuration:

- EVM Version: Shanghai

- Solidity Version: 0.8.24

```bash
[profile.default]
evm_version = "Shanghai"
solc_version = "0.8.24"
```

Ensure the settings match the network requirements to avoid compatibility issues.

## 📚 Resources

- [Foundry Documentation](https://book.getfoundry.sh/)
- [Core Blockchain Docs](https://docs.coredao.org/docs/Dev-Guide/foundry)

---

## 🛡 Disclaimer

This project is intended for **educational and development purposes** only. Always safeguard your private keys and avoid exposing sensitive credentials in your codebase or version control.
