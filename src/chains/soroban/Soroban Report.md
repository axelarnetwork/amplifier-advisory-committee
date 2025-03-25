## **Section 2: Network and Protocol Integrity**


### **2.1 Network Architecture**

Stellar is a **Layer-1 blockchain** designed for **cross-border payments, asset issuance, and decentralized financial applications**. Unlike most blockchains, Stellar does not use **Proof-of-Work (PoW) or Proof-of-Stake (PoS)**. Instead, it operates on the **Stellar Consensus Protocol (SCP)**, which is based on **Federated Byzantine Agreement (FBA)**.


#### **Consensus and Validation Model**

Stellar’s **unique consensus mechanism** allows each node to select a trusted set of validators (**quorum slices**) to determine transaction validity. This **decentralized voting process** ensures fast finality while maintaining security.

There are **three types of Stellar Nodes**:



* **Basic Validators** – Submit and validate transactions but do not publish historical data.
* **Full Validators** – Submit transactions and store **historical snapshots of the ledger**.
* **Archiver Nodes** – Store **historical ledger data** but do not participate in consensus.

As of **March 2024**, Stellar operates with **~86 Validators and ~72 Full Validators**, with **23 Organization  operates the nodes**. The **Stellar Development Foundation (SDF) operates three Full Validators**. The Geo decenetlation of the nodes are diversified betwee Germany (26), Unites States (36), Finland (8) and Other (24)


#### **Decentralization vs. Performance Trade-offs**

Stellar’s **Federated Byzantine Agreement (FBA) model** allows **quorum sets** to form organically, but network finality still relies on a small number of **Tier 1 Organizations** that control the majority of quorum slices. These organizations serve as the **core pillars of network consensus**, but the selection process remains informal and lacks clear transparency.

Stellar’s **validator network is smaller** compared to **PoS blockchains**, making it efficient but raising concerns about **concentration risk** among **SDF and key ecosystem participants**.


#### **Transaction Speed and Scalability**



* **Settlement Time**: Transactions settle in **2-5 seconds**, making Stellar one of the **fastest payment-focused chains**.
* **Transaction Fees**: Minimal, with a **base fee of 0.00001 XLM (~$0.000001 USD per transaction)**.
* **Throughput**: The network can process **~5,000 transactions per second (TPS)** under optimal conditions.


#### **Smart Contract Capabilities**

Stellar introduced **Soroban**, a **WASM-based smart contract platform**, via **[Protocol 20](https://stellar.org/blog/developers/protocol-20-upgrade-guide)**. Soroban is currently in **Phase 0 of its three-phase rollout**, limiting full network deployment. **Future phases will enable permissionless smart contract execution. The [CAP-0046 ](https://github.com/stellar/stellar-protocol/blob/master/core/cap-0046.md)provide an overview of changes to stellar-core and the Stellar Protocol needed to enable the Soroban smart contract system.**


##### **Key Features of Soroban:**



* Rust-Based Smart Contracts – Uses WebAssembly (WASM) for execution, improving efficiency.
* Scalable State Management – Implements state expiration and resource pricing, preventing state bloat.
* Predictable Fees – Introduces a fee model that balances cost-efficiency and network sustainability.
* Seamless Integration – Works alongside Stellar’s native asset issuance and payments infrastructure.


#### **Anchors and Fiat On-Ramps**

Stellar **anchors** serve as **regulated financial intermediaries** that bridge traditional financial systems with blockchain-based payments. As of **March 2024**, the **Stellar Anchor Directory** lists **71 financial institutions** supporting **multiple fiat currencies** (USD, EUR, MXN, etc.) and **Circle’s USDC stablecoin**.


#### **Asset Issuance and Decentralized Exchange (DEX)**

Stellar natively supports **tokenized assets** with built-in compliance features like **KYC, multi-signature control, and time-locked escrows**. The **Stellar DEX (SDEX)** and **Automated Market Makers (AMMs)** enable **on-chain liquidity provision** for assets issued on Stellar.


### **2.2 Governance and Compliance**


#### **Governance Model**

Stellar operates a structured governance model centered around[ Core Advancement Proposals (CAPs) ](https://github.com/stellar/stellar-protocol/blob/master/core/README.md)for network-level changes and **[Stellar Ecosystem Proposals (SEPs)](https://github.com/stellar/stellar-protocol/tree/master/ecosystem)** for ecosystem standards. Governance impacts **protocol upgrades, fee structures, and ecosystem functionality**, with participation from **community members, tokenholders, and the Stellar Development Foundation (SDF).**


#### **Core Advancement Proposals (CAPs) Process**

The **CAP process** governs **technical upgrades and network changes**:



1. **Pre-CAP (Initial Discussion)** – Any community member can propose an idea via the [**stellar-dev mailing list**](https://groups.google.com/g/stellar-dev) for feedback.
2. **Drafting a CAP** – Anyone can draft a **formal proposal** using the **CAP Template** and submit it as a **GitHub pull request**.
3. **CAP Core Team Review** – The **CAP Core team (members from SDF, including Nicolas, Jed, and David)** reviews and refines the proposal.
4. **CAP Core Team Vote** – The **CAP Core team must unanimously approve** the proposal before implementation begins.
5. **Implementation & Validator Consensus** – Approved CAPs must be implemented in code and **adopted via a protocol upgrade**, requiring **majority validator approval**.

As of **February 2024**, all major **network parameters appear subject to the CAP process**, with no disclosed exceptions from the **Stellar Development Foundation (SDF).**


#### **Stellar Ecosystem Proposals (SEPs) Process**

SEPs define **standards and methods for applications built on Stellar**, including **wallets, APIs, and asset issuance frameworks**.



* **Informational SEPs** are **not formally endorsed by SDF** and require approval from **two SEP team members**.
* **Standard SEPs** require **three approvals**, including two from **SDF members**, and must address all **team concerns** before approval.

As of **March 2024**, **nine of the ten SEP team members** are also **SDF members**, reinforcing SDF’s influence over **ecosystem standards**.


#### **Stellar Community Fund & Neural Quorum Governance**

The **Stellar Community Fund (SCF)** distributes **XLM grants** to support ecosystem growth.



* The **SCF Selection Panel** initially **reviews applications**, filtering projects before presenting them for a **Community Vote**.
* **Voting uses "Neural Quorum Governance"**, a reputation-based model that **weights votes based on expertise, peer trust, and contributions**.
* As of **November 2023**, the first version of **Neural Quorum Governance** was deployed on **Soroban’s testnet**.
* **By mid-2024**, SCF aims to **fully transition** to this governance model for grant allocation.

Currently, **Community Votes serve as a signaling mechanism** rather than a **binding decision process**, with final funding decisions left to the **SCF Selection Panel**.


#### **Regulatory Considerations**

Stellar has faced **regulatory scrutiny**, particularly regarding the classification of **XLM as a security**:



* **SEC Investigation into Coinbase (2024)** – The **U.S. SEC examined XLM’s status as a security**, leading to compliance uncertainties.
* **Class-Action Lawsuits Against Dapper Labs & SDF (2021-2024)**:
    * **Video Privacy Protection Act (VPPA) Violation** – Allegations of unauthorized data collection.
    * **Unregistered Securities Sales (NBA Top Shot Moments)** – Resulted in a **$4M settlement in June 2024**.


#### **Key Risks**



1. **Validator Centralization** – A **small number of Tier 1 Organizations** influence the consensus process.
2. **Regulatory Uncertainty** – **Potential SEC enforcement** actions could impact **XLM’s status and exchange listings**.
3. **Reliance on SDF** – The **Stellar Development Foundation** plays a central role in **governance, funding, and validator selection**.
