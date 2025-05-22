# Chain Integration Proposal

## Overview

### Project Overview

- **Chain Name:** Plume
- **Project Description:** Plume is a modular Layer 2 (L2) blockchain specifically designed for real-world assets (RWAs). It features full EVM compatibility and integrates asset tokenization and compliance providers directly into the chain. Plume aims to bridge traditional finance and Web3 by simplifying the process of tokenizing, trading, and managing real-world assets through a composable ecosystem focused on RWAfi (Real World Asset finance). The platform enables users to interact with tokenized assets in crypto-native ways, including yield farming, lending, borrowing, and trading across multiple chains.
- **Proposer:** Plume Network
- **Contact Information:**
  - **Email:** support@plume.org
  - **Website:** https://plumenetwork.xyz/

### Chain Overview

#### At-A-Glance

- **Justification for Plume EVM:** Integrating Plume with the Axelar network will expand cross-chain interoperability for real-world assets (RWAs), enabling projects built on Plume's Layer 2 ecosystem to seamlessly connect with other blockchain networks. This integration will allow for the efficient movement of tokenized real-world assets across chains, increasing liquidity and utility while maintaining compliance requirements that are essential for RWA projects.

- **Management Team Credentials:** Plume Network was founded by a team with extensive industry experience: Chris Yin (CEO, former VP of Product at Rainforest and Principal at Scale Venture Partners), Eugene Y.Q. Shen (CTO, previously a Senior Software Engineer at dYdX and Robinhood Crypto), and Teddy Pornprinya (CBO, formerly at Binance, Swim Protocol, and Coinbase Ventures). The broader team includes professionals from leading companies including LayerZero, Galaxy Digital, JP Morgan, and other prominent Web3 and traditional finance organizations.

- **Notable Use Cases:**
  * **Tokenized Financial Assets:** Integration with platforms like [DigiFT](https://www.digift.sg/index) (regulated exchange for on-chain real-world assets) and [MatrixDock](https://www.matrixdock.com/) (tokenized U.S. T-Bills).
  * **Private Credit & Lending:** Protocols such as Credible (lending secured by RWAs like private credit and trade receivables) and Kasu (risk-optimized private credit yields).
  * **Real Estate & Physical Assets:** Projects like [LandX](https://app.landx.io/) (platform for investing in farmland and agricultural commodities) and Mattereum (tokenization of physical assets with legal protections).
  * **Infrastructure & Alternative Assets:** Solutions for tokenizing renewable energy projects, luxury goods, collectibles, and other alternative asset classes.
  * **[Nest Protocol](https://www.nestprotocol.org/):** A flagship staking platform within the Plume ecosystem, Nest offers [institutional-grade yields]( https://plumenetwork.xyz/blog/rwaxyz-analytics) backed by tokenized assets such as U.S. Treasuries, private credit, and alternative investments. Vaults include assets from BlackRock’s BUIDL, Hamilton Lane, and Ondo USDY.
  * **RWA Inc.:** A regulated tokenization platform based in the UAE, RWA Inc. has [partnered with Plume](https://medium.com/@RWA_Inc_/rwa-inc-partners-with-the-plume-network-to-elevate-tokenization-sector-059d638ec164) to streamline asset issuance and liquidity provisioning.
  * **[Moca Network](https://www.animocabrands.com/moca-network-plume-partner-to-bring-privacy-preserved-institutional-grade-rwa-yield-to-users) (Animoca Brands) – Digital ident:** Moca integrates AIR Kit digital identity with Plume, allowing 700M+ users access to institutional-grade RWA yields.
  * **[RWA.xyz](https://plumenetwork.xyz/blog/rwaxyz-analytics) Integration:** Plume has integrated with RWA.xyz, a leading analytics platform for tokenized real-world assets. This partnership allows for real-time data accessibility and transparency for investors and issuers within the Plume ecosystem.
  * **[Polytrade and Brickken](https://cryptopotato.com/plume-network-announces-key-projects-to-reinvent-real-world-asset-tokenization):** These RWA-focused projects are part of Plume’s ecosystem, utilizing its infrastructure to tokenize assets and integrate with DeFi applications.

#### Technology Overview

- **Protocol Overview:** Plume Network is a modular Layer 2 blockchain specifically designed for real-world assets (RWAs). It employs an innovative architecture optimized for tokenizing, distributing, and creating crypto-native use cases for real-world assets within a composable DeFi ecosystem.
  - **Consensus Mechanism:** Plume is built on Arbitrum technology with custom modifications to enhance RWA functionality. The platform operates as a permissionless EVM-compatible chain that leverages a consensus system with cryptoeconomic incentives and slashing mechanisms to ensure the integrity and security of tokenized assets.
  - **Smart Contract Platform:** Plume offers full Ethereum Virtual Machine (EVM) compatibility, enabling seamless deployment of Solidity smart contracts and integration with existing Ethereum developer tools. This compatibility allows developers to build RWA applications using familiar frameworks while accessing specialized features optimized for real-world asset management and compliance.

- **Transaction Finality:** Plume follows a two-tiered finality model typical of Arbitrum-based Layer 2 solutions. Transactions receive rapid soft confirmation on the Plume chain, while achieving absolute finality when batched and settled on Ethereum. This approach balances practical usability with the security guarantees required for RWA transactions, while offering reduced gas costs compared to direct Ethereum mainnet operations.

- **Additional Notable Features:**
  - **Arc Tokenization Engine:** A comprehensive framework for efficiently tokenizing real-world assets with integrated compliance workflows, reducing barriers for asset issuers and providing a streamlined path to bring assets onchain.
  - **Nexus Data Highway:** A specialized data integration layer that bridges real-world information with blockchain applications through partnerships with leading oracle providers, enabling accurate on-chain representations of off-chain data.
  - **Smart Wallets:** Built-in wallet technology with embedded custody and compliance features, allowing RWA holders to leverage their assets within DeFi applications for staking, collateralization, and yield generation.
  - **[SkyLink](https://www.theblockbeats.info/en/news/56710):** Cross-chain connectivity solution that enables RWA yields to be distributed across multiple blockchain networks, expanding accessibility and liquidity for tokenized assets.
- **Regulatory Compliance Framework:** Built-in support for tokenization standards that enable compliance with securities regulations, including features for identity verification, transfer restrictions, and asset management controls that meet the requirements of regulated RWA markets.

#### Security Considerations

- **Architectural Safeguards:** Plume's security infrastructure builds on established Layer 2 technology while incorporating specialized safeguards for RWA transactions. The network employs economic incentives with validator staking and slashing mechanisms, creating accountability for participants who validate and process transactions.

- **Smart Contract Protection:** The platform's smart contracts leverage standard EVM security patterns combined with additional compliance measures essential for tokenized real-world assets. These include transaction monitoring systems, sanctions screening protocols, and built-in regulatory compliance tools that protect both users and asset issuers.

- **Regulatory Alignment:** As the RWA space continues to evolve, Plume's security approach focuses on maintaining compliance with relevant regulations while providing the transparency and verifiability expected in blockchain systems. This balanced approach helps ensure that tokenized assets remain secure throughout their lifecycle on the network.

- **External Verification:** For third-party verification, Plume works with security partners to audit critical components of its infrastructure, with details available in their [security documentation](https://docs.plume.org/plume/plume-security/audits-and-security). The platform also implements continuous security monitoring to identify and address potential threats in real-time.

- Halborn Audit (January 2025): Assessed Plume's Airdrop Distributor and Staking contracts. Identified 10 findings (2 informational, 8 low severity), all of which were addressed by Plume.
Report: https://www.halborn.com/audits/plume/plume-contracts

- CertiK Skynet: Ongoing security assessments are available on [CertiK's platform](https://skynet.certik.com/projects/plume-network).

- Veritas Protocol Audit: The AI-driven audit report can be reviewed [here](https://www.veritasprotocol.com/audits/plume-audit).

### Axelar Integration Components

- **External Gateway Contract:** Because Plume is fully EVM-compatible, the Axelar integration for the external gateway contracts will be those found here: https://github.com/axelarnetwork/axelar-gmp-sdk-solidity/blob/main/contracts/gateway/INTEGRATION.md. These contracts were developed by the Interop Labs team and fully [audited](https://github.com/axelarnetwork/audits).
- **Amplifier Contracts:** Similarly, the Amplifier contracts (Gateway, Voting Verifier, Multisig Prover) on the Axelar Network will be those developed by the Interop Labs team, which can be found here: https://github.com/axelarnetwork/axelar-amplifier/tree/main/contracts
- **ITS Contract:** The Interchain Token Service contracts will be deployed without modification, allowing seamless token transfers between Plume and other chains in the Axelar ecosystem: https://github.com/axelarnetwork/interchain-token-service

### Current Status

- **Testnet launched:** Plume has launched its public testnet with over 3.75 million active wallets and 270+ million transactions.
- **Mainnet launch:** Scheduled for Q3 2025.
- **Audit reports:** Halborn and Veritas Protocol audits completed. No high or critical issues found; low-severity findings have been resolved.  
- **Integration readiness:** Plume is fully EVM-compatible. GMP messaging is already under test, and integration with Axelar’s ITS and Amplifier contracts is expected to proceed without modification.

## Request for the Amplifier Advisory Committee Review

### Purpose

The purpose of this review is to ensure that the integration of Plume EVM with the Axelar network adheres to all security and technical standards, ensuring a secure and efficient connection.

### Additional Information

- **GitHub Repository:** https://github.com/plumenetwork
- **Developer Documentation:** https://docs.plumenetwork.org/plume
- **Plume Manifesto:** https://plume.org/blog/manifesto
- **Plume Explorer:** Real-time network activity and smart contract verification can be accessed via the [Plume Explorer](https://explorer.plume.org/).

## Community Involvement

### Discussion Forum

Community members are encouraged to participate in the discussion and provide feedback on this proposal through the Axelar community forum.

### Voting

Following the Amplifier Advisory Committee's review, a community vote will be held to determine the approval of Plume's integration with the Axelar network.

### Feedback and Questions

For any questions or feedback regarding this proposal, please contact the Plume Development Team at support@plume.org.
