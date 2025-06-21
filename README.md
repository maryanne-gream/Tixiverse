# 🎟️ Tixiverse – A Decentralized Ticketing Platform on Bitcoin via Stacks

**Tixiverse** is a decentralized ticketing platform powered by the Stacks blockchain, enabling transparent, tamper-proof, and trustless ticketing. Using **Clarity** smart contracts, Tixiverse brings Bitcoin security and immutability to event ticket creation, sales, and validation.

---

## 🌐 Live Demo

- 🌍 [Tixiverse Frontend](https://your-dapp-url.com)
- 🔍 [View Smart Contract on Stacks Explorer](https://explorer.stacks.co/txid/your-contract-address)

---

## 📚 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Tech Stack](#tech-stack)
- [Smart Contract (Clarity)](#smart-contract-clarity)
- [Frontend](#frontend)
- [Getting Started](#getting-started)
- [Deployment](#deployment)
- [Contributing](#contributing)
- [License](#license)

---

## 🔍 Overview

Traditional ticketing platforms are plagued with scalping, fraud, and centralized control. Tixiverse solves these problems by using **smart contracts written in Clarity** to:

- Mint tickets as non-fungible tokens (NFTs)
- Record and verify ticket ownership on-chain
- Prevent double spending and fake tickets
- Enable resale and royalty mechanics
- Ensure censorship-resistance and transparency

---

## ✨ Features

### ✅ For Event Organizers
- Deploy event-specific smart contracts
- Mint tickets (as NFTs)
- Set ticket limits and pricing
- Enable/disable resale and royalties
- Validate tickets at the event gate

### 🎫 For Attendees
- Purchase tickets with Stacks (STX)
- Transfer or resell tickets via smart contracts
- View owned tickets via wallet
- Scan QR codes for entry validation

---

## 🧱 Architecture

```

```
                  ┌────────────────────┐
                  │   Event Organizer  │
                  └────────┬───────────┘
                           │
                  ┌────────▼───────────────┐
                  │ Tixiverse Clarity SC   │
                  └────────┬───────────────┘
                           │
          ┌────────────┬───▼─────┬─────────────┐
          │            │         │             │
   ┌──────▼─────┐ ┌────▼─────┐ ┌──▼────────────┐
   │   Frontend │ │  IPFS    │ │  Stacks Chain │
   │ (React + JS│ │ Metadata │ │  + Bitcoin    │
   └────────────┘ └──────────┘ └───────────────┘
                           │
                  ┌────────▼────────┐
                  │     Users       │
                  └─────────────────┘
```

````

---

## 🛠️ Tech Stack

| Layer        | Technology                          |
|--------------|--------------------------------------|
| Blockchain   | Stacks Blockchain                    |
| Smart Contract | Clarity Language                  |
| Token Standard | SIP-009 (NFT Standard for Stacks) |
| Frontend     | React.js, Stacks.js, Tailwind CSS   |
| Wallet       | Hiro Wallet                         |
| Storage      | IPFS via Web3.Storage or Pinata     |
| QR Validation| Wallet Auth + Event Gate Validator  |

---

## 🔒 Smart Contract (Clarity)

**Highlights:**
- SIP-009 NFT compliant
- Maps ticket IDs to owners
- Tracks resale, royalties, and redemption
- Uses `trait`s to define interfaces
- Permissioned minting for event organizers

**Contract Structure:**
- `mint-ticket` – Mints a new NFT ticket
- `transfer` – Transfers ticket between users
- `burn-ticket` – Invalidates a used or refunded ticket
- `validate-ticket` – Marks ticket as used (checked-in)
- `set-resale` – Enables resale with conditions

Example Clarity Snippet:
```clojure
(define-non-fungible-token ticket uint)

(define-public (mint-ticket (ticket-id uint) (recipient principal))
  (begin
    (asserts! (is-eq tx-sender contract-owner) (err u401))
    (nft-mint? ticket ticket-id recipient)))
````

Contracts can be deployed using [Clarinet](https://github.com/hirosystems/clarinet).

---

## 💻 Frontend

Frontend built with:

* React + Vite
* @stacks/connect
* @stacks/transactions
* Hiro Wallet integration
* Tailwind CSS UI
* IPFS metadata fetcher
* QR Code generator and scanner

**Screens:**

* Event Creation Dashboard
* Ticket Purchase Page
* My Tickets Wallet View
* Admin Validation Panel

---

## 🚀 Getting Started

### 1. Prerequisites

* Node.js v18+
* Clarinet (for Clarity dev)
* Hiro Wallet
* Git

---

### 2. Clone the Repository

```bash
git clone https://github.com/your-username/tixiverse.git
cd tixiverse
```

---

### 3. Install Dependencies

```bash
# Contracts
cd contracts
clarinet check

# Frontend
cd ../frontend
npm install
```

---

### 4. Run the Dev Environment

**Start Clarity localnet (Clarinet):**

```bash
cd contracts
clarinet console
```

**Run Frontend Dev Server:**

```bash
cd ../frontend
npm run dev
```

---

### 5. Deploy Smart Contract

```bash
clarinet deploy
```

Use [Stacks Explorer](https://explorer.stacks.co/) to verify contract deployment.

---

## 🚢 Deployment

### Smart Contract

* Test and deploy via Clarinet or directly via CLI
* Update contract address in frontend `.env`

### Frontend Hosting

* Vercel / Netlify / GitHub Pages

`.env` example:

```env
VITE_CONTRACT_ADDRESS=ST123ABC...XYZ
VITE_NETWORK=testnet
```

---

## 🤝 Contributing

We welcome PRs and issue submissions!

1. Fork the repo
2. Create your feature branch (`git checkout -b feat/something`)
3. Commit your changes (`git commit -am 'feat: add new thing'`)
4. Push to the branch (`git push origin feat/something`)
5. Open a PR

---

## 📄 License

MIT License © 2025 \[Your Name or Organization]

---

## 📬 Contact

For support or collaboration:

* Twitter: [@yourhandle](https://twitter.com/yourhandle)
* Email: [contact@yourdomain.com](mailto:contact@yourdomain.com)
