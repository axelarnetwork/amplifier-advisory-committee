# Report on Sui Blockchain

## Project Overview
- **Chain Name**: Sui
- **Proposal Reviewed**: [Sui Integration Proposal](Sui%20Integration%20Proposal.md)

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

## Section 2: Network and Protocol Integrity 
### 2.1 Network Architecture
Sui is a Layer 1 blockchain that supports scalable, high-performance decentralized applications. Unlike traditional blockchain architectures, Sui employs an object-based accounting model and a modified Delegated Proof-of-Stake (DPoS) consensus mechanism. Transactions are categorized into "simple" and "complex," with simple transactions bypassing traditional consensus steps, enhancing performance. Complex transactions leverage Narwhal for data availability and Bullshark for ordering, ensuring efficiency and resilience.

Key Architectural Features:
- **Object-Based Accounting Model:** Combines features of UTXO and account-based models to enable granular state management, making it particularly suitable for complex dApps.
- **Consensus:** The Sui Network relies on the Mysticeti DAG-based consensus algorithm, which improves upon Narwhal-Tusk. Mysticeti has been formalized in the form of [an academic research paper](https://arxiv.org/pdf/2310.14821) published on arXiv, with rigorous proofs of safety and liveness. Notably, Mysticeti achieves the optimal consensus latency of three network round trips, resulting in a ~4x latency reduction to Sui mainnet. Rather than relying on a single leader to propose a block, Mysticeti supports multiple validators proposing blocks in parallel, making use of the full bandwidth of the network. Moreover, validators who attempt to censor valid transactions are accountable.
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

## Section 3: Security and Risks 
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

## Section 4: Axelar Integration Components 
### 4.1 Code Quality and Transparency
Axelar was responsible for developing the Sui external contracts. [Axelar GCP Sui](https://github.com/axelarnetwork/axelar-cgp-sui) is Axelar Cross-chain Gateway Protocol implementation developed in [Move](https://sui.io/move) programming language. The codebase was audited by Ottersec [6/24](https://github.com/axelarnetwork/audits/blob/main/audits/2024-06%20Ottersec.pdf) and [11/24](https://github.com/axelarnetwork/audits/blob/main/audits/2024-11%20Ottersec%20-%20Sui.pdf). [Ackee](https://ackee.xyz/) performed a cross-check of audit reports and confirmed that all reported findings were remediated except one informational finding (OS-AXN-SUG-00) from the 11/24 audit.

Summary of findings from Sui CGP audits (Reported-Fixed-Acknowledged):

| Company            | Critical | High  | Medium | Low   | Info  |
|--------------------|----------|-------|--------|-------|-------|
| **Ottersec 6/24**  |          |       | 1-1-0  | 3-3-0 | 3-3-0 |
| **Ottersec 11/24** |          | 1-1-0 | 1-1-0  | 4-4-0 | 4-3-1 |

No audit report for [Sui Amplifier](https://github.com/axelarnetwork/axelar-amplifier/tree/main/ampd/src/sui) code was provided.

### 4.2 Understanding of Deployment and Maintenance Plans
Deployment scripts for Sui Axelar components are provided, and the process is well documented in the [Axelar repository](https://github.com/axelarnetwork/axelar-contract-deployments/tree/main/sui#sui-deployment-scripts). The code is well-structured, and [Ackee](https://ackee.xyz/) did not identify any best practices violations in the development scripts.

### 4.3 Mitigation of Potential Risks
Sui and Axelar confirm that the system includes proper logging and mechanisms to resolve unusual situations in the network to avoid further damage to the network and users' funds. Sui performs continuous security monitoring and a proactive approach to vulnerability management.

---

## Conclusion 
The Sui integration with Axelar Network presents a significant opportunity to expand interoperability and enable seamless cross-chain transactions for developers. The evaluation highlights Sui’s strengths, including its innovative Move-based programming model, object-based accounting system, and high transaction throughput enabled by Narwhal and Tusk consensus. Axelar’s integration components demonstrate strong adherence to best practices, with thorough audits and well-documented deployment plans.

Despite these strengths, the assessment identified critical areas for improvement. Sui’s centralized governance, recent mainnet outage, and limited audits since 2023 raise concerns about network resilience and community engagement. Historical vulnerabilities, including denial-of-service (DoS) and transaction validation bugs, emphasize the need for robust security mechanisms. The complexity of Sui’s architecture and reliance on validator coordination in high-load scenarios necessitate enhanced fault tolerance and operational readiness.

The integration offers Sui developers access to broader liquidity pools and interoperable dApps, fostering innovation across the ecosystem. To realize these benefits, addressing security risks, decentralization challenges, and governance gaps will be critical. By implementing proactive measures such as expanded audits, improved disaster recovery plans, and decentralized decision-making, Sui can solidify its position as a secure and scalable blockchain within the Axelar Network ecosystem.

---

## Next Steps 
To ensure the successful integration of Sui with Axelar Network and long-term operational resilience, the following actions are recommended:

Focus on maintaining integration stability and performance through continuous monitoring and proactive issue detection. Node Monster will spin up a globally distributed Sui validator to enhance network redundancy and decentralization, verifying the final implementation status with the Axelar Foundation. Additionally, the development team should design and implement a proactive outage management plan, including on-chain smart contract protections, to address potential network disruptions on Sui.

---

## Committee Members
- **Axelar**: Liana Spano, Coordinator
- **Node.Monster**: Eyal Alsheich, Contributor
- **Common Prefix**: Nikolaos Kamarinakis, Contributor
- **Ackee**: Stepan Sonsky, Contributor
- **Eiger**: Marcin, Contributor
