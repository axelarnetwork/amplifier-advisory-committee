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
2. **Drafting a CAP** – Anyone can draft a **formal proposal** using the [**CAP Template**](https://github.com/stellar/stellar-protocol/blob/3bc9054e4bfe1510acdd60baa2e0636189535576/cap-template.md#L4) and submit it as a **GitHub pull request**.
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

---  

## **Section 3: Security and Risks**

### Stellar Consensus Protocol

The Stellar Consensus Protocol (SCP) has been rigorously defined and reviewed in
academic conferences that include [ACM
SOSP](https://dl.acm.org/doi/pdf/10.1145/3341301.3359636?casa_token=r5u8GKHBJboAAAAA:hmqRVOpUkUok5MFwZNCoqyngv_SxT1kZ82taV2rONWaBFlnmKeQWwjTLfsZtXnBRuyKaT7H5-LnH)
and
[OPODIS](https://drops.dagstuhl.de/storage/00lipics/lipics-vol153-opodis2019/LIPIcs.OPODIS.2019.5/LIPIcs.OPODIS.2019.5.pdf).
Nonetheless, SCP's implementation in
[stellar-core](https://github.com/stellar/stellar-core) may
include optimizations or other differences from the theoretical abstractions
which could require further review and validation.

Notably, stellar-core has never been fully audited. Instead, the SDF runs a [bug
bounty program](https://stellar.org/grants-and-funding/bug-bounty) on
[immunefi](https://immunefi.com/bug-bounty/stellar/information/) and
[hackerone](https://hackerone.com/stellar). This lack of full audits reduces the
confidence in the implementation's security and resilience.

### Stellar Network Security and Stability

Stellar has seen two cases of outage in its 10+ year existence:

- **15 May 2019**: The network [halted for 67
  minutes](https://medium.com/stellar-developers-blog/may-15th-network-halt-a7b933103984)
  due to inability to reach consensus. The identified cause was new nodes
  (beyond the SDF-operated ones) taking too much consensus responsibility and,
  by failing, causing the whole network's outage.
- **April 2021**: The network [halted for 9
  hours](https://status.stellar.org/incidents/7h0czw6mnjzs) on April 6, 2021.
  The cause was some validators, including those run by the SDF, dropping offline
  and causing an outage to the SDF Horizon service. As a result deposits and
  withdrawals were halted some exchanges, including
  [Bitfinex](https://cryptonary.com/the-stellar-blockchain-down-for-over-seven-hours/)
  and
  [Bitstamp](https://cryptobriefing.com/stellar-blockchain-faces-outage-some-validators-go-offline/).
  The issue was fixed by [upgrading the network to Protocol
  16](https://stellar.org/blog/developers/protocol-16-upgrade-guide).

These instances highlight Stellar's prioritization of safety over liveness. In
essence, a halt is preferable to a fork, so the security of funds and integrity
of accounts is prioritized over the system's availability. However, they also
showcase the reliance of the system's stability to the SDF and the risks that
come from such centralization tendencies.

### Stellar (de)centralization

As of March 25, the Stellar network [consists of](https://stellarbeat.io): (i)
183 connectable nodes; (ii) 88 validators; (iii) 74 full validators; (iv) 22
organizations; (v) 23 top tier validators; (vi) 7 top tier organizations.
These numbers make Stellar more centralized than competing Proof-of-Stake
ledgers; for example, XRP has [954 nodes and 198
validators](https://xrpscan.com/validators), Tezos has [294 validators
("bakers")](https://tzstats.com/bakers), and Cardano has [2348 validators
("pools")](https://cexplorer.io/pool).

6 of the 7 top tier organizations (
[Stellar Development Foundation](https://stellarbeat.io/organizations/266107f8966d45eedce41fee2581326d),
[Blockdaemon Inc](https://stellarbeat.io/organizations/c1a16879b171bc6f0087f884acbea046),
[SatoshiPay](https://stellarbeat.io/organizations/753e017d811e12c41ef03b5b4c51a1a5),
[Franklin Templeton](https://stellarbeat.io/organizations/bc8b7a147ab684c37551a69369b70953),
[Creit Technologies LLP](https://stellarbeat.io/organizations/a742187e2b2408eea2abad9d277f43aa),
[Public Node](https://stellarbeat.io/organizations/2dd1cd0e5ba445846799c0d1114dda47))
run 3 nodes each, as per the [documentation's
recommentation](https://developers.stellar.org/docs/validators/tier-1-orgs),
whereas the other
([LOBSTR](https://stellarbeat.io/organizations/ad733706cebb901f8b8cbb1b6a9bb785))
runs 5 nodes.

9 (out of 23) top tier validators from 5 of the 7 organizations (SatoshiPay, Franklin
Templeton, LOBSTR, Creit Technologies LLP, Public Node) demonstrate operation
warnings regarding history archive verification (
[SatoshiPay Iowa](https://stellarbeat.io/nodes/GAK6Z5UVGUVSEK6PEOCAYJISTT5EJBB34PN3NOLEQG2SUKXRVV2F6HZY),
[FT SCV 1](https://stellarbeat.io/nodes/GARYGQ5F2IJEBCZJCBNPWNWVDOFK7IBOHLJKKSG2TMHDQKEEC6P4PE4V),
[FT SCV 2](https://stellarbeat.io/nodes/GCMSM2VFZGRPTZKPH5OABHGH4F3AVS6XTNJXDGCZ3MKCOSUBH3FL6DOB),
[FT SCV 3](https://stellarbeat.io/nodes/GA7DV63PBUUWNUFAF4GAZVXU2OZMYRATDLKTC7VTCG7AU4XUPN5VRX4A),
[LOBSTR 1](https://stellarbeat.io/nodes/GCFONE23AB7Y6C5YZOMKUKGETPIAJA4QOYLS5VNS4JHBGKRZCPYHDLW7),
[LOBSTR 4](https://stellarbeat.io/nodes/GA7TEPCBDQKI7JQLQ34ZURRMK44DVYCIGVXQQWNSWAEQR6KB4FMCBT7J),
[LOBSTR 5](https://stellarbeat.io/nodes/GA5STBMV6QDXFDGD62MEHLLHZTPDI77U3PFOD2SELU5RJDHQWBR5NNK7),
[Hercules by OG Technologies](https://stellarbeat.io/nodes/GBLJNN3AVZZPG2FYAYTYQKECNWTQYYUUY2KVFN2OUKZKBULXIXBZ4FCT))
and running an outdated Stellar-core version
([Alpha Node Validator](https://stellarbeat.io/nodes/GBPLJDBFZO2H7QQH7YFCH3HFT6EMC42Z2DNJ2QFROCKETAPY54V4DCZD)).
These warnings are significant, since most organizations require agreement from
them, Tier 1 organizations "bear the safety and
liveness of the Stellar network on their shoulders". Notably, one of their
validators' main responsibilities is publishing an archive of transactions in
order to ["make the network more
resilient"](https://developers.stellar.org/docs/validators/tier-1-orgs).

All validators run the same software
([stellar-core](https://github.com/stellar/stellar-core)], which highlights the
extreme centralization of the software development process around Stellar's core
protocol. Consequently, bugs in stellar-core can escalate to systemic risks and
affect the entire Stellar network.

### Soroban Security

Soroban's core contracts were [audited by Veridise between October-December
2023](https://veridise.com/wp-content/uploads/2024/11/VAR_Stellar_Soroban-5.pdf).
The review discovered 8 issues, of which one was of medium severity (fixed).

On March 2024 the SDF launched the [Soroban Security Audit
Bank](https://stellar.org/blog/developers/the-soroban-audit-bank-fostering-a-secure-smart-contract-ecosystem),
a program for funding security audits of Soroban-based projects. As of March
2025 it is unclear how many audits and tools have received funding from this
program.

Various tools exist to assist Soroban smart contract developers to write secure
contracts or formally verify their implementations. Among others, they include:

- [CoinFabrik's Scout](https://github.com/CoinFabrik/scout-soroban);
- [Certora's formal Wasm tool](https://www.certora.com/blog/formally-verifying-webassembly);
- [OtterSec's stellar-verify](https://github.com/otter-sec/stellar-verify);
- [Runtime Verification's Komet](https://docs.runtimeverification.com/komet).

The existence of such tools enables the creation of high-assurance code and can
help increase confidence in the security guarantees of Soroban-based smart
contracts.

---  

## **Section 4: Axelar Integration Components **
### 4.1 Code Quality and Transparency
Interop Labs was responsible for developing the Soroban external contracts. [Axelar Amplifier Stellar](https://github.com/axelarnetwork/axelar-amplifier-stellar) is the Axelar Cross-chain Gateway Protocol implementation developed in Rust programming language. The codebase contains the following components:

- Gas Service
- Gateway
- Operators
- Interchain Token Service
- Interchain Token
- Token Manager
- Stellar Upgrader

Axelar Amplifier Stellar underwent the following audits:
- FYEO [1/23/2025](https://github.com/axelarnetwork/audits/blob/main/audits/2025-01%20FYEO_Soroban.pdf) 
- Ottersec [Not published](https://github.com/axelarnetwork/audits/blob/main/audits/)

Summary of findings from Stellar CGP audits (Reported-Fixed-Acknowledged):

| Company            | Critical | High  | Medium | Low   | Info  |
|--------------------|----------|-------|--------|-------|-------|
| **FYEO 1/25**      |          |       |        | 3-2-1 | 4-0-4 |
| **Ottersec TBD**   |          |       |        |       |       |

[Ackee](https://ackee.xyz/) performed a cross-check of audit reports and confirmed that from 7 findings reported by FYEO, 2 were remediated and 5 acknowledged. The Ottersec audit was not published during the integration report writing.

No audit report for [Axelar Amplifier / External Gateways / Stellar](https://github.com/axelarnetwork/axelar-amplifier/tree/main/external-gateways/stellar) code was provided.

### 4.2 Understanding of Deployment and Maintenance Plans
Deployment scripts for Stellar Axelar components are provided, and the process is well documented in the [Axelar contract deployments repository](https://github.com/axelarnetwork/axelar-contract-deployments/tree/main/stellar). The code is well-structured, and [Ackee](https://ackee.xyz/) did not identify any violations of best practices in the development scripts.

### 4.3 Mitigation of Potential Risks
Stellar and Axelar confirm that the system includes proper logging and mechanisms to effectively handle unusual situations in the network.

## **Section 5: Committee Members**

The **Amplifier Advisory Committee** overseeing this integration consists of the following teams:

- **Axelar**: Liana Spano, Coordinator
- **Node.Monster**: Eyal Alsheich, Contributor
- **Common Prefix**: Nikolaos Kamarinakis, Contributor; Dimitris Karakostas, Contributor
- **Ackee**: Stepan Sonsky, Contributor
- **Eiger**: Marcin, Contributor
