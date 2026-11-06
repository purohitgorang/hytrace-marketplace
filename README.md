# ⚡ HyTrace: Green Hydrogen Credit (GHC) Tokenization Marketplace

[![Next.js](https://img.shields.io/badge/Next.js-15.3.3-black.svg)](https://nextjs.org/)
[![Web3](https://img.shields.io/badge/Ethereum-Solidity%20ERC721-3c3c3d.svg)](https://ethereum.org/)
[![AI Engine](https://img.shields.io/badge/Google%20Genkit-AI%20Flows-4285f4.svg)](https://firebase.google.com/docs/genkit)
[![Styling](https://img.shields.io/badge/TailwindCSS-v3.4-38bdf8.svg)](https://tailwindcss.com/)

HyTrace is a decentralized CleanTech marketplace engineered to verify, tokenize, and trade Green Hydrogen Credits (GHC). It allows verified clean hydrogen producers to mint ERC-721 non-fungible tokens representing megawatt-hours (MWh) of renewable energy generation, with an irreversible one-way retirement mechanism to prevent greenwashing and duplicate carbon offset claims.

---

## 🌟 Key Features

* **ERC-721 Smart Contract Minting:** Smart contracts encode producer address, verification authority, production timestamp, and renewable energy source (solar/wind).
* **Permanent Token Retirement:** Emits on-chain `CreditRetired` events, ensuring tokens cannot be re-sold after an offset is claimed.
* **Google Genkit AI Flows:** Automates compliance document auditing and data extraction from renewable power plant logs.
* **Modern Next.js 15 App Router:** Built with React 18, Radix UI primitives, Lucide icons, and Tailwind CSS.

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
MIT License
