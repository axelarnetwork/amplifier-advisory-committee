# Amplifier Advisory Committee Assessment on Solana Proposal

## Project Overview
- **Chain Name**: Solana
- **Proposal Reviewed**: [Solana Integration Proposal](PROPOSAL.md)
- **Source Code**: [https://github.com/eigerco/solana-axelar](https://github.com/eigerco/solana-axelar)

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

Solana’s integration with Axelar aims to enable seamless cross-chain transactions and interoperability by leveraging Axelar's General Message Passing (GMP) and security infrastructure. This integration will facilitate cross-chain token transfers, smart contract interactions, and liquidity sharing, enhancing the utility and adoption of both Solana and Axelar.

### 1.2 Evaluation Approach

The Committee’s assessment methodology included the following:

- **Research and Documentation Review**: A detailed review of technical documentation, Solana’s GitHub repositories, whitepapers, and Solana Improvement Documents (SIMDs) to understand the network’s capabilities and integration requirements.
- **Security Audits and Testing**: Examination of Solana's codebase, previously conducted audits, and tests for vulnerabilities.
- **Collaboration with the Solana Team**: Ongoing discussions with the Solana development team to understand their infrastructure, upgrade plans, incident response protocols, and readiness for cross-chain integrations.

### 1.3 Assessment Framework

The assessment framework focused on the following key areas:

- **Protocol Integrity**: Evaluating Solana’s consensus mechanism (TODO: add link), validator decentralization, and the scalability of its architecture. (TODO: Check if scalability is relevant here)
- **Security Risks**: Identifying vulnerabilities within Solana’s VM, bridge components, and network infrastructure. (TODO: Check if this is relevant)
- **Operational Risks**: Assessing challenges developers might face when integrating with Solana, such as stability, untested features, or constraints.
- **Compliance and Governance Risks**: Reviewing Solana’s governance model, community involvement, and regulatory considerations.
- **Code Quality and Transparency**: Analysis of the codebase, audit results, and adherence to development best practices. (TODO: Revisit codebase analysis point)
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
  core, PoH employs a delay function based on sequentially computing hashes,
  where each new hash output depends on the previous one. By requiring these
  computations to be executed in order, the computation of the repeated hashing
  function cannot be parallelized, thereby adding a delay. Note that the
  verification of the function's output is not efficient though (using the
  efficiency definition of [Verifiable Delay
  Functions](https://eprint.iacr.org/2018/601.pdf)), since it requires
  recomputing all hashes sequentially.
- **Proof of Stake (PoS)**: Solana's PoS component is used to confirm the
  sequence of transactions produced by the PoH mechanism and to devise the
  [slot leader schedule](https://docs.anza.xyz/consensus/leader-rotation).
  Briefly, Solana's execution is divided in epochs, with each epoch having a
  pre-defined leader schedule. To compute the schedule, a PoH _height_ is used
  to both seed a pseudo-random algorithm. Following, the leader schedule is
  computed from this algorithm, by randomly sampling the set active validators
  weighted by their stake at the chosen height. Additionally, validators
  participate in [voting](https://docs.anza.xyz/consensus/vote-signing) in
  order to resolve forks, with each validator weighted by their stake (own and
  delegated).
- **Turbine**: A custom multi-layered [block propagation
  mechanism](https://docs.anza.xyz/consensus/turbine-block-propagation).
  At a high level, each block is broken into multiple components, called shreds,
  which are then encoded in groups using Reed-Solomon erasure coding.
  Nodes are organized in layers in a deterministic manner, weighted by each
  node's stake. A special root node receives all shred groups from the slot
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

Notably, no formal security analysis of Solana's consensus mechanism are
available as of March 2025. Therefore, it is unclear whether and under which
assumptions this mechanism guarantees the ledger's robustness and core
properties, safety and liveness.

### 2.2 Governance and Compliance

Solana's governance model balances between stakers and validators. Essentially,
the community proposes changes following the [Solana Improvement Document
(SIMD)](https://github.com/solana-foundation/solana-improvement-documents)
format. Validators signal their stance by voting on a proposed change in a
nonbinding, advisory manner, whereas the final decision occurs when validators
choose which software version to run. Solana stakers participate indirectly by
delegating their voting rights to validators.

The [Solana Foundation](https://solana.org) plays a central role in Solana's
ecosystem in various ways. First, it is the only entity that develops the
ledger's core node software. Second, at the system's onset it directly held a
[10.5% of all tokens](https://crypto.com/en/university/solana-tokenomics) and
controlled 38.9% by managing the Community Reserve. Third, it is the main force
of [funding](https://solana.org/grants-funding) in the ecosystem.

---

## Section 3: Security and Risks
### 3.1 Smart Contract Security and Vulnerabilities
Solana smart contracts, called programs, are primarily written in Rust and compiled using LLVM into Solana's custom version of eBPF (called sBPF). Hence, any programming language that can be compiled to sBPF can be used to write Solana programs. This includes but is not limited to Rust, C, C++, and Solidity.
This multi-language support and compiler diversity eliminates single points of failure in the compilation toolchain, enhancing the overall security and resilience of Solana's smart contract ecosystem.

Solana utilizes an account-based model, where all data, including programs, are organized under accounts. This enables the Solana Virtual Machine to perform parallel transaction execution when accessing independent accounts, achieving high throughput. However, it also introduces additional security considerations for developers, who need to grasp the intricacies of this unique programming model in order to write secure programs.
Anchor, a Rust-based framework for building Solana programs, has been developed to simplify the development process and minimize security risks. Anchor provides simplified syntax and out-of-the-box implementations for common security checks, making it easier to write secure programs.
