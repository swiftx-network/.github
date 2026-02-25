# Security Policy

SwiftX programs are deployed on Solana and handle real user funds. We take
security seriously and appreciate responsible disclosure from the community.

---

## Reporting a Vulnerability

**Please do NOT open a public GitHub issue for security vulnerabilities.**
Public disclosure before a fix is deployed puts user funds at risk.

### Contact

| Channel | Address | Response Time |
|---|---|---|
| Email (preferred) | <!--security@swiftx.network-->the3rdweblabs@gmail.com | 48 hours |
| Encrypted email | PGP key at <!--swiftx.network/pgp.asc--> | 48 hours |
| Discord (DM core team) | <!--discord.gg/swiftx--> | 72 hours |

### What to include in your report

Please provide as much of the following as possible:

- **Description** - clear explanation of the vulnerability
- **Impact** - what an attacker could achieve (fund loss, DoS, manipulation)
- **Affected component** - which program and instruction(s)
- **Reproduction steps** - minimal steps or PoC code to reproduce
- **Suggested fix** - if you have one (optional but appreciated)

We will acknowledge receipt within **48 hours** and provide a timeline for
resolution within **7 days**.

---

## Supported Versions

| Deployment | Supported |
|---|---|
| Mainnet (latest) | ✅ Active |
| Devnet (latest) | ✅ Active |
| Devnet (previous) | ⚠️ Best effort |
| Localnet / forks | ❌ Not supported |

---

## Bug Bounty

SwiftX operates a bug bounty programme for verified vulnerabilities in
deployed on-chain programs. Rewards are evaluated based on severity:

| Severity | Description | Reward |
|---|---|---|
| **Critical** | Direct loss of user funds, theft via exploit | Up to ??<!--$25,000 USDC--> |
| **High** | Fund freeze, permanent DoS, privilege escalation | Up to ??<!--$10,000 USDC--> |
| **Medium** | Temporary DoS, incorrect state, fee manipulation | Up to ??<!--$4,000 USDC--> |
| **Low** | Minor logic errors, informational issues | Up to ??<!--$500 USDC--> |

### Bounty scope

**In scope:**
- `swiftx_escrow` — all instructions (open, claim, refund)
- `swiftx_stream` — all instructions (create, withdraw, top-up, cancel)
- `swiftx_router` — all instructions (register, batch, reputation)
- Cross-program invocation (CPI) interfaces
- PDA derivation and account validation logic
- Fee calculation and distribution

**Out of scope:**
- Front-end / UI bugs
- Issues requiring physical access to a user's device
- Social engineering attacks
- Issues in third-party dependencies (Anchor, SPL Token) not specific to SwiftX
- Issues already known or previously reported

### Bounty rules

- First reporter of a unique vulnerability receives the reward
- Reward paid in USDC within 30 days of patch deployment
- Public disclosure coordinated with SwiftX team — minimum 90-day embargo
  after fix is deployed
- Researchers must not access, modify, or destroy user data during testing
- Testing must be performed on devnet or localnet — never mainnet

---

## Disclosure Policy

1. Reporter submits vulnerability to <!--security@swiftx.network-->the3rdweblabs@gmail.com
2. SwiftX acknowledges within 48 hours
3. SwiftX investigates and develops a fix
4. Fix deployed to devnet for verification
5. Fix deployed to mainnet with upgrade authority
6. Reporter notified of deployment
7. Coordinated public disclosure after 90 days (or earlier by mutual agreement)
8. Reporter credited in changelog (unless anonymity requested)

---

## Known Security Properties

For reference, the following security properties are by design:

| Property | Mechanism |
|---|---|
| Funds cannot be stolen without nonce | SHA-256 pre-image resistance — O(2¹²⁸) to break |
| Receiver address cannot be changed after open | Embedded in PDA at open time, validated on-chain |
| Relayer cannot redirect funds | Destination enforced by on-chain program, not relayer |
| Program upgrades require 7-day timelock | XFT DAO multisig enforced by upgrade authority |
| Protocol can be paused in emergency | `paused` flag in ProtocolConfig, DAO controlled |
| Escrows always claimable if FIL offline | On-chain programs accessible via any Solana RPC |

---

## Past Security Audits

| Auditor | Scope | Date | Report |
|---|---|---|---|
| — | — | Pending | — |

Audit reports will be published here upon completion. SwiftX is targeting a
full audit of all three programs before mainnet launch.

---

## Contact

<!--security@swiftx.network-->
the3rdweblabs@gmail.com
