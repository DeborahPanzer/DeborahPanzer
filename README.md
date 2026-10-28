<div align="center">

# Hi there, I'm Deborah Panzer 👋

### **Tech Lead & Principal Payment Systems Architect**
*Designing zero-dependency financial engines, formally verified (TLA+) transaction state machines, and high-availability multi-rail clearing infrastructure.*

[![GitHub Sponsors](https://img.shields.io/badge/Sponsor-DeborahPanzer-ea4aaa?logo=github-sponsors&logoColor=white)]([https://github.com/sponsors/DeborahPanzer](https://github.com/sponsors/DeborahPanzer))
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache_2.0-blue.svg)](#)
[![Compliance: PCI-DSS v4.0.1 | OFAC | ISO-20022](https://img.shields.io/badge/Compliance-PCI--DSS_v4.0.1_%7C_OFAC_%7C_ISO--20022-blueviolet)](#)
[![Formal Verification: TLA+](https://img.shields.io/badge/Formal_Verification-TLA%2B-informational)](#)
[![Focus: FinTech & Distributed Systems](https://img.shields.io/badge/Focus-FinTech_%7C_Distributed_Systems-2ea44f)](#)

</div>

---

## 🏛️ Enterprise FinTech Infrastructure Suite

I architect and maintain modular, zero-dependency, production-grade financial abstractions engineered to eliminate double-charging, guarantee **Serializable ACID** & **Two-Phase Commit (2PC)** invariants, enforce **PCI-DSS v4.0.1** & **OFAC SDN** compliance, and orchestrate end-to-end money movement at scale:

```text
 [Inbound Card / Wallet Pay-In]               [Dispute & Risk Shield]
        │                                               │
        ▼                                               ▼
┌──────────────────────┐                       ┌──────────────────────┐
│ 💳 checkout-core     │◄─────────────────────►│ 🛡️ refund-guard      │
│ (TypeScript 100%)    │   Webhook & Dispute   │ (TypeScript 100%)    │
│ • PCI-DSS AES-256    │   State Sync          │ • Chargeback Defense │
│ • 3DS2 & Reg II      │                       │ • Automated Evidence │
│ • Interchange++ & FX │                       │ • Balance Protection │
└──────────┬───────────┘                       └──────────┬───────────┘
           │                                              │
           │         Zero-Sum Double-Entry Posting        │
           └───────────────────┐      ┌───────────────────┘
                               ▼      ▼
                       ┌──────────────────────┐
                       │ 🏛️ ledger-vault      │
                       │ (Go 100%)            │
                       │ • Serializable ACID  │
                       │ • ISO-4217 Precision │
                       │ • SHA-256 Hash-Chain │
                       └──────────┬───────────┘
                                  │
                                  │ Atomic 2PC Settlement & Reserve Holdback
                                  ▼
                       ┌──────────────────────┐
                       │ 💸 payout-engine     │
                       │ (Go 100%)            │
                       │ • OFAC & IRS 1099-K  │
                       │ • FedNow ISO-20022   │
                       │ • NACHA ACH & SEPA   │
                       └──────────────────────┘
```

### Core Repositories & Live CI Matrix

| Repository | Role & Domain | Runtime | Verification & Compliance | CI Status |
| :--- | :--- | :--- | :--- | :--- |
| 💳 **[checkout-core](https://github.com/DeborahPanzer/checkout-core)** | Inbound Payment & Acquiring Engine | `TypeScript 100%` | PCI-DSS v4.0.1, EMV 3DS2, Reg II, ISO-8583, TLA+ | [![CI](https://github.com/DeborahPanzer/checkout-core/actions/workflows/ci.yml/badge.svg)](https://github.com/DeborahPanzer/checkout-core/actions/workflows/ci.yml) |
| 💸 **[payout-engine](https://github.com/DeborahPanzer/payout-engine)** | Outbound Treasury & Clearing Gateway | `Go 100%` | OFAC SDN, NACHA ACH, FedNow ISO-20022, IRS 1099-K, TLA+ | [![CI](https://github.com/DeborahPanzer/payout-engine/actions/workflows/ci.yml/badge.svg)](https://github.com/DeborahPanzer/payout-engine/actions/workflows/ci.yml) |
| 🛡️ **[refund-guard](https://github.com/DeborahPanzer/refund-guard)** | Dispute & Chargeback Defense Middleware | `TypeScript` | Idempotent Reversals, HMAC Webhooks, Audit Ledgers | `Active` |
| 🏛️ **[ledger-vault](https://github.com/DeborahPanzer/ledger-vault)** | Immutable Double-Entry Accounting Core | `Go` | Serializable ACID, Zero-Sum Invariants, SHA-256 Chain | `Active` |

---

### 🔍 Deep-Dive Architectural Highlights

* 💳 **[checkout-core](https://github.com/DeborahPanzer/checkout-core)** — **Enterprise Acquiring & Transaction Engine (`v1.0.0`):**
  * **PCI-DSS v4.0.1 Cryptographic Isolation:** Authenticated **AES-256-GCM** Primary Account Number (PAN) tokenization vault, ISO/IEC 7812 Luhn validation, and **Apple Pay / Google Pay EMV TAVV cryptogram** verification.
  * **Smart Routing & Conversion Optimization:** US Federal Reserve **Regulation II (Durbin Amendment)** least-cost PINless debit router (`STAR`, `NYCE`, `PULSE`, `ACCEL`), **EMV 3-D Secure 2 (3DS2)** PSD2 SCA exemption engine, **ISO-8583** hard/soft decline classifier, and multi-gateway **Circuit Breakers**.
  * **Financial Precision & Auditing:** Fixed-point `BigInt` **ISO-4217 FX conversion** with deterministic **Banker's Rounding (Round Half to Even)**, **Interchange++** scheme fee calculator, **ISO-20022 (`pain.001.001.09`)** XML credit transfer generator, 3-way settlement reconciliation, and **SHA-256 Merkle Tree** batch inclusion proofs.
* 💸 **[payout-engine](https://github.com/DeborahPanzer/payout-engine)** — **Automated Treasury & Multi-Rail Disbursement Gateway (`v1.0.0`):**
  * **Atomic 2PC & Marketplace Treasury:** Unanimous **Two-Phase Commit (2PC)** batch coordinator, multi-party **Stripe Connect-style split settlement** with exact penny-remainder conservation, configurable **Rolling Reserve** holdbacks, multilateral intraday obligation netting, and **Nostro liquidity pool** routing.
  * **Multi-Rail Clearing & Failover:** Real-time **US FedNow / TCH RTP (`ISO-20022 pacs.008.001.08`)** XML builder, **94-byte NACHA ACH CCD** generator with weighted Modulo-10 ABA routing validation and R01–R29 return code classification, **SEPA ISO-13616 Modulo-97** IBAN validator, and automatic rail failover.
  * **Pre-Disbursement Regulatory Shield:** **OFAC SDN sanctions screening**, statutory **24% US IRS Form 1099-K backup withholding** for unverified TINs, 24-hour beneficiary bank-swap cooling locks (ATO defense), and bounded exponential backoff retry queues with Dead-Letter Queue (DLQ) isolation.
* 🛡️ **[refund-guard](https://github.com/DeborahPanzer/refund-guard)** — **Idempotent Dispute & Chargeback Management Middleware:**
  * Real-time webhook state synchronization, constant-time HMAC-SHA256 signature verification, SHA-256 cryptographic audit ledgers, and automated merchant balance protection against friendly fraud and double-refund race conditions.
* 🏛️ **[ledger-vault](https://github.com/DeborahPanzer/ledger-vault)** — **Immutable Double-Entry Accounting & Reconciliation Engine:**
  * Append-only financial ledger enforcing PostgreSQL `SERIALIZABLE` ACID isolation, strict zero-sum debit/credit invariants ($\sum \text{Debits} - \sum \text{Credits} = 0$), ISO-4217 minor-unit precision, and tamper-evident cryptographic hash-chaining.

---

## ⚙️ Core Architecture & Tech Stack

* **Languages & Runtimes:** TypeScript (`strict` zero-dependency ESM/CommonJS), Go (Golang 1.22+ with concurrency `-race` verification), PostgreSQL (`SERIALIZABLE` ACID SQL), TLA+ (Formal Mathematical Specification).
* **Payment Protocols & Banking Rails:** ISO-20022 (`pain.001` & `pacs.008`), ISO-8583 Acquirer Messaging, US FedNow / RTP, NACHA ACH (94-byte CCD/PPD), SEPA Credit Transfer (ISO-13616 IBAN Mod-97), EMV 3-D Secure 2 (3DS2), Apple Pay / Google Pay Network Tokens (DPAN/TAVV).
* **Security, Risk & Regulatory Compliance:** PCI-DSS v4.0.1 Envelope Encryption (AES-256-GCM & HMAC-SHA256 Blind Indexing), OFAC SDN Sanctions Screening, US Regulation II Debit Routing, IRS Form 1099-K Backup Withholding, AVS & Sliding-Window Velocity Limiting, SHA-256 Merkle Tree Auditing.
* **Distributed Systems & Resiliency:** Hybrid Two-Phase Commit (2PC) & LIFO Compensating Sagas, Transactional Outbox Pattern with Jittered Exponential Backoff, Multi-Acquirer Circuit Breakers, Three-Way Settlement Reconciliation.

---

## 💖 Support Open-Source FinTech Tooling

Building financial-grade infrastructure requires rigorous edge-case testing, formal TLA+ state verification, continuous vulnerability audits, and automated compliance testing against banking clearing specifications.

Your sponsorship directly fuels:
* 🛠️ Maintenance of production-ready, zero-dependency modules for high-reliability payment architectures.
* 🔒 Zero-day security patching, PCI-DSS v4.0.1 / OFAC compliance research, and formal invariant verification.
* ⚡ Continuous integration pipelines and deterministic multi-rail clearing test suites.

👉 **[Become a GitHub Sponsor to support ongoing open-source maintenance](https://github.com/sponsors/DeborahPanzer)**

---

<div align="center">
  <sub>Architected with mathematical precision for resilient, fault-tolerant financial systems. 🚀</sub>
</div>
