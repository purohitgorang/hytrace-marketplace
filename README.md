# ⚡ HyTrace: Green Hydrogen Credit (GHC) Tokenization Marketplace

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Next.js](https://img.shields.io/badge/Next.js-15.3.3-black.svg)](https://nextjs.org/)
[![Web3](https://img.shields.io/badge/Ethereum-Solidity%20ERC721-3c3c3d.svg)](https://ethereum.org/)
[![AI Engine](https://img.shields.io/badge/Google%20Genkit-AI%20Flows-4285f4.svg)](https://firebase.google.com/docs/genkit)
[![Styling](https://img.shields.io/badge/TailwindCSS-v3.4-38bdf8.svg)](https://tailwindcss.com/)

**HyTrace** is a decentralized CleanTech marketplace engineered to verify, tokenize, and retire Green Hydrogen Credits (GHC). It enables verified renewable hydrogen producers to mint ERC-721 tokens representing audited megawatt-hours (MWh) of zero-emission generation, enforcing irreversible on-chain token burns to eliminate double-counting and carbon greenwashing.

---

## 🏛️ Architecture: Solving the Physical-to-Digital "Oracle Problem"

In CleanTech Web3 systems, on-chain tokens are worthless if the physical hydrogen was never produced. HyTrace bridges physical plant telemetry to smart contracts through an audited verification pipeline:

```
┌────────────────────────────────────────────────────────┐
│             Physical Production Facility               │
│   Smart Power Inverters (Solar/Wind) + Electrolyzers   │
└───────────────────────────┬────────────────────────────┘
                            │ Signed Modbus / MQTT Telemetry (MWh & kg H2)
                            ▼
┌────────────────────────────────────────────────────────┐
│            Google Genkit AI Audit & Validation         │
│  • Automated ingestion of plant telemetry logs         │
│  • Cross-checks water consumption vs. hydrogen volume  │
│  • Verifies renewable energy grid origin certificates  │
└───────────────────────────┬────────────────────────────┘
                            │ Cryptographic Attestation Payload
                            ▼
┌────────────────────────────────────────────────────────┐
│          Solidity ERC-721 Smart Contract               │
│  • Minting: `mintCredit(facilityId, mwhProduced)`     │
│  • Trading: Non-custodial secondary transfer           │
│  • Retirement: `retireCredit(tokenId)` (Permanent Burn)│
└───────────────────────────┬────────────────────────────┘
                            │ Emits `CreditRetired` Event
                            ▼
┌────────────────────────────────────────────────────────┐
│                Next.js 15 Web3 DApp                    │
│      Provable Carbon Offset Certificate Generated       │
└────────────────────────────────────────────────────────┘
```

---

## 🔒 Smart Contract Lifecycle & State Machine

Every Green Hydrogen Credit moves through a strictly enforced, one-way state machine:

| Token State | Permitted Actions | Smart Contract Guard |
|---|---|---|
| **1. Minted** | Attestation validated; token assigned to producer address | `onlyAuthorizedMinter` role restriction |
| **2. Listed / Transferred** | Traded on marketplace to corporate industrial buyers | Standard ERC-721 non-custodial transfer |
| **3. Retired (Burned)** | Claimed against corporate carbon footprint | `retireCredit()` transfers token to `0x000...dead` |

> Once retired, tokens are irrevocably burned on-chain. The smart contract emits a permanent event containing the company's legal entity ID, making duplicate carbon offset claims mathematically impossible.

---

## 💡 Engineering Ownership & Design Decisions

### 1. What problem was identified?
Voluntary carbon credit markets suffer from widespread fraud: the same renewable hydrogen batch is frequently sold to multiple buyers across un-synchronized private registries. A trustless, public ledger with permanent burn semantics was required.

### 2. Why ERC-721 instead of fungible ERC-20?
Unlike standard currency, green hydrogen batches are not interchangeable commodities. Each production run has unique, auditable attributes: specific electrolyzer efficiency, geographical plant location, exact production hour, and renewable energy mix (e.g. 80% solar / 20% wind). ERC-721 non-fungible metadata preserves this physical chain of custody.

### 3. What failed during development & how was it fixed?
* **Failure:** Next.js 15 App Router server-side rendering (SSR) threw severe hydration mismatches when interacting with injected browser wallet providers (`window.ethereum`).
* **Solution:** Decoupled Web3 wallet state into an isolated client-side context provider with dynamic imports (`ssr: false`), preventing hydration collisions between server pre-renders and browser wallet extensions.

### 4. What would be added in a production version?
* Chainlink Functions integration to pull real-time grid renewable energy percentage directly from national electricity transmission operators.
* ERC-4337 Account Abstraction to allow non-crypto corporate enterprise buyers to purchase credits using standard bank ACH/wire transfers without managing private seed phrases.

---

## 🚀 Quick Start

### 1. Install Dependencies
```bash
npm install --legacy-peer-deps
```

### 2. Launch Local Development Server
```bash
# Windows turnkey launcher
run_hytrace.bat

# Or run via npm
npm run dev
```
Open **`http://localhost:9002`** in your browser.

---

## 📄 License
MIT License. Copyright (c) 2026 Gorang Purohit.
