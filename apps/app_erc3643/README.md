 > ⚠️ **NOTICE:** This app 'app_erc3643' has been supported by [app_bridge_ui](https://github.com/LFDT-Smoot/bridge/tree/main/apps/app_bridge_ui). Please use  [app_bridge_ui](https://github.com/LFDT-Smoot/bridge/tree/main/apps/app_bridge_ui) for further development.
 
# SMOOT-Bridge: Secure Cross-Chain Messaging and Interoperability Protocol



## 🚀 Project Overview

The **SMOOT-Bridge Application** is a decentralized, community-driven **generic message-passing protocol** designed to establish secure, bidirectional communication between diverse blockchain ecosystems, including both **EVM-compatible chains** (like Ethereum and Polygon) and **non-EVM chains** (such as Solana or Stellar). Currently, we demonstrate its capability by facilitating seamless and secure **cross-chain token transfer** between the **Ethereum Mainnet** and the **Polygon network**. The underlying architecture is inherently designed for easy expansion to any future supported chain.

Our primary focus is enabling the cross-chain transfer of tokens compliant with the **ERC-3643 standard**, which maintains full compatibility with the widely used **ERC-20** token standard. This ensures that assets with enhanced regulatory or compliance features can move efficiently across chains.

## ✨ Key Features

- **Generic Message Passing:** The fundamental ability to relay arbitrary data payloads across chains, enabling future decentralized application (dApp) interoperability.
- **ERC-3643 / ERC-20 Compatibility:** Supports the transfer of compliant token standards, ensuring broader utility.
- **Robust Lock/Mint Mechanism:** Utilizes a secure lock-and-mint approach to maintain 1:1 token parity across both networks.
- **Decentralized Agents:** Relies on external SMOOT-Bridge Agents for reliable event capture and message relaying.
- **Gateway Abstraction:** Uses a dedicated `Gateway` contract to decouple the bridging logic from the core token contracts, simplifying future protocol upgrades.

## 🏗️ Architecture and Contract Roles

The SMOOT-Bridge relies on a minimal set of smart contracts and a relaying agent network deployed across both chains:

| Contract/Entity         | Chain     | Role                                                         |
| ----------------------- | --------- | ------------------------------------------------------------ |
| **TokenHome**           | Ethereum  | The primary contract where the original ERC-3643 token is registered and **locked** when transferring to Polygon. |
| **TokenRemote**         | Polygon   | The counterpart contract responsible for **minting** and registering the mapped token on the Polygon network. |
| **Gateway**             | Both      | The message bus. This contract manages the low-level communication and triggers the appropriate action (`inboundCall` / `outboundCall`) on the token contracts. |
| **SMOOT-Bridge Agents** | Off-chain | A network of decentralized relayers that monitor `outboundCall` events on one chain and initiate the corresponding `inboundCall` on the destination chain. |

## 🌊 Cross-Chain Transfer Flow

The bridging process follows a standard lock-and-mint/burn-and-unlock model, built upon the foundation of the generic message-passing capability.

### A. Crossing Token from Ethereum (Home) to Polygon (Remote)

This process locks the original token on Ethereum and mints a corresponding token on Polygon.

1. **Initiation:** The user on Ethereum calls the `send` function of the **TokenHome** contract, specifying the recipient's address and the cross-chain amount.
2. **Lock & Event:** The token asset is securely **locked** in the `TokenHome` contract. The contract then calls the `outboundCall` function of the Ethereum **Gateway** contract, emitting a cross-chain message event.
3. **Message Capture:** The **SMOOT-Bridge Agents** capture this emitted event from the Ethereum Gateway. The designated leader agent prepares and signs the relay transaction.
4. **Relay & Execution:** The offline agent calls the `inboundCall` function of the **Gateway** contract on **Polygon**.
5. **Minting:** The Polygon Gateway executes the inbound message, triggering the **TokenRemote** contract to **mint** the mapping token and transfer it to the specified recipient's address on Polygon.

### B. Crossing Asset Back to Ethereum (Home) from Polygon (Remote)

This process burns the mapped token on Polygon and unlocks the original token on Ethereum.

1. **Initiation:** The user on Polygon calls the `send` function of the **TokenRemote** contract to initiate the return transfer.
2. **Burn & Event:** The mapped token is immediately **burnt** by the `TokenRemote` contract. It then calls the `outboundCall` function of the Polygon **Gateway** contract, emitting a cross-chain message event.
3. **Message Capture:** The **SMOOT-Bridge Agents** capture this event from the Polygon Gateway.
4. **Relay & Execution:** The offline agent calls the `inboundCall` function of the **Gateway** contract on **Ethereum**.
5. **Unlock & Transfer:** The Ethereum Gateway executes the inbound message, triggering the **TokenHome** contract to **transfer** (unlock) the original token from the contract's reserves to the recipient's address on Ethereum.

