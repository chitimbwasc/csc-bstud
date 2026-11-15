# Blockchain Music Rights Platform Wtih Utility Token and Automated Royalty Distribution

A blockchain-based prototype for music rights management, tokenized access, and automated royalty distribution — built on NFTs, smart contracts, per-stream re-encryption, and the Cadence ($CADN) utility token.

---

## 📖 Overview

The music industry suffers from fragmented databases, manual reconciliation, delayed payments, opaque royalty calculations, and frequent disputes. **This platform** addresses these problems with a **dual-track architecture**:

| Track | Purpose | Technology |
|-------|---------|------------|
| **Rights & Licensing** | Certify provenance, ownership shares, and licensing contact info | NFTs |
| **Platform Access & Discovery** | Enable secure streaming, demand signalling, and royalty funding | Cadence ($CADN) utility token |

Unlike naive "upload → mint NFT → get paid" models, this platform deliberately avoids unrestricted automatic rewards. It introduces **quality-control stages**, **content protection via per-stream re-encryption**, and a **clear, non-speculative utility role for its token** so the platform remains sustainable and spam-resistant.

---

## ✨ Key Features

- **NFT-Based Rights Certification** — Mint NFTs that record provenance, contributor shares, royalty rules, and licensing contact metadata. These remain useful even if the platform ceases to operate.
- **Cadence ($CADN) Utility Token** — A pure utility token (not equity, not a rights claim) used exclusively for platform access, streaming, and demand signalling.
- **Automated Royalty Splits** — Smart contracts distribute royalties to multiple stakeholders based on predefined shares and verified usage.
- **Per-Stream Re-Encryption** — Media is encrypted under a master key that is **never released to customers**. Each authorized stream is re-encrypted specifically to the paying customer's public key or session. A leaked stream key compromises only that single stream.
- **Quality Control & Anti-Spam** — Review/waiting periods, Cadence-weighted community voting, and optional curation gates prevent spam and low-value uploads from extracting rewards.
- **Immutable Audit Trail** — On-chain records of ownership changes, usage events, and payment settlements.
- **Prototype Dashboard** — Registration, wallet interaction, streaming simulation, royalty monitoring, and independent artist payout demonstration.

---

## 🏗️ Architecture

### Main Components

```
┌─────────────────────────────────────────────────────────┐
│                 User Interface                          │
│  Artists · Rights Admins · Listeners                    │
└────────────────────────┬────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────┐
│                Blockchain Layer                         │
│  Ownership records · NFT data · $CADN balances          │
│  Immutable event logs                                   │
└────────────────────────┬────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────┐
│                Smart Contracts                          │
│  Royalty splitting · $CADN access payments              │
│  Usage recording · Reward distribution                  │
└────────────────────────┬────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────┐
│  Encrypted Media Storage & Re-Encryption Service        │
│  Master-encrypted files (IPFS)                          │
│  Per-stream re-encryption to customer key/session       │
│  ⚠️ Master decryption key NEVER released               │
└────────────────────────┬────────────────────────────────┘
                         │
┌────────────────────────▼────────────────────────────────┐
│                  Backend Service                        │
│  Off-chain data · Key management · Re-encryption        │
│  requests · UI↔blockchain coordination                  │
└─────────────────────────────────────────────────────────┘
```

### High-Level Workflow

1. **Artist registers** a track with contributor and split information.
2. **NFT is minted** as a rights certificate (includes licensing contact metadata).
3. **Media is encrypted** under a master key retained only by the platform and stored (never distributed).
4. **Listener obtains $CADN** (via subscription or other means) and sends it to the content's smart-contract entry point to request a stream.
5. **Upon successful payment**, the system **re-encrypts** the content (or a short-lived content key) specifically to the returning customer's public key or session.
6. **Customer decrypts** only the re-encrypted instance for that stream; the usage event is recorded.
7. **Usage signals** ($CADN volume) feed reward logic; smart contracts distribute royalties per predefined shares.
8. **Artists verify** on-chain usage and payments; third parties contact rights holders via NFT metadata for licensing.

---

## 🪙 Cadence ($CADN) Tokenomics

**Cadence is a pure utility token** — not a governance token, equity, ownership of music rights, or a claim on platform revenue.

**Core utility:**
- Users obtain $CADN via subscription or other platform mechanisms.
- $CADN is spent/directed to a content's smart-contract entry point to request a stream.
- Successful payment triggers per-stream re-encryption to the user's wallet/session.
- $CADN volume received per work acts as an on-chain popularity/usage signal.
- These signals feed automated royalty distribution.

**$CADN is deliberately separated from the NFT rights certificate:**
- **NFT** → records provenance, ownership shares, licensing contact.
- **$CADN** → governs access and measures consumption.

---

## 🔐 Content Protection Model

Media files are **never stored in plaintext** and a **general decryption key is never released**.

**Per-stream re-encryption guarantees:**
- ✅ No general decryption key is ever given to customers.
- ✅ Each stream is bound to a specific paying customer and session.
- ✅ Leakage of a single stream key does not compromise the master content or enable unlimited future access.
- ✅ Access remains strictly one-to-one and platform-mediated.

**Implementation options:** proxy re-encryption, envelope encryption with per-session keys, or equivalent cryptographic patterns.

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Blockchain | Ethereum or lower-cost smart-contract-compatible chain / L2 |
| Smart Contracts | Solidity |
| Frontend | React / Vue + wallet integration |
| Backend | Node.js / Python |
| Storage & Crypto | IPFS (or equivalent) for encrypted media; envelope encryption / proxy re-encryption libraries |
| Key Management | Secure component that never releases the master decryption key |
| Wallet | Browser wallet support for transactions and identity |

---

## 🎯 Objectives

1. Design a digital rights registration model for music assets using NFTs (provenance, ownership shares, licensing contact).
2. Introduce $CADN as a distinct utility token for platform access, streaming, and community voting.
3. Develop smart contracts automating royalty allocation among stakeholders based on verified usage and predefined splits.
4. Implement per-stream / per-session re-encryption with a master key never released to customers.
5. Incorporate quality-control mechanisms (Cadence-weighted voting, review stages) to prevent unrestricted rewards for spam.
6. Create an immutable, traceable record of ownership changes, usage events, and payment settlements.
7. Build a prototype interface for registration, $CADN access, royalty monitoring, and independent artist payouts.

---

## 📦 Expected Deliverables

- Updated project report/documentation reflecting the dual-track architecture, quality controls, and per-stream re-encryption model.
- Blockchain-based prototype for music rights registration and $CADN-powered platform access.
- Smart contracts for royalty distribution, $CADN access payments, and usage logging.
- Demonstration of master-key encryption with per-stream re-encryption (no general key release).
- Simple UI covering registration, $CADN interaction, and royalty monitoring.
- Test cases, sample data, and a final presentation explaining $CADN utility, anti-spam design, and the re-encryption access-control model.

---

## 🚧 Scope

### ✅ Included
- Music asset registration and multi-party ownership/percentage management.
- NFT minting for rights certification and licensing metadata.
- $CADN utility token design for access, streaming, and demand signalling.
- Smart-contract royalty splitting based on predefined shares and verified usage.
- Encrypted content storage with per-stream re-encryption (no general key released).
- Quality-control and anti-spam mechanisms (waiting periods, $CADN-weighted signals, optional review).
- Transaction history, ownership audit trail, usage logs.
- Prototype dashboard for registration, $CADN interactions, royalty monitoring, and artist payouts.

### ❌ Excluded
- Full legal enforcement of copyright transfer or litigation features.
- Production-scale integration with all major streaming services.
- Real-world fiat on/off-ramps at commercial scale.
- Complex multi-jurisdictional dispute arbitration.

---

## ⚠️ Risk & Limitations

| Risk | Mitigation |
|------|-----------|
| Spam / low-quality uploads | No unrestricted automatic payments; waiting periods; $CADN-weighted usage signals |
| Content bypass / key leakage | No general decryption key released; per-stream re-encryption to returning customer |
| Unclear legal status of tokenised rights | NFT treated as provenance certificate + licensing channel, not full copyright conveyance |
| Smart-contract vulnerabilities | Careful design, testing, established patterns |
| Gas costs & usability | Lower-cost chain / L2; focused on-chain operations |
| Token utility / security classification | $CADN strictly for platform access and demand signalling, not investment |
| Key-management complexity | Acknowledged implementation focus area for the prototype |

---

## 🧭 Methodology

1. **Requirements gathering** (incorporating critique on token utility, quality control, content protection).
2. **System analysis & architecture design** (dual NFT/$CADN model, per-stream re-encryption, voting/reward logic).
3. **Smart-contract design & implementation** (royalty splits, $CADN access transfer, event logging).
4. **Front-end prototype development** (registration, wallet interaction, streaming simulation, royalty dashboard).
5. **Blockchain integration, encryption/re-encryption layer, and testing.**
6. **Evaluation** using sample music assets, simulated usage, and demonstration of both platform-mediated and independent payment paths.

---

## 🚀 Getting Started





### Prerequisites
- Node.js (v18+) or Python 3.10+
- A browser wallet (MetaMask or equivalent)
- Access to an IPFS node or pinning service
- A testnet account on your chosen chain

---

## 🗺️ Roadmap / Milestones

- [ ] Requirements & architecture finalization
- [ ] Smart-contract implementation (royalty splits, $CADN access, usage logging)
- [ ] Encrypted media storage + key-management component
- [ ] Per-stream re-encryption service
- [ ] Front-end prototype (registration, streaming, dashboard)
- [ ] End-to-end integration & testing
- [ ] Evaluation with sample assets & simulated usage
- [ ] Final report & presentation

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome. Please open an issue to discuss substantial changes before submitting a pull request.

1. Fork the repo
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add your feature'`)
4. Push and open a Pull Request



> **Cadence — the rhythm of access and fair rewards.**
