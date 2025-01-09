# Axelar Threat model report 

*Initially prepared by [FYEO](https://www.fyeo.io/) for the Axelar Foundation with contributions from the Amplifier Advisory Committee and the Interop Labs engineering team. This threat model does not identify specific threats or risks, but describes areas of potential concern. It is intended for use by auditors as a guide during their audits.*

*This document may be updated from time to time as certain features of the Amplifier product are still under active development.*

#

**Table of Contents**

[**Management summary**](#management-summary)

[**Background**](#background)

[Methodology](#methodology)

[**Threat model results**](#threat-model-results)

[System description and overview](#system-description-and-overview)

[Protected assets by the system](#protected-assets-by-the-system)

[Protected Asset Categories](#protected-asset-categories)

[System Security Model](#system-security-model)

[Threat actor analysis](#threat-actor-analysis)

[Identified threats](#identified-threats)

[Conclusion and Results](#conclusion-and-results)

[Conclusion](#conclusion)

# 

# Management summary 

The threat model analysis validates the platform's robust security model, emphasizing secure authentication, data protection, and modern cryptographic practices. Focused on identifying key threats, the analysis pinpointed smart contract vulnerabilities as the main concern, necessitating rigorous security and auditing measures.

The Axelar platform enables secure cross-chain communication, asset transfers, and message routing between diverse blockchain environments. However, given the complexity of interchain operations, several high-priority security risks have been identified that could impact system integrity, user trust, and financial security.

This report has been focused on the integration of Axelar to layer-1 blockchains via Axelar's Interchain Amplifier mechanism.

* The analysis highlights **Cross-Chain Message Tampering** and **Double-Spend Risks** as critical threats, where unauthorized message modification or transaction duplication could lead to significant asset loss.   
* Other medium-priority risks, such as **Contract Logic Exploits** and **Cross-Chain Rate Limit Exploits**, indicate vulnerabilities in smart contract functions and rate-limiting mechanisms.   
* Lower-priority threats include **Reentrancy Attacks** and **Integer Overflow/Underflow**, which, though less likely, could disrupt functionality if exploited.

Mitigation strategies will require robust implementation, and an emphasis on smart contract security. Implementing strict protocol safeguards, multi-layered verification, and regular audits will be essential in addressing these risks and preserving platform integrity.

# 

# Background 

This report outlines the findings from a threat model workshop conducted to assess the security posture of a specified system. 

The objective of the threat modeling exercise was to systematically identify potential risks to the system and evaluate its defenses against those identified threats. The process was aimed at uncovering vulnerabilities, assessing the impact of potential threats, and recommending strategies to enhance the system's security. 

This initiative responds to the necessity for rigorous security assessments in today's complex and rapidly evolving technological landscapes, where systems may handle sensitive data, financial transactions, or critical operational functions. Through this comprehensive threat modeling exercise, the goal was to ensure the integrity, confidentiality, and availability of the system's assets and functionalities.

## 

## Methodology 

The methodology adopted for the threat model workshop is inspired by established threat modeling practices, customized to address the unique aspects and security requirements of the system under review. The process was structured into several key phases, conducted over multiple workshops with stakeholder engagement, as follows:

**System Function Analysis:** Initially, the workshop focused on understanding the system's architecture, core functionalities, and operational mechanisms. This foundational analysis laid the groundwork for identifying critical components and their interactions within the system.

**Protected Assets Analysis:** Subsequently, the workshop identified and categorized assets crucial to the system's security and operation. This step involved distinguishing between various types of assets, such as data, financial, or infrastructural assets, prioritizing them based on their sensitivity and significance.

**Information Flow Analysis:** An examination of the information flow within the system was conducted to trace how data is processed, stored, and transmitted. This analysis aimed to identify potential vulnerabilities or points of exposure in data handling and transfer processes.

**Threat Actors and Motivations Analysis:** Identifying potential adversaries, understanding their capabilities, and assessing their motivations were crucial for evaluating the threat landscape. This phase involved classifying threat actors, from individual hackers to sophisticated entities, and analyzing the potential risks they pose to the system.

**Threat Identification and Classification:** The final phase involved integrating insights from the preceding steps to pinpoint specific threats to the system. These threats were then classified based on their severity, taking into account the likelihood of occurrence and potential impact. This classification facilitated a targeted approach to prioritizing and addressing security vulnerabilities.

The methodology emphasized an interactive and iterative process, incorporating scenario analysis, stakeholder discussions, and technical evaluations to achieve a holistic understanding of the system's security challenges. By adapting this structured approach, the threat model workshop aimed to provide actionable insights and recommendations to strengthen the system's defenses against identified and potential security threats.

# Threat model results  

In this chapter we go through the results of the threat model workshops.

## System description and overview 

The Axelar Amplifier provides a modular, secure infrastructure for interoperable cross-chain transactions and messaging, with GMP for simplified application integration, external verifiers for message validation, and governance through Axelar’s Cosmos SDK.

* **Modular Infrastructure**:  
  * **Gateways**: On-chain components enabling dynamic cross-chain messaging.  
  * **CosmWasm Message Routers**: Route and verify messages securely across chains.  
* **Asset Management**:  
  * **Wrapping/Unwrapping**: Converts assets for interoperability.  
  * **Multi-signature Accounts**: Custody on non-smart-contract chains  
* **General Message Passing (GMP)**: Standardized, simple cross-chain messaging.  
* **Security and Governance**:  
  * **External Verifiers**: Ensure secure cross-chain transactions by validating and signing commands for communication between the Axelar network and connected chains.   
  * **External Validators:** Participate in consensus and verify cross-chain transactions by monitoring multiple external chains  
  * **Cosmos SDK Governance**: Validator voting for decentralized protocol updates.

## Protected assets by the system 

The system employs a multifaceted approach to asset protection, central to its security architecture. The system's asset protection strategy is designed to mitigate threats and vulnerabilities, ensuring the integrity and confidentiality of user assets and data. The following delineates the categories of assets protected within the system and outlines the protective mechanisms in place:

### Protected Asset Categories 

**User Funds**:

* **Locked Tokens**: Tokens locked on the source chain during a cross-chain transfer.  
* **Wrapped Tokens**: Representations of locked tokens issued on the destination chain (e.g., Ethereum tokens on another, newly connected layer-1 blockchain).  
  **Governance and Validator Assets**:  
* **Staked Tokens**: Tokens staked by validators and verifiers, which are at risk if they engage in malicious activity.  
  **Multi-signature Accounts**:  
* **Multi-sig Wallets**: Custodial accounts on connected blockchains, controlled by external verifiers and storing user funds temporarily for secure asset handling.  
  **Protocol-Controlled Accounts**:  
* **Admin Keys**: Keys controlling protocol settings, such as introducing new tokens or updating multi-sig accounts in response to verifier changes.  
  **Cross-chain Message Integrity**:  
* **Message Integrity Tokens**: Guarantees the authenticity of cross-chain messages, protecting against spoofing and unauthorized double-spend attempts.

## 

## System Security Model 

The security model for Axelar Amplifier emphasizes decentralized verification, governance, and a layered approach to validating cross-chain operations:

1. **External Verification**: Independent verifiers authenticate and authorize messages using Axelar's gateways and multi-layer verification protocols, ensuring message integrity for GMP and asset transfer. For blockchains connected via Interchain Amplifier, a multi-signature (multi-sig) wallet is managed by external verifiers to handle transactions securely.  
2. **Governance and Validator Oversight**: Axelar’s governance, powered by the Cosmos SDK, enforces protocol updates, contract migrations, verifier roles, and chain integrations. Validators, who stake Axelar tokens, vote on these changes, ensuring a decentralized and community-driven approach to managing Axelar's infrastructure. Governance includes a proposal system where validators review and approve requests to modify the Amplifier’s core components or add integrations.  
3. **Modular Gateway and Verification Layers**: Amplifier introduces a modular system where each cross-chain integration has customizable gateways and CosmWasm-supported on-chain message routers. These routers and gateways manage verifications per chain, allowing independent control and auditability for each cross-chain link.  
4. **Relayer Liveness Trust and Accountability**: While relayers in the Amplifier architecture are non-trusted entities for message integrity, they are essential for message liveness (i.e., timely delivery). Governance can penalize or replace relayers that fail to forward messages, maintaining reliability and service continuity across chains.  
5. **Stake Mechanism and Verifier Incentives**: External verifiers are required to stake tokens as collateral, incentivizing integrity and punishing malicious behavior through staking risks. Verifiers earn rewards for correct activity, and though Axelar lacks automatic slashing, governance retains authority to withhold a verifier’s stake indefinitely if they engage in harmful actions.  
 


## Threat actor analysis 

The threat actor analysis conducted as part of our threat modeling exercise has illuminated a diverse array of potential adversaries, each with distinct motivations and capabilities that could pose risks to the system. 

This analysis categorizes threat actors ranging from general hackers and DeFi-specific attackers to internal stakeholders such as node operators, and even end-users. 

During the workshop the following classes of threat actors were identified:

| Threat Actor | Description | Motivation | Capabilities |
| ----- | ----- | ----- | ----- |
| **General DeFi Hackers** | External attackers seeking vulnerabilities in smart contracts for unauthorized access to funds | Financial gain | Capable of exploiting smart contract vulnerabilities (e.g., reentrancy attacks, logic flaws) |
| **Compromised Validators** | Validators within Axelar's governance system who may act maliciously or collude | Financial gain or control over protocol | If achieving quorum, they can alter governance votes, approve fake transactions, or alter protocol |
| **External Verifiers** | Entities tasked with message verification and authentication | Financial gain; malicious influence on cross-chain actions | Can validate or deny transactions; colluding verifiers may approve false transactions |
| **Malicious Relayers** | Relayers who facilitate message passage but may selectively choose not to forward messages after payment | Financial gain; disruption of service (affects liveness) | Can refuse to relay messages but cannot alter them; affects only liveness, not integrity |
| **Governance Attackers** | Attackers who gain significant control over Axelar's governance (e.g., 75% of staked tokens) | Full control over protocol for unauthorized actions | Can change protocol settings, approve malicious verifiers, and migrate contracts |
| **Cross-chain Compromisers** | Attackers focusing on low-security chains within Axelar, using them as entry points to compromise other chains | Financial gain; disruption across connected ecosystems | Limited by verifier support on small chains, can affect larger ecosystems if compromising verifier quorum on a smaller chain |

The highest-risk threat actor in the Axelar Amplifier system would appear to be **Compromised Validators and External Verifiers**, particularly due to their ability to collude and alter cross-chain message verification and governance. A quorum of compromised validators could authorize false transactions, exploit governance settings, or disable essential components, potentially impacting message integrity, user funds, and cross-chain interoperability. Since verifiers control multi-signature wallets, they could also compromise asset custody, posing significant risks to wrapped and locked tokens if acting maliciously.

## Identified threats 

The platform faces a spectrum of security threats that range from critical to high, medium and low priorities, each posing distinct challenges to the integrity, functionality, and trustworthiness of the system.

* High-priority threats include **Cross-Chain Message Tampering** and **Double-Spend Risk**, where unauthorized message modifications or duplicate transactions could lead to significant financial losses. **Asset Custody Compromise** and **Governance Exploitation** also rank as critical risks, as compromised verifiers or governance controls could enable unauthorized access to locked assets or protocol manipulation.  
* Medium-priority threats, such as **Contract Logic Exploits** and **Multisig Key Compromise**, highlight vulnerabilities within smart contract operations and key management, posing risks to asset integrity and system reliability. **Cross-Chain Rate Limit Exploits** and **Relayer Non-responsiveness** are of moderate concern, with potential impacts on transaction speed and liveness.  
* Low-priority threats, including contract **Integer Overflow/Underflow**. Additional risks from **Verifier Collusion**, **Stake-Based Attacks**, and **Phishing or Social Engineering** indicate broader threats to protocol governance and the security of validator roles. 

| Title | Description | Threat Actors | Impact | Probability |
| ----- | ----- | ----- | ----- | ----- |
| Cross-Chain Message Tampering | Unauthorized modification or spoofing of messages between chains. | Compromised External Verifiers, Governance Attackers | Critical | Medium |
| Double-Spend Risk | Duplicate messages leading to double-spend scenarios across chains. Relayer relays the same message twice etc., should not be able to double spend | Compromised Validators, External Verifiers, Relayer, DeFi Hackers | Critical | Medium |
| Contract Logic Exploits | Exploiting vulnerabilities in smart contracts within Axelar or its gateways | General DeFi Hackers, Validators | Critical | Medium |
| Multisig Key Compromise | Unauthorized access to the multisig account controlling assets on chains without native smart contracts | Compromised External Verifiers | Critical | Medium |
| Asset Custody Compromise | Loss of locked or wrapped tokens due to unauthorized multi-sig access or verifier collusion. Check if less than quorum can drain funds | External Verifiers, Compromised Validators | Critical | N/A |
| Governance Exploitation | Malicious changes to protocol governance, enabling unauthorized updates or verifier roles. Check if less than quorum can drain funds | Governance Attackers, Compromised Validators | Critical | N/A |
| Reentrancy Attacks | Recursive calls in smart contracts could lead to fund drain by allowing multiple executions before state updates | General DeFi Hackers | Critical | Low |
| Integer Overflow/ Underflow | Exploits due to improper handling of numbers, potentially leading to financial losses or unintended behaviors. No raw arithmetic allowed | General DeFi Hackers | High | Low |
| Cross-Chain Rate Limit Exploit | Bypassing rate limits on specific chains, draining assets more quickly than intended. Implemented as a control to slow down an attack; purely on Axelar | General DeFi Hackers, Cross-chain Compromisers | Medium | Low |
| Relayer Non-responsiveness | Relayers fail to forward messages, affecting liveness but not integrity. Could this lead to anything other than D.O.S? | Malicious Relayers | Med/ Low | Low |
| Stake-Based Attacks | Attackers gain governance control by accumulating a large stake, potentially overriding protocol safeguards | Compromised Validators | N/A | N/A |
| Verifier Collusion | Verifiers collude to approve unauthorized transactions or bypass integrity checks | External Verifiers, Governance Attackers | N/A | N/A |
| Verifier Node Downtime | Verifiers go offline, affecting message validation and potentially stalling transactions. Assumes honest quorum online | External Verifiers, Validators | N/A | N/A |
| Chain-Specific Vulnerabilities | Weak security on one chain affects all connected chains in the Axelar network. Assumes chains are safe and live | Cross-Chain Compromisers | N/A | N/A |
| Governance Takeover via Delegation | Attackers gain governance control by acquiring delegations from unaware or inactive stakeholders | Governance Attackers | N/A | N/A |
| Fee Manipulation by Relayers | Relayers inflate transaction fees or fail to refund users for failed transactions. Hardcoded currently, no refund implemented | Malicious Relayers | N/A | N/A |
| Phishing and Social Engineering | Attempts to compromise verifier or validator keys through phishing or social engineering | External Threat Actors | N/A | N/A |
| Wallet Connect Hacks | Security of DApps connecting to the exchange, outside of protocol control. This is excluded since there is not the part of the protocol | N/A | N/A | N/A |
| Prover Contract Compromise | Manipulation of cryptographic proofs by malicious actors could bypass verification checks and allow false cross-chain messages. | External Attackers, Cryptographic Attackers | High | Low |
| Gateway Contract Compromise | Unauthorized message routing or transaction tampering at the gateway level. | Malicious Actors, Compromised Verifiers | Critical | Medium |
| Replay Attacks | Reuse of messages on external chains leading to unauthorized transactions or state inconsistencies. | General Hackers, Malicious Validators | Medium | Low |
| Cryptographic Failure | Cryptographic weaknesses or flawed implementations could allow message forgery or unauthorized transactions. | General Hackers, Cryptographic Attackers | Hi | Low |

## 

## Conclusion and Results 

### Conclusion 

The threat model analysis underscores the importance of a proactive and comprehensive approach to security within the DeFi ecosystem. By addressing the identified threats and vulnerabilities through the recommended actions, the platform can significantly enhance its security posture, safeguarding user assets and maintaining trust in its operations. The commitment to ongoing security assessment and adaptation is essential for navigating the challenges and opportunities presented by the rapidly evolving landscape of decentralized finance.
