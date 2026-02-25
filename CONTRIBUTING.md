# Contributing to SwiftX Network

Thank you for your interest in contributing to SwiftX. We are building open,
permissionless settlement infrastructure for the world and we welcome
contributions from developers, researchers, and community members at every
level.

---

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Ways to Contribute](#ways-to-contribute)
- [Development Setup](#development-setup)
- [Branch & Commit Conventions](#branch--commit-conventions)
- [Pull Request Process](#pull-request-process)
- [Smart Contract Contributions](#smart-contract-contributions)
- [Security Vulnerabilities](#security-vulnerabilities)
- [Community](#community)

---

## Code of Conduct

By participating in this project you agree to abide by our
[Code of Conduct](CODE_OF_CONDUCT.md). We enforce it to keep SwiftX a
welcoming and productive environment for everyone.

---

## Ways to Contribute

### Bug Reports
Open a [GitHub Issue](https://github.com/swiftx-network/contracts/issues/new)
using the **Bug Report** template. Include:
- What you expected to happen
- What actually happened
- Steps to reproduce
- Environment details (OS, Anchor version, Solana CLI version)

### Feature Requests
Open a [GitHub Issue](https://github.com/swiftx-network/contracts/issues/new)
using the **Feature Request** template. Describe the problem you are solving,
not just the solution you have in mind.

### Code Contributions
See the [Pull Request Process](#pull-request-process) below.

### Documentation
Even small fixes - typos, broken links, unclear explanations - are genuinely
valuable. Documentation PRs follow the same process as code PRs.

### Protocol Research
Open a Discussion in the
[SwiftX Research forum](https://github.com/swiftx-network/contracts/discussions)
for protocol-level proposals before writing any code.

---

## Development Setup

### Prerequisites

```bash
# Solana CLI
sh -c "$(curl -sSfL https://release.solana.com/stable/install)"

# Anchor CLI
cargo install --git https://github.com/coral-xyz/anchor avm --locked
avm install latest
avm use latest

# Node / Yarn
node --version   # >= 18
yarn --version   # >= 1.22
```

### Clone and build

```bash
git clone https://github.com/swiftx-network/contracts
cd contracts
yarn install
anchor build
anchor test
```

All tests must pass before submitting a PR.

---

## Branch & Commit Conventions

### Branch naming

```
feat/short-description       # new feature
fix/short-description        # bug fix
docs/short-description       # documentation only
refactor/short-description   # code change with no behaviour change
test/short-description       # test additions or fixes
chore/short-description      # build, CI, dependency updates
```

### Commit messages

We follow [Conventional Commits](https://www.conventionalcommits.org/):

```
feat(escrow): add SPL token support to open_escrow
fix(stream): correct claimable_at calculation after cancel
docs(readme): update program addresses for devnet
test(router): add batch escrow size limit test
chore(deps): bump anchor to 0.32.0
```

Format: `type(scope): short imperative description`

- Keep the subject line under 72 characters
- Use the body to explain **why**, not what
- Reference issues with `Closes #123` or `Refs #456`

---

## Pull Request Process

1. **Fork** the repository and create your branch from `main`
2. **Write tests** for any new behaviour - PRs without tests for on-chain
   changes will not be merged
3. **Run the full test suite** locally: `anchor test`
4. **Run the linter**: `yarn lint`
5. **Open the PR** against `main` with:
   - A clear title following commit conventions
   - Description of what changed and why
   - Link to the relevant issue(s)
   - Screenshots or logs for UI/UX changes
6. **Address review feedback** - maintainers aim to review within 72 hours
7. **Squash commits** before merge if requested

### PR size guidelines

- Keep PRs focused - one logical change per PR
- Large refactors should be discussed in an Issue first
- PRs with more than 500 lines changed require extra justification

---

## Smart Contract Contributions

On-chain program changes carry additional requirements because deployed
programs are immutable and handle real user funds.

### Requirements for on-chain PRs

- [ ] All existing tests pass
- [ ] New instructions have full test coverage including error paths
- [ ] Account size changes are documented with size calculations
- [ ] PDA seed changes are documented and backwards-compatible or migration
      path is provided
- [ ] No `unwrap()` or `expect()` in instruction handlers — use `?` operator
      with typed errors
- [ ] All arithmetic uses `checked_add`, `checked_sub`, `saturating_mul` etc.
      No unchecked arithmetic
- [ ] New errors are added to the typed `#[error_code]` enum — no raw error
      strings
- [ ] Events are emitted for all state-changing instructions

### Things that require a security review before merge

- Changes to PDA seed derivation
- Changes to CPI calls
- Changes to fee calculation or distribution
- New token account interactions
- Any change to `ProtocolConfig` or `RouterConfig`

---

## Security Vulnerabilities

**Please do not open public GitHub issues for security vulnerabilities.**

See [SECURITY.md](SECURITY.md) for our responsible disclosure process.

---

## Community

- **Discord** - [discord.gg/swiftx](https://discord.gg/swiftx) — best place
  for real-time discussion
- **Twitter** - [@swiftxnetwork](https://twitter.com/swiftxnetwork)
- **Email** - research@swiftx.network
- **Discussions** - [GitHub Discussions](https://github.com/swiftx-network/contracts/discussions)
  for longer-form protocol questions

---

We appreciate every contribution, no matter the size.
- The SwiftX Core Team
