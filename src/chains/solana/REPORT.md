# Report on Solana Blockchain

## Project Overview
- **Chain Name**: Solana
- **Proposal Reviewed**: [Solana Integration Proposal](PROPOSAL.md)

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

### 1.2 Evaluation Approach

### 1.3 Assessment Framework

### 1.4 Assessment Criteria

---

## Section 2: Network and Protocol Integrity
### 2.1 Network Architecture

### 2.2 Governance and Compliance

---

## Section 3: Security and Risks
### 3.1 Smart Contract Security and Vulnerabilities

### 3.2 Risks and Concerns

---

## Section 4: Axelar Integration Components
### 4.1 Code Quality and Transparency

Eiger team was responsible for developing the Solana external contracts (programs). Eiger team was also responsible for developing the Solana Amplifier components as well as the Relayer.

[Solana Axelar](https://github.com/eigerco/solana-axelar/tree/main/solana/programs) repository contains the Axelar Cross-chain Gateway Protocol implementation
developed in Rust programming language for the Solana blockchain. The programs are "native Rust" programs and do not use the Anchor framework.

The Solana Amplifier ampd implementation was merged to the [Axelar Amplifier](https://github.com/axelarnetwork/axelar-amplifier/pull/744) repository, while the Solana Amplifier Multisig & Prover contracts logic are in the [eiger Axelar Amplifier](https://github.com/eigerco/axelar-amplifier/tree/add-multisig-prover-sol-logic) repository. 
[Axelar Solana Relayer](https://github.com/eigerco/axelar-solana-relayer) repository contains the implementation of the relayer. 

The codebase for all 3 components (Solana Axelar contracts, Solana Amplifier and Axelar Solana Relayer) underwent the following audits:
- FYEO [03/2025](https://github.com/fyeo-io/public-audit-reports/blob/main/Code%20Audit%20Reports/2025/Axelar/Axelar%20Foundation%20-%20Security%20Code%20Review%20of%20Axelar%20-%20Solana%20Integration%20v1.0.pdf)

Summary of findings from the audits (Reported-Fixed-Acknowledged):

| Company        | Critical | High  | Medium | Low   | Info    |
|----------------|----------|-------|--------|-------|---------|
| **FYEO 3/25**  |          | 1-1-0 | 4-4-0  | 2-2-0 | 13-13-6 |

[Buidly](https://www.buidly.com) performed a cross-check of audit reports and confirmed that all reported findings were remediated except 6 informational findings from the FYEO 03/2025 audit

### 4.2 Understanding of Deployment and Maintenance Plans

Deployment scripts for Solana Axelar components are provided in the [Solana Axelar Scripts](https://github.com/eigerco/solana-axelar-scripts) repository, but the process is not well documented. 

### 4.3 Mitigation of Potential Risks

Solana and Axelar confirm that the system includes proper logging and mechanisms to effectively handle unusual situations in the network.

The current Relayer implementation uses a monolithic approach which can not be easily scaled.
This issue is acknowledged by the Eiger team and fixes are already underway. Worst case scenario, cross chain calls to/from Solana can get stuck for a limited period of time, but they can always be manually executed if needed, ensuring no user funds are at risk.

Another issue with the current Relayer is the lack of support for custom programs that implement the Axelar Executable Interface to be called by the Relayer.
The current Relayer can only execute calls to Solana ITS. If other programs want to utilize Solana GMP, at the moment they will have to provide their own Relayer service.

---

## Conclusion

---

## Next Steps

---

## Committee Members
- **Axelar**: Liana Spano, Coordinator
- **Node.Monster**: Eyal Alsheich, Contributor
- **Common Prefix**: Nikolaos Kamarinakis, Contributor
- **Ackee**: Stepan Sonsky, Contributor
- **Buidly**: Rares Serban, Contributor
