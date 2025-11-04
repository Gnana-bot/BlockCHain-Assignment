
# Blockchain-Based Supply Chain Tracking System

This repository presents a blockchain-based solution designed to ensure secure and transparent tracking of products and shipments across a multi-participant supply chain network. The implementation uses Solidity smart contracts deployed on an Ethereum-compatible environment through Hardhat. The system provides robust role-based access control, immutable event recording, and complete product lifecycle traceability.

---

## 1. Introduction

Supply chains increasingly demand transparency, trust, and tamper-proof data recording. Traditional centralized systems are prone to manipulation, unauthorized access, and lack of accountability. This project introduces a decentralized approach to managing supply chain records, ensuring that stakeholders can only perform actions aligned with their specific responsibilities.

The system records:

- Product creation events
- Shipment transfer operations
- Shipment receipt confirmations

All events are permanently preserved on the blockchain, ensuring integrity, transparency, and auditability.

---

## 2. System Features

### 2.1 Core Functional Features
- Support for manufacturer, distributor, and retailer roles
- Full product lifecycle monitoring from creation to final delivery
- Controlled shipment creation, transfer, and receiving processes
- Historical shipment record retrieval for each product
- Detailed on-chain event logs for accountability

### 2.2 Smart Contract Enforcement
- Administrator-managed participant registration
- Manufacturers retain exclusive permission to create new products
- Verification of correct shipment flow: Manufacturer → Distributor → Retailer
- Prevention of unauthorized access and inconsistent state changes
- Automatic recording of block timestamps for all state transitions

---

## 3. Architecture

### 3.1 Organizational Flow
MANUFACTURER → DISTRIBUTOR → RETAILER

### 3.2 Shipment Lifecycle State Model
CREATED → IN_TRANSIT → RECEIVED

---

## 4. Project Structure

bt/
├── SupplyChain.sol
├── hardhat.config.js
├── package.json
├── scripts/
│   └── deploy.js
└── test/
    └── SupplyChain.test.js

---

## 5. Installation and Execution

### Prerequisites
- Node.js v16+
- npm or yarn
- Hardhat

### Setup
npm install
npx hardhat compile
npx hardhat test

Deploy locally:
npx hardhat node (new terminal)
npx hardhat run scripts/deploy.js --network localhost

---

## 6. Usage

### Participant Registration
await supplyChain.registerParticipant(...)

### Product Creation
await supplyChain.connect(manufacturer).createProduct("Premium Widget")

### Shipment Processing
await supplyChain.connect(manufacturer).createShipment(...)
await supplyChain.connect(manufacturer).transferShipment(...)
await supplyChain.connect(distributor).receiveShipment(...)

### Querying Records
const shipmentIds = await supplyChain.getProductHistory(productId)

---

## 7. Test Coverage
Validates:
- Deployment
- Registration
- Product creation
- Shipment lifecycle
- Access rules
- Data integrity

Example result:
31 passing

---

## 8. Security Considerations
- Role-based authorization
- Tamper-proof ledger
- Valid-state enforcement
- Protection against double-transfer and forgery

---

## 9. Hyperledger Fabric Adaptation

### Conversion for Fabric Chaincode
Smart contract functionalities can be rewritten in Go/Node.js.
Example:
func (s *SmartContract) CreateProduct(...) {}

### Channel Usage
Private channels between participants ensure data confidentiality.

---

## 10. Conclusion

This blockchain system demonstrates a reliable and secure approach to supply chain tracking by combining decentralized architecture, detailed logging, permission enforcement, and traceability standards. It strengthens trust between participants and provides resilience against data manipulation, making it suitable for real-world enterprise deployment.

---
