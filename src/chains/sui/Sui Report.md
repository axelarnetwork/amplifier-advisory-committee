# Report on Sui Blockchain

## Project Overview
- **Chain Name**: Sui
- **Proposal Reviewed**: [Insert Proposal Details]
- **Sui Integration Proposal**: Overview of objectives for integrating Sui with Axelar Network.
- **Points of Contact**: [Insert relevant channels and individuals for communication.]

---

## Section 1: Assessment Methodology

### 1.1 Integration Overview

Sui’s integration with Axelar aims to enable seamless cross-chain transactions and interoperability by leveraging Axelar's General Message Passing (GMP) and security infrastructure. This integration provides Sui developers access to broader liquidity pools, decentralized applications (dApps), and enhanced functionality across interconnected blockchain networks. Sui’s unique Move-based programming model and high throughput architecture make it a promising candidate for cross-chain innovation.

### 1.2 Evaluation Approach

The Committee’s assessment methodology included the following:

- **Research and Documentation Review**: A detailed review of technical documentation, Sui’s GitHub repositories, whitepapers, and Sui Improvement Proposals (SIPs) to understand the network’s capabilities and integration requirements.
- **Security Audits and Testing**: Examination of Sui's codebase, previously conducted audits, and tests for vulnerabilities. This included reviewing best practices for Move-based smart contracts.
- **Collaboration with the Sui Team**: Ongoing discussions with the Sui development team to understand their infrastructure, upgrade plans, incident response protocols, and readiness for cross-chain integrations.

### 1.3 Assessment Framework

The assessment framework focused on the following key areas:

- **Protocol Integrity**: Evaluating Sui’s consensus mechanism (Narwhal and Tusk), validator decentralization, and the scalability of its DAG-based architecture.
- **Security Risks**: Identifying vulnerabilities within Sui’s Move VM, bridge components, and network infrastructure.
- **Operational Risks**: Assessing challenges developers might face when integrating with Sui, such as stability, untested features, or constraints in the Move language.
- **Compliance and Governance Risks**: Reviewing Sui’s governance model, community involvement, and regulatory considerations.
- **Code Quality and Transparency**: Analysis of the codebase, audit results, and adherence to development best practices.
- **Integration Plan**: Reviewing deployment and maintenance strategies for the Axelar-Sui integration, including monitoring systems and threat detection mechanisms.

### 1.4 Assessment Criteria

The desirable properties related to Sui’s architecture and its integration with Axelar included:

- **Security**: How Sui’s consensus and Move-based contracts safeguard against exploits.
- **Scalability and Performance**: Sui’s ability to handle high transaction throughput with low latency.
- **Decentralization**: The extent of validator distribution and its impact on the network’s security.
- **Governance**: The mechanisms for protocol upgrades, decision-making, and dispute resolution.
- **Fault Tolerance**: Sui’s ability to recover from network halts or failures without impacting system integrity.
- **Transparency**: Open-source availability of the codebase, audit reports, and developer documentation.


---

## Section 2: Network and Protocol Integrity [Common Prefix, Eiger, NodeMonster]
### 2.1 Network Architecture
Sui is a Layer 1 blockchain that supports scalable, high-performance decentralized applications. Unlike traditional blockchain architectures, Sui employs an object-based accounting model and a modified Delegated Proof-of-Stake (DPoS) consensus mechanism. Transactions are categorized into "simple" and "complex," with simple transactions bypassing traditional consensus steps, enhancing performance. Complex transactions leverage Narwhal for data availability and Bullshark for ordering, ensuring efficiency and resilience.

Key Architectural Features:
- **Object-Based Accounting Model:** Combines features of UTXO and account-based models to enable granular state management, making it particularly suitable for complex dApps.
- **Consensus:** The Sui Network uses a Narwhal and Tusk consensus mechanism, which combines DAG-based mempool design (Narwhal) with a Byzantine Fault Tolerant (BFT) consensus algorithm (Tusk). Validators individually validate transactions and generate certificates of finality, optimizing for throughput and latency.
- **Sponsored Transactions:** Unique mechanism allowing third parties to pay transaction fees, promoting accessibility.
All computation fees and reward subsidies earned by a validator, minus its chosen commission rate, are shared with delegators. The validator receives the tokens charged as commission and a percentage of the rewards after removing the commission. This percentage equals the ratio of self-staked SUI against the total SUI staked to the validator. The second part of a validator’s rewards is sourced from the Storage Fund, which is funded by the storage fees involved in each transaction. Today’s validators process transactions occurring today and create data. If new validators join tomorrow, they will have to store data they were not rewarded to create. Storage fees included in each transaction fee are sent to the fund, which is used to reward tomorrow's validators with the storage fees paid today. Of note, the tokens held in the Storage Fund accrue rewards from its proportionate amount of the total staked supply.

Sui’s staking mechanism requires validators to hold a minimum of 30 million SUI (high barrier relative to the market). Validators share computational rewards with delegators, fostering ecosystem-wide engagement. Sui currently operates with approx. 108 active validators, ensuring robust security and incentivizing network participation. The total number of staked assets on Sui is approximately 7.8B SUI (78.33% of total assets), The top 10 validators (inc. Mysten Labs) are operating approx 22% of the total staked assets.


### 2.2 Governance and Compliance
Sui’s governance framework is currently centralized, with decisions predominantly directed by the Sui Foundation and Mysten Labs. The network lacks an active decentralized governance model as of December 2024. However, plans to integrate governance through staked SUI tokens have been proposed, where voting power would correspond to combined self-staked and delegated tokens, capped at 10% per validator to prevent centralization.
Key Governance Insights:
- Community proposals follow the SIP (Sui Improvement Proposal) process. While the community can signal support, the project team makes the final decisions.
- Regulatory considerations are actively managed by Mysten Labs, which maintains compliance with U.S. legal frameworks.
- The absence of a robust, decentralized governance mechanism may limit community-driven innovation but ensures streamlined decision-making during the network’s early stages.
Sui was founded in 2021 by Evan Cheng, Adeniyi Abiodun, Sam Blackshear, George Danezis, and Kostas Chalkias to continue the work performed while employed by Meta. In June 2019, Facebook, which later rebranded to Meta, announced its plans to build a permissioned blockchain and a digital wallet that would underlie a global payment network. Meta spearheaded an independent consortium called the Diem Association (originally the Libra Association) that was responsible for building the blockchain. Meta’s subsidiary Novi Finance (originally Calibra) was responsible for developing the digital wallet. Neither product was successful. The Diem Association shut down due to regulatory hurdles and sold all its assets in January 2022. Meta ended the Novi project later that year due to calls from the United States Senate. Two separate blockchains emerged from the initial Diem and Novi research: Aptos and Sui. Mysten Labs, Inc., one of the centralized entities supporting Sui, was formed to build something new from research conducted during the Diem Association’s life.


---

## Section 3: Security and Risks [Common Prefix, Eiger, NodeMonster]
### 3.1 Smart Contract Security and Vulnerabilities
Sui’s smart contracts are written in Sui Move, a Rust-based programming language derived from the Move language developed at Meta. This language offers enhanced safety features, including:
- **Type Safety:** Reduces vulnerabilities by ensuring strict data type adherence.
- **Resource-Oriented Programming:** Prevents double-spending and unauthorized state changes by enforcing ownership and access rules.
- **Formal Verification:** Facilitates rigorous testing and validation of smart contracts to minimize bugs.
Testing and debugging mechanisms for Sui’s smart contracts include modular code organization, ownership rules, and structured data flow that allow developers to easily test and debug contracts. Developers are encouraged to employ local testing environments, implement explicit error-handling mechanisms, and regularly verify contracts using Move Prover. Recent updates to development tools also enhance debugging processes and streamline integration with Sui's broader ecosystem.

However, historical incidents highlight the need for continuous vigilance:
- **November 17, 2023:** An unspecified vulnerability was discovered and promptly patched across the mainnet, testnet, and devnet. While the issue did not escalate, it underscores the importance of proactive community engagement in identifying flaws.
- **September 3, 2023:** A denial-of-service (DoS) vulnerability in Sui’s P2P protocol was reported by Beosin Alert. The vulnerability, which could deplete memory and crash nodes, was resolved in version 1.6.3.
- **May 16, 2023:** A critical "billion-dollar bug" was identified during an audit by Xellic. The issue, which had the potential to cause significant disruptions, was patched effectively.
- **July 6, 2024:**  Public RPC nodes were crashed when attempting to submit a transaction.
- **November 12, 2024:** Sui testnet validators don't accept new user transactions. The issue has been resolved.
- **November 21, 2024 Mainnet Outage:** A major outage occurred due to a critical bug in the consensus mechanism, an unexpected issue in the transaction validation pipeline caused intermittent disruptions, <ins>and led to a halt in transaction processing for over 24 hours.</ins>  The problem was [traced to an edge case](https://blog.sui.io/sui-mainnet-outage-resolution/) in transaction ordering and was resolved in version 1.8.2 of the protocol, but it exposed vulnerabilities in handling high-throughput scenarios. The incident also highlighted the need for improved disaster recovery mechanisms and validator coordination.
SUI has engaged with [third-party auditors](https://sui.io/security), including Zellic, Halborn,Common Prefix, OtterSec, and others, which conducted multiple audits focusing on core components. Its worth noting that no further audits were made from April 2023.

### 3.2 Risks and Concerns
Recent incidents have also highlighted systemic risks. The November 2024 mainnet outage, caused by a critical bug in the consensus mechanism, disrupted transaction processing for over 24 hours. This incident exposed vulnerabilities in transaction ordering and underscored the need for robust disaster recovery mechanisms and better validator coordination. In addition, the lack of audits since April 2023 leaves the network vulnerable to undiscovered security flaws.

Additional notable considerations for the Axelar community include the nuances of Sui's consensus mechanism and upgrade processes. The Narwhal and Tusk consensus mechanism used by Sui integrates a Directed Acyclic Graph (DAG)-based mempool with a Byzantine Fault Tolerant (BFT) protocol. This architecture is inspired by cutting-edge research but has seen limited external audits. While the foundational papers validating these approaches are rigorous, the specific implementations in Sui may include optimizations that require further review and validation.

Sui has introduced significant upgrades, such as version 1.9.0, aimed at improving performance and enhancing fault tolerance. However, these updates often bring added complexity, which, if not thoroughly tested, could introduce new vulnerabilities. Notably, recent findings by security firms have identified edge cases in Sui's transaction validation pipeline that require further mitigation efforts.
Finally, while the Narwhal and Tusk mechanisms provide high throughput and resilience, their reliance on validator coordination in high-load scenarios remains a critical area of focus. Ensuring decentralized participation and seamless fallback mechanisms will be essential to maintaining trust and security across the network.

Mitigation strategies include expanding the bug bounty program to incentivize community-driven vulnerability identification, enhancing decentralization by encouraging broader validator participation, and conducting periodic audits to ensure security and protocol integrity. Proactive measures such as threat monitoring, disaster recovery planning, and regular protocol upgrades aim to address these risks and foster long-term resilience.

Despite its challenges, Sui’s commitment to innovation and proactive security measures positions it as a strong player in the blockchain ecosystem. By addressing these concerns and continuing to prioritize security, Sui can maintain trust and support its growing user base.

---

## Section 4: Axelar Integration Components [Ackee]
### 4.1 Code Quality and Transparency
- Audit summaries and findings relevant to the Sui integration.

### 4.2 Understanding of Deployment and Maintenance Plans
- Plans for secure deployment and ongoing maintenance of Sui-related components.

### 4.3 Mitigation of Potential Risks
- Risk management strategies specific to the Sui integration.

---

## Conclusion [Common Prefix, Eiger, NodeMonster, Ackee]
- Summary of findings and recommendations for the integration.

---

## Next Steps [Common Prefix, Eiger, NodeMonster, Ackee]
- Outline of actions required for completion.

---

## Committee Members
- List of team members and their roles in the assessment.
- ### Committee Members
- **Axelar**:
- **Node.Monster**: 
- **Common Prefix**: 
- **Ackee**: 
