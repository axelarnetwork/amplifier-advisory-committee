# Chain Integration Proposal

Integrating Soroban with the Axelar network will unlock new capabilities for decentralized applications (dApps) by enabling seamless cross-chain interoperability, enhanced scalability, and robust security. This partnership aims to leverage Soroban’s efficient WASM-based smart contract platform and Stellar’s infrastructure to provide a foundation for innovative use cases in decentralized finance (DeFi), tokenized assets, and cross-border payments.

---

## Overview

### Project Overview

**Chain Name:** Soroban

**Project Description:**  
Soroban is a smart contract platform built on the Stellar blockchain, designed to power decentralized applications (dApps) with a focus on simplicity, performance, and trustworthiness. Leveraging Stellar’s fast and efficient transaction protocol, Soroban introduces robust features for developers to build and deploy scalable, secure, and low-latency applications. Its integration with Stellar’s existing infrastructure ensures seamless functionality for financial and enterprise use cases.

**Proposer:** Interop Labs (on behalf of Stellar Development Foundation)

**Contact Information:**

- **Slack:** Confidential
- **Stellar Website:** [https://stellar.org](https://stellar.org)
- **Axelar Website:** [https://www.axelar.network/](https://www.axelar.network/)

---

## Chain Overview

### At-A-Glance

**Justification for Soroban:**  
Integrating Soroban with the Axelar network will significantly enhance interoperability across blockchain ecosystems by enabling seamless cross-chain communication and asset transfer capabilities. Soroban’s efficient smart contract platform, combined with Axelar’s secure and scalable infrastructure, will provide developers and users with new opportunities for decentralized finance (DeFi), asset tokenization, and enterprise blockchain solutions. This integration will allow Stellar’s ecosystem to expand its functionality, gain access to broader liquidity, and facilitate interactions with other blockchains.

**Management Team Credentials:**  
Soroban is developed and maintained by the Stellar Development Foundation (SDF), a nonprofit organization with years of experience supporting the Stellar network. SDF’s leadership includes blockchain experts and seasoned professionals committed to fostering financial inclusion and innovation:

- **Denelle Dixon:** CEO and Executive Director, experienced in legal, regulatory, and operational leadership.
- **Justin Rice:** VP of Ecosystem, leading efforts to expand Stellar’s developer community and integrations.
- **Jed McCaleb:** Stellar co-founder and advisor, known for his contributions to blockchain technology and decentralized systems.
- **Graydon Hoare:** Principal Engineer, responsible for Soroban’s development and network integration, with extensive experience in blockchain architecture and security.
- **David Mazières:** Stellar’s Chief Scientist, an expert in distributed systems and cryptographic security.

### Notable Use Cases

- **MoneyGram International:** [Global leader in cross-border payments and remittances](https://stellar.org/products-and-tools/moneygram), leveraging Stellar for digital asset transactions and financial inclusion.
- **Circle's USDC:** [A stablecoin issued on Stellar](https://stellar.org/products-and-tools/circle-usdc-eurc), facilitating fast, scalable, and cost-effective digital transactions for businesses and individuals.
- **Flutterwave:** [A leading African payments company](hhttps://stellar.org/press/flutterwave-enables-new-europe-africa-payment-corridors-via-stellar) utilizing Stellar for seamless cross-border payments and financial access.
- **Allbridge:** [Enabling seamless tokenized asset transfers](https://stellar.org/press/allbridge-launch-connects-stellar-network-to-ethereum-solana-and-polygon) between Stellar Network, Ethereum, Solana, Celo, and Polygon.
- **Starbridge:** [A blockchain solution](https://stellar.org/blog/developers/starbridge-a-trust-minimized-bridge-between-stellar-and-other-blockchains) allowing transfer of local assets and wrapped assets to facilitate symmetrical bidirectional capabilities.
- **Solar Wallet:** [An intuitive wallet](https://solarwallet.io) for accessing dApps, managing assets, and seamless Soroban integration.
- **Interstellar:** [A financial infrastructure](https://interstellar.com/what-we-do/) for remittances and cross-border payments.

---

## Technology Overview

### Protocol Overview

Soroban is a WebAssembly (WASM)-based smart contract platform leveraging Stellar’s highly efficient consensus algorithm, the Stellar Consensus Protocol (SCP). It supports up to **5,000 transactions per second (TPS)** under optimal conditions.

### Key Features

- **Smart Contracts:** Modular, composable, and built in a WASM execution environment.
- **Transaction Finality:** Near-instant, ensuring real-time performance for financial systems.
- **Developer Tools:** Includes the Stellar Laboratory, Horizon API, and Soroban CLI for seamless dApp development.
- **Cross-Chain Interoperability:** Facilitating multi-network DeFi, tokenized asset transfers, and payments.

---

## Axelar Integration Components

**Amplifier and External Contracts**  
Integrating Soroban with Axelar includes the following components:

- **[Ampd](https://github.com/axelarnetwork/axelar-amplifier):** Responsible for voting and signing within the Axelar Amplifier protocol, ensuring secure and decentralized decision-making.
- **[Gateway Contracts](https://github.com/axelarnetwork/axelar-cgp-stellar):** Securely route messages and assets between Stellar and other chains, acting as the trust-minimized entry and exit point for cross-chain transactions.
- **[Gas Service Contracts](https://github.com/axelarnetwork/axelar-cgp-stellar/tree/main/contracts/gas-service):** Manage and collect fees required for cross-chain transactions, ensuring seamless user experience by abstracting gas payments.
- **[Relayers](https://github.com/axelarnetwork/axelar-cgp-stellar/tree/main/contracts/relayer):** Responsible for submitting transactions and facilitating message delivery across chains, including Stellar.
- **[Multisig Prover](https://github.com/axelarnetwork/axelar-cgp-stellar/tree/main/contracts/multisig-prover):** A CosmWasm-based component used for verifying cross-chain messages with a decentralized threshold signature scheme.
- **[Governance Contracts](https://github.com/axelarnetwork/axelar-cgp-stellar/tree/main/contracts/governance):** Allow for proposal creation, execution, and cancellation, enabling on-chain governance decisions that affect cross-chain interactions. (Stellar ITS will be supported at initial launch of the Soroban integration.)

---

## Request for Security Council Review

### Purpose

The purpose of this review is to ensure that the integration of Soroban with Axelar adheres to security and technical standards, enabling secure cross-chain interactions. The Security Council review will be conducted by Axelar’s internal security team and external auditors such as Ottersec and FYEO.

### Additional Information

- **Soroban GitHub Repository:** [https://github.com/stellar/soroban](https://github.com/stellar/soroban)
- **Soroban Documentation:** [https://soroban.stellar.org/docs](https://soroban.stellar.org/docs)
- **Soroban Whitepaper:** [https://soroban.stellar.org/whitepaper](https://soroban.stellar.org/whitepaper)
- **Stellar Audit Reports:** [https://stellar.org/security](https://stellar.org/security)
- **Axelar Integration of Soroban (FYEO):** [https://github.com/axelarnetwork/audits/blob/main/audits/2025-01%20FYEO_Soroban.pdf](https://github.com/axelarnetwork/audits/blob/main/audits/2025-01%20FYEO_Soroban.pdf)
- **Axelar Integration of Soroban (Ottersec):** *Pending publication*

### Additional Audit Links

- [Audit of Axelar Amplifier (2024-08 Code4rena)](https://code4rena.com/reports/2024-08-axelar-network)
- [Audit of Axelar Amplifier Gateway (2024-07Ackee)](https://github.com/axelarnetwork/audits/blob/main/audits/2024-07%20Ackee%20Blockchain.pdf)
- [Audit of Axelar Amplifier Gateway (2024-06 NCC)](https://github.com/axelarnetwork/audits/blob/main/audits/2024-06%20NCC.pdf)
- [Audit of Axelar Amplifier (Halborn)](https://github.com/axelarnetwork/audits/blob/main/audits/2024-05%20Halborn.pdf)
- [Audit of Axelar Amplifier Gateway (2024-04Ackee)](https://github.com/axelarnetwork/audits/blob/main/audits/2024-04%20Ackee%20Blockchain.pdf)
- [Audit of Axelar Amplifier (2024-03 NCC)](https://github.com/axelarnetwork/audits/2024-03%20NCC.pdf])

---

## Feedback and Questions

For questions or feedback about this integration, please reach out to the Interop Labs team:  

- **Technical Inquiry Form:** [https://www.axelar.network/delegation-guidelines](https://www.axelar.network/delegation-guidelines)
- **Discord:** [https://discord.com/invite/axelarnetwork](https://discord.com/invite/aRZ3Ra6f7D)
