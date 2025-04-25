# Amplifier Advisory Committee Assessment on Solana Proposal

## Project Overview
- **Chain Name**: Solana
- **Proposal Reviewed**: [Solana Integration Proposal](PROPOSAL.md)
- **Source Code**:
  - [Programs on Solana](https://github.com/eigerco/solana-axelar/tree/main/solana)
  - [Multisig Prover Contract on Axelar](https://github.com/eigerco/axelar-amplifier/tree/add-multisig-prover-sol-logic/contracts/multisig-prover)
  - [Axelar Relayer](https://github.com/eigerco/axelar-solana-relayer)

### Table of Contents
  #### [Section 1: Assessment Methodology](#section-1-assessment-methodology-1)
  #### [Section 2: Network and Protocol Integrity](#section-2-network-and-protocol-integrity-1)
  #### [Section 3: Security and Risks](#section-3-security-and-risks-1)
  #### [Section 4: Axelar Integration Components](#section-4-axelar-integration-components-1)
  #### [Conclusion](#conclusion-1)
---

---

## Section 1: Assessment Methodology

### 1.1 Integration Overview

Solana’s integration with Axelar aims to enable seamless cross-chain transactions and interoperability by leveraging Axelar’s General Message Passing (GMP) and security infrastructure. This integration will facilitate cross-chain token transfers, smart contract interactions, and liquidity sharing, enhancing the utility and adoption of both Solana and Axelar.

### 1.2 Evaluation Approach

The Committee’s assessment methodology included the following:

- **Research and Documentation Review**: A detailed review of technical documentation, Solana’s GitHub repositories, whitepapers, and Solana Improvement Documents (SIMDs) to understand the network’s capabilities and integration requirements.
- **Security Audits and Testing**: Examination of Solana’s codebase, previously conducted audits, and tests for vulnerabilities.
- **Collaboration with the Solana Team**: Ongoing discussions with the Solana development team to understand their infrastructure, upgrade plans, incident response protocols, and readiness for cross-chain integrations.

### 1.3 Assessment Framework

The assessment framework focused on the following key areas:

- **Protocol Integrity**: Evaluating Solana’s consensus mechanism, validator decentralization, and the scalability of its architecture.
- **Security Risks**: Identifying vulnerabilities within Solana’s VM, bridge components, and network infrastructure.
- **Operational Risks**: Assessing challenges developers might face when integrating with Solana, such as stability, untested features, or constraints.
- **Compliance and Governance Risks**: Reviewing Solana’s governance model, community involvement, and regulatory considerations.
- **Code Quality and Transparency**: Analysis of the codebase, audit results, and adherence to development best practices.
- **Integration Plan**: Reviewing deployment and maintenance strategies for the Axelar-Solana integration, including monitoring systems and threat detection mechanisms.

### 1.4 Assessment Criteria

The desirable properties related to Solana’s architecture and its integration with Axelar included:

- **Security**: How Solana’s consensus safeguards against exploits.
- **Scalability and Performance**: Solana’s ability to handle high transaction throughput with low latency.
- **Decentralization**: The extent of validator distribution and its impact on the network’s security.
- **Governance**: The mechanisms for protocol upgrades, decision-making, and dispute resolution.
- **Fault Tolerance**: Solana’s ability to recover from network halts or failures without impacting system integrity.
- **Transparency**: Open-source availability of the codebase, audit reports, and developer documentation.

---

## Section 2: Network and Protocol Integrity

### 2.1 Consensus and Network Architecture

[Solana](https://solana.com/solana-whitepaper.pdf) is a Layer 1 blockchain
engineered for high performance and scalability, supporting thousands of
transactions per second with low latency. It employs a system of validators and
designated leaders who alternate in producing blocks, running a [hybrid
consensus mechanism](https://www.shinobi-systems.com/primer.html) that combines
Proof-of-History (PoH) with Proof-of-Stake (PoS).

Key Architectural Features:
- **Proof of History (PoH)**: A timekeeping mechanism that provides a historical
  record proving that an event has occurred at a specific moment in time. At its
  core, PoH uses a delay function based on sequentially computing hashes,
  where each new hash output depends on the previous one. By requiring these
  computations to be executed in order, the computation of the repeated hashing
  function cannot be parallelized, thereby adding a delay. Note that the
  verification of the function’s output is not efficient though (using the
  efficiency definition of [Verifiable Delay
  Functions](https://eprint.iacr.org/2018/601.pdf)), since it requires
  recomputing all hashes sequentially.
- **Proof of Stake (PoS)**: Solana’s PoS component is used to confirm the
  sequence of transactions produced by the PoH mechanism and to devise the
  [slot leader schedule](https://docs.anza.xyz/consensus/leader-rotation).
  Briefly, Solana’s execution is divided in epochs, with each epoch having a
  pre-defined leader schedule. To compute the schedule, a PoH _height_ is used
  to both seed a pseudo-random algorithm. Following, the leader schedule is
  computed from this algorithm, by randomly sampling the set of active validators
  weighted by their stake at the chosen height. Additionally, validators
  participate in [voting](https://docs.anza.xyz/consensus/vote-signing) in
  order to resolve forks, with each validator weighted by their stake (own and
  delegated).
- **Turbine**: A custom multi-layered [block propagation
  mechanism](https://docs.anza.xyz/consensus/turbine-block-propagation).
  At a high level, each block is broken into multiple components, called shreds,
  which are then encoded in groups using Reed-Solomon erasure coding.
  Nodes are organized in layers in a deterministic manner, weighted by each
  node’s stake. A special root node receives all shred groups from the slot
  leader and disseminates them to the rest of the network following the computed
  layer structure, such that eventually all nodes receive enough shreds so that
  they can recompute the block.
- **Gulf Stream**: A custom [transaction forwarding
  protocol](https://solana.com/news/gulf-stream--solana-s-mempool-less-transaction-forwarding-protocol)
  designed to streamline message propagation and reduce network congestion. Its
  main idea is that, since the leader schedule is deterministic and publicly
  known ahead of time, clients and validators forward transactions to the
  expected slot leader ahead of time, in order to validate transactions faster
  and reduce confirmation times, effectively eliminating the traditional
  mempool.
- **Slashing**: Solana implements a _manual_ [slashing
  mechanism](https://solana.com/staking). Currently, a safety violation [causes
  the network to
  halt](https://docs.anza.xyz/proposals/optimistic-confirmation-and-slashing/#slashing-roadmap).
  In such event, the honest nodes are expected to manually investigate the
  event, identify the faulty nodes, and manually slash their stake, after which
  point the network is restarted without them.
- **Smart contracts**: Solana supports smart contracts, called
  ["programs"](https://solana.com/docs/core/programs), which are written in a
  Solana-focused language, [Anchor](https://www.anchor-lang.com/docs), or [native
  Rust](https://solana.com/docs/programs/rust).

Notably, no formal security analysis of Solana’s consensus mechanism is
available as of March 2025. Therefore, it is unclear whether and under which
assumptions this mechanism guarantees the ledger’s robustness and core
properties, safety and liveness.

### 2.2 Governance and Compliance

Solana’s governance model balances between stakers and validators. Essentially,
the community proposes changes following the [Solana Improvement Document
(SIMD)](https://github.com/solana-foundation/solana-improvement-documents)
format. Validators signal their stance by voting on a proposed change in a
non-binding, advisory manner, whereas the final decision occurs when validators
choose which software version to run. Solana stakers participate indirectly by
delegating their voting rights to validators.

The [Solana Foundation](https://solana.org) and [Solana Labs](https://www.solanalabs.com) play a central role in Solana’s ecosystem in various ways.
First, the only validator implementation as of March 2025 for Solana is Agave, developed by Anza, a company consisting of former executives and core engineers from Solana Labs. The software was [forked](https://solana.com/ru/news/solana-labs-anza-fork) by the [original Solana validator client](https://github.com/solana-labs/solana) developed by Solana Labs which has since been archived. Second, at the system’s onset, the Solana Foundation directly held [10.5% of all tokens](https://crypto.com/en/university/solana-tokenomics) and controlled 38.9% by managing the Community Reserve.
Additionally, 12.5% of the tokens went to the founding team and 31% went to venture capitalists.
Third, the Solana Foundation is the main force of [funding](https://solana.org/grants-funding) in the ecosystem.

---

## Section 3: Security and Risks
### 3.1 Smart Contract Security and Vulnerabilities
Solana smart contracts, called programs, are primarily written in Rust and compiled using LLVM into Solana’s custom version of eBPF (called sBPF). Hence, any programming language that can be compiled to sBPF can be used to write Solana programs. This includes but is not limited to Rust, C, C++, and Solidity.
This multi-language support and compiler diversity eliminates single points of failure in the compilation toolchain, enhancing the overall security and resilience of Solana’s smart contract ecosystem.

Solana utilizes an account-based model, where all data, including programs, are organized under accounts. This enables the Solana Virtual Machine to perform parallel transaction execution when accessing independent accounts, achieving high throughput. However, it also introduces additional security considerations for developers, who need to grasp the intricacies of this unique programming model in order to write secure programs.
Evidence of this is the Wormhole bridge exploit in February 2022, which resulted in a $320 million loss due to insufficient validation in a Solana program’s signature verification logic.
Anchor, a Rust-based framework for building Solana programs, has been developed to simplify the development process and minimize security risks. Anchor provides simplified syntax and out-of-the-box implementations for common security checks, making it easier to write secure programs.

Solana demonstrates an ongoing commitment to strong security standards through:
* Maintaining a lucrative [bug bounty program](https://github.com/anza-xyz/agave/security#security-bug-bounties) which incentivizes community-driven vulnerability identification.
* Performing frequent and thorough [audits](https://github.com/anza-xyz/security-audits) with third-party auditing firms such as Zellic, Halborn, OtterSec, Trail of Bits, and others.
* Quick response times to security vulnerabilities and network outages indicating good monitoring mechanisms.

However, Solana over the years has been plagued by a series of outages and other incidents which are important to consider:
- **December 4, 2020:**  A six-hour outage occurred due to a block propagation bug in Solana’s Turbine protocol. The problem was resolved by improving block tracking and fault detection mechanisms.
- **September 14, 2021:** A 17-hour outage caused by a DDoS attack that pushed transaction loads beyond the network’s capacity, stalling consensus. The fix involved rate-limiting and improved consensus voting prioritization.
- **January 6 - 12, 2022:** Degraded performance and partial outages were observed due to excessive duplicate transactions spammed by bots. Solana 1.8.12 and 1.8.14 introduced deduplication and performance optimizations.
- **April 30, 2022:** A seven-hour outage due to high number of transactions that overwhelmed the network. Solana showed much improved performance compared to the 2021 DDoS attack and the patch was quickly released.
- **June 1, 2022:** A four-and-a-half-hour outage occurred due to a consensus failure triggered by duplicate processing of durable nonce transactions. The bug was patched in version 1.10.23.
- **September 30, 2022:** A six-hour outage occurred due to a bug in the consensus implementation that caused a fork. It was quickly resolved.
- **February 25, 2023:** A 19-hour outage was triggered due to an issue in Turbine’s deduplication logic. The network had to manually downgrade to the previous stable version.
- **February 6, 2024:** A five-hour outage occurred due to a bug in the Agave client’s just-in-time (JIT) compiler. The legacy loader that was causing the issue was disabled.
- **August 5–8, 2024:** A critical ELF file alignment bug, that could have caused network outage, was quietly patched in coordination with validators. The disclosure raised concerns about decentralization.

As of March 2025, Solana has not experienced any outages since February 2024. However, their live production network is still called Mainnet-beta, which indicates that continuous vigilance is still required.

### 3.2 Risks and Concerns
Areas of concern include:
- **Consensus Mechanism:** As of March 2025, no formal security analysis of Solana’s consensus mechanism is available.
- **Network Outages:** Solana has experienced a series of outages over the years. Potential network stalls should be taken seriously into account when designing cross-chain applications enabled by this Axelar integration.
- **Centralization Risks:** There are centralization risks about the Solana network that should be considered: (1) Agave is the only validator client as of March 2025, although there are plans to launch Firedancer, a new independent validator client, in 2025; (2) The Solana foundation controls a large sum of the network tokens; (3) The Solana Foundation is the main force of funding in the ecosystem; (4) Secretly coordinated network upgrades such as the one in August 2024.
- **Smart Contract Security:** Solana introduces a unique programming model that requires careful attention from developers in order to avoid pitfalls that expose the system to attacks.

Despite its challenges, Solana’s commitment to innovation and proactive security measures positions it as a strong player in the blockchain ecosystem. By addressing these concerns and continuing to prioritize security, Solana can maintain trust and support its growing user base.