# Chain Integration Proposal

## Overview

### Project Overview

- **Chain Name:** Solana
- **Project Description:** Solana is a high-performance Layer 1 blockchain designed for decentralized applications (dApps) and crypto-native use cases. It has unique Proof-of-History (PoH) consensus mechanism, which, combined with Proof-of-Stake (PoS), enables high throughput, low fees, and fast finality. Solana is optimized for scalability and performance, making it a preferred choice for DeFi, NFT marketplaces, high-frequency trading applications, and large-scale blockchain-based games.
- **Proposer:** Eiger
- **Contact Information:**
  - **Email:** hello@eiger.co

### Chain Overview

#### At-A-Glance

- **Justification for Solana:** Integrating Solana with the Axelar network will enable seamless interoperability, allowing Solana-based applications to connect with other blockchain ecosystems. This integration will facilitate cross-chain token transfers, smart contract interactions, and liquidity sharing, enhancing the utility and adoption of both Solana and Axelar.
- **Management Team Credentials:** Solana Labs is the primary development team behind Solana, co-founded by Anatoly Yakovenko and Raj Gokal. The team has extensive experience in distributed systems, cryptography, and networking, with backgrounds from leading technology firms such as Qualcomm, Google, and Intel.
- **Notable Use Cases:**
  * **DeFi:** Serum, Raydium, Orca (Decentralized Exchanges), Mango Markets (lending & perpetuals), Jupiter Aggregator (swap protocol).
  * **NFTs:** Magic Eden, Solanart, Metaplex (NFT marketplaces and infrastructure), SolSea (NFT launchpad).
  * **Gaming & Metaverse:** Star Atlas, Aurory, Genopets, DeFi Land (blockchain-based play-to-earn gaming).
  * **Payments & Stablecoins:** Solana Pay (fast and low-cost transactions for merchants), USDC and USDT on Solana.

#### Technology Overview

- **Protocol Overview:** Solana employs a unique Proof-of-History (PoH) mechanism that timestamps transactions before they are processed by the network’s validators. This allows Solana to achieve high throughput and low confirmation times. Combined with Proof-of-Stake (PoS), Solana ensures security and decentralization. The network's innovative consensus model reduces block propagation time, making it one of the fastest blockchains in the industry.
	- **Consensus Mechanism:** PoH plus PoS
	- **Smart Contract Platform:** Solana uses Rust and C-based smart contracts. Developers build on Solana using the Solana Program Library (SPL) and the Anchor framework, which provides a structured way to develop and deploy smart contracts efficiently. The ability to execute smart contracts in parallel is a defining feature of Solana’s architecture, allowing dApps to scale beyond what is possible on traditional blockchain networks.
- **Transaction Finality:** Transactions on Solana achieve finality in about 400 milliseconds, making it one of the fastest blockchains available. This rapid finality is critical for financial applications, gaming, and real-time dApps that require near-instant settlement.
- **Additional Notable Features:**
  - **Sealevel Parallel Processing:** Solana executes smart contracts in parallel, unlike traditional blockchains that use single-threaded execution, significantly improving network efficiency.
  - **Gulf Stream:** Optimized transaction propagation, reducing mempool size and enabling faster confirmations with lower latency.
  - **Turbine:** A block propagation protocol that increases network efficiency by breaking data into smaller packets, improving reliability.
  - **Validator Incentives:** Solana offers a robust staking and validator incentive program, ensuring network decentralization while rewarding participants.
  - **Wormhole Bridge:** Solana’s primary cross-chain bridge, connecting assets and smart contracts across multiple blockchain networks.

#### Security Considerations

- **Security Model:** Solana has undergone multiple security audits from firms such as Halborn, Kudelski Security and Neodyme. The network is designed with Byzantine Fault Tolerance (BFT) to prevent attacks, and a diverse set of approximately 1,000-1,200 active validators secure the network via a delegated Proof-of-Stake (dPoS) model. Solana employs a robust cryptographic structure and uses transaction signatures to prevent unauthorized access and tampering.
- **Previous Incidents & Mitigation:** While Solana has experienced occasional network congestion due to high transaction loads, the development team actively implements protocol upgrades and optimizations to enhance network resilience. Security improvements are continuously made to mitigate risks related to spam attacks, DDoS vulnerabilities, and network stability.
- **Bug Bounty Program & Security Monitoring:** Solana operates an active bug bounty program to encourage security researchers to identify and report vulnerabilities before they can be exploited. The network is monitored in real time using advanced threat detection systems to identify and mitigate potential attack vectors, ensuring a high level of security at all times.
- **Smart Contract Safety & Developer Security Best Practices:** The Solana Foundation provides guidelines and best practices for developers to write secure smart contracts, including secure coding patterns, recommended use of auditing services, and built-in security features in the Anchor framework. Developers are encouraged to undergo rigorous testing and formal verification processes before deploying dApps to the mainnet.
- **Network Resilience:** Solana has demonstrated significant improvements in network uptime, achieving over 99% uptime rate over the past year. This reliability ensures continuous operation for dApps, financial applications, and DeFi protocols, making it a dependable infrastructure for developers and enterprises.

### Axelar Integration Components

- **External Gateway Contract:** the External Gateway Contract will be implemented within Solana's native environment and optimized for the network's performance characteristics, allowing seamless cross-chain messaging and asset bridging.
- **Amplifier Contracts:** The Amplifier contracts will follow Axelar's established integration patterns with appropriate adaptations for Solana's programming model. These contracts will handle routing and validation of interchain messages to and from Solana, ensuring secure communication between networks.
- **ITS Contracts:** Interchain Token Service (ITS) contracts will be adapted to support SPL token transfers, enabling cross-chain assets to be issued and redeemed on Solana with minimal friction.
- **Governance Contract:** The governance module allows decisions taken on the Axelar network to be propagated and executed on the different integrated chains, giving a chance (by timelock) to each chain maintainer to prepare for its execution. So the governance module acts as an "approved proposal's forwarder" which is connected to the Axelar governance infrastructure via GMP messages.

## Request for the Amplifier Advisory Committee Review

### Purpose

The purpose of this review is to ensure that the integration of Solana with the Axelar network adheres to all security and technical standards, ensuring a secure and efficient connection.

### Additional Information

- **GitHub Repository:** https://github.com/anza-xyz/agave
- **Developer Documentation:** https://solana.com/docs
- **Whitepaper:** https://solana.com/solana-whitepaper.pdf
- **Independent Audit Reports:** https://github.com/anza-xyz/security-audits
- **Independent Audit Reports of Axelar Integration of Solana:**
  - [FYEO v1.0](https://github.com/fyeo-io/public-audit-reports/blob/main/Code%20Audit%20Reports/2025/Axelar/Axelar%20Foundation%20-%20Security%20Code%20Review%20of%20Axelar%20-%20Solana%20Integration%20v1.0.pdf)

## Community Involvement

### Discussion Forum

Community members are encouraged to participate in the discussion and provide feedback on this proposal through the Axelar community forum.

### Voting

Following the Amplifier Advisory Committee's review, a community vote will be held to determine the approval of Solana's integration with the Axelar network.

### Feedback and Questions

For any questions or feedback regarding this proposal, please contact Daren Tuzi at hello@eiger.co.
