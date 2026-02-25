<div align="center">
  <img src="https://myoctocat.com/assets/images/base-octocat.svg" alt="SwiftX" width="120" />
  
  # SwiftX Network

  **Peer-to-peer instant settlement on Solana**
  
  Sub-second escrow · Streaming payments · Fiat-to-fiat remittance rails

 <!--[![Twitter](https://img.shields.io/badge/Twitter-@swiftxnetwork-1DA1F2?style=flat&logo=twitter)](https://twitter.com/swiftxnetwork)-->
  <!--[![Discord](https://img.shields.io/badge/Discord-Join-5865F2?style=flat&logo=discord)](https://discord.gg/swiftx)-->
  <!--[![Docs](https://img.shields.io/badge/Docs-swiftx.network-0A0A0A?style=flat)](https://docs.swiftx.network)-->
  [![License](https://img.shields.io/badge/license-MIT-blue?style=flat)](LICENSE)

</div>

---

## What is SwiftX?

SwiftX is a composable settlement protocol built on Solana that solves three problems with existing payment infrastructure:

- **Latency** - traditional rails take 1–3 business days. SwiftX settles in 400ms.
- **Cost** - wire fees erode micro-transactions. SwiftX charges 0.05% protocol fee.
- **Exclusion** - 1.4 billion adults lack bank accounts. SwiftX works with mobile money.

---

## Core Primitives

| Primitive | Program | Description |
|---|---|---|
| **QLR Escrow** | `swiftx-contracts` | SHA-256 commit-reveal escrow. Funds locked in PDA, released only to pre-committed receiver. |
| **Streaming Payments** | `swiftx-contracts` | Per-second lamport / SPL token drip. Lazy evaluation, no keeper required. |
| **Fee-Market Router** | `swiftx-contracts` | Priority fee oracle, transaction batching, Jito bundle relay, relayer registry. |

---

## Repositories

| Repo | Description |
|---|---|
| [`contracts`](https://github.com/swiftx-network/contracts) | Anchor/Rust on-chain programs — escrow, stream, router |
<!--| [`sdk`](https://github.com/swiftx-network/sdk) | TypeScript SDK — EscrowClient, StreamClient, RouterClient |-->
<!--| [`app`](https://github.com/swiftx-network/app) | React Native mobile app |-->
<!--| [`docs`](https://github.com/swiftx-network/docs) | Protocol documentation |-->
<!--| [`whitepaper`](https://github.com/swiftx-network/whitepaper) | Core whitepaper and companion update |-->

---

## Program Addresses

| Program | Network | Address |
|---|---|---|
| `swiftx_escrow` | Devnet | `SWe...EX` |
| `swiftx_stream` | Devnet | `SWs...EX` |
| `swiftx_router` | Devnet | `SWr...EX` |

---

## Architecture
```
User / SDK
    │
    ▼
swiftx_router   ← single entry point
    │
    ├── CPI ──▶ swiftx_escrow   (QLR commit-reveal)
    └── CPI ──▶ swiftx_stream   (per-second streaming)
```

---

## Getting Started
```bash
# Clone the contracts
git clone https://github.com/swiftx-network/contracts
cd contracts

# Build
anchor build

# Test
anchor test
```

---

## Community & Security

<!---**Discord** — [discord.gg/swiftx](https://discord.gg/swiftx)-->
<!---**Twitter** — [@swiftxnetwork](https://twitter.com/swiftxnetwork)-->
<!---**Email** — research@swiftx.network
<!---**Security** — security@swiftx.network - please disclose vulnerabilities privately-->

---

<div align="center">
  <sub>Built on Solana · MIT License · © 2025 SwiftX Network</sub>
</div>
