# Chain Integration Proposal


Integrating Soroban with the Axelar network will unlock new capabilities for decentralized applications (dApps) by enabling seamless cross-chain interoperability, enhanced scalability, and robust security. This partnership aims to leverage Soroban’s efficient WASM-based smart contract platform and Stellar’s infrastructure to provide a foundation for innovative use cases in decentralized finance (DeFi), tokenized assets, and cross-border payments. Key milestones include developing gateway contracts, ensuring compatibility with Axelar’s network, and securing cross-chain communications.

---

## Overview

### Project Overview

**Chain Name:** Soroban

**Project Description:**  
Soroban is a smart contract platform built on the Stellar blockchain, designed to power decentralized applications (dApps) with a focus on simplicity, performance, and trustworthiness. Leveraging Stellar’s fast and efficient transaction protocol, Soroban introduces robust features for developers to build and deploy scalable, secure, and low-latency applications. Its integration with Stellar’s existing infrastructure ensures seamless functionality for financial and enterprise use cases.

**Proposer:** Stellar Development Foundation (SDF)

**Contact Information:**
- **Email:** [contact@stellar.org](mailto:contact@stellar.org)
- **Slack:** In Axelar’s Integrator Slack channel tag [TBD]
- **Discord:** [https://discord.com/invite/stellar](https://discord.com/invite/stellar)
- **Website:** [https://stellar.org](https://stellar.org)

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

- **Stellar Asset Bridge:** [Enabling seamless tokenized asset transfers](https://www.stellar.org) between Stellar and other blockchain ecosystems.
- **Pendulum:** [A blockchain solution](https://pendulumchain.org) enhancing DeFi functionality with stablecoin liquidity pools and cross-border transactions.
- **Solar Wallet:** [An intuitive wallet](https://solarwallet.io) for accessing dApps, managing assets, and seamless Soroban integration.
- **Lightnet Group:** [A financial infrastructure](https://lightnet.io) for remittances and cross-border payments.

---

## Technology Overview

### Protocol Overview

Soroban is a WebAssembly (WASM)-based smart contract platform leveraging Stellar’s highly efficient consensus algorithm, the Stellar Consensus Protocol (SCP). It supports up to **5,000 transactions per second (TPS)** under optimal conditions.

### Key Features:
- **Smart Contracts:** Modular, composable, and built in a WASM execution environment.
- **Transaction Finality:** Near-instant, ensuring real-time performance for financial systems.
- **Developer Tools:** Includes the Stellar Laboratory, Horizon API, and Soroban CLI for seamless dApp development.
- **Cross-Chain Interoperability:** Facilitating multi-network DeFi, tokenized asset transfers, and payments.

---

## Axelar Integration Components

**Amplifier and External Contracts**  
Integrating Soroban with Axelar includes the following components:

- **Gateway Contracts:** Secure routing of messages and assets.
- **Relayers:** Efficient cross-chain message delivery.
- **Gas Service Contracts:** Handling fees for cross-chain transactions.
- **Security Modules:** Ensuring integrity and safety of data.

Axelar integration components are available here:  
[https://github.com/axelarnetwork/axelar-cgp-stellar](https://github.com/axelarnetwork/axelar-cgp-stellar)

---

## Request for Security Council Review

### Purpose

The purpose of this review is to ensure that the integration of Soroban with Axelar adheres to security and technical standards, enabling secure cross-chain interactions.

### Additional Information

- **GitHub Repository:** [https://github.com/stellar/soroban](https://github.com/stellar/soroban)
- **Documentation:** [https://soroban.stellar.org/docs](https://soroban.stellar.org/docs)
- **Whitepaper:** [https://soroban.stellar.org/whitepaper](https://soroban.stellar.org/whitepaper)
- **Stellar Audit Reports:** [https://stellar.org/security](https://stellar.org/security)
- **Soroban FYEO Audit Report:** [https://github.com/axelarnetwork/audits/blob/main/audits/2025-01%20FYEO_Soroban.pdf](https://github.com/axelarnetwork/audits/blob/main/audits/2025-01%20FYEO_Soroban.pdf)
- There is an ongoing audit conducted by the Ottersec team | Feb 24 - Mar 7 2025

---

## Feedback and Questions

For questions or feedback, please contact the Stellar Development Foundation:  
- **Email:** [contact@stellar.org](mailto:contact@stellar.org)  
- **Discord:** [https://discord.com/invite/stellar](https://discord.com/invite/stellar)
