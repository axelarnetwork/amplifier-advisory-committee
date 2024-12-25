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
- Assessment of Sui's architecture, consensus mechanism, and staking requirements.
- Assessment of the Sui team, governance structure, and decentralization status.

### 2.2 Governance and Compliance
- Assessment of Sui's governance framework, key decision-making processes, and regulatory considerations.

---

## Section 3: Security and Risks [Common Prefix, Eiger, NodeMonster]
### 3.1 Smart Contract Security and Vulnerabilities
- Assessment of Sui's programming language, smart contract features, and security measures.

### 3.2 Risks and Concerns
- Key risks for developers and users in cross-chain interactions, mitigation strategies.

---

## Section 4: Axelar Integration Components [Ackee]
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
