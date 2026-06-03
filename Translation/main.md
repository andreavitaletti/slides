---
marp: true
theme: beam
paginate: true
header: "Blockchain Introduction"
footer: "Sapienza University of Rome"
style: |
  @import url('https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.1/css/all.min.css');
  section {
    font-size: 28px;
  }
  h1 {
    color: #2c3e50;
  }
  h2 {
    color: #34495e;
  }
  .box {
      background-color: var(--color-primary, #1f38c5);
      color: white;
      padding: 25px;
      border-radius: 8px;
      margin-top: 20px;
    }
  .box h3 {
      color: white !important;
      margin-top: 0;
      border-bottom: 1px solid rgba(255,255,255,0.3);
      padding-bottom: 10px;
    }
  .box strong { color: #ffcc00; }
  .source {
    position: absolute;
    bottom: 10px;
    right: 10px;
    font-size: 12px;
    background: rgba(255, 255, 255, 0.7);
    padding: 2px 8px;
    border-radius: 4px;
    z-index: 100;
  }
  .source a {
    color: #333;
    text-decoration: none;
  }
  .two-col {
    display: grid;
    grid-template-columns: 1fr 1fr;
    gap: 30px;
    margin-top: 10px;
  }
  .highlight {
    color: #c0392b;
    font-weight: bold;
  }
---

<!--
https://rnd195.github.io/marp-community-themes/theme/beam.html
https://fontawesome.com/icons
-->

# Blockchain Introduction

**Andrea Vitaletti**
*vitaletti@diag.uniroma1.it*
*Sapienza Università di Roma*

---

# Organization

- **A2** 15:00–17:00 Thursday
- **A7** 10:00–13:00 Friday
- In continuous evolution
- Based on what I consider well done work … no need to reinvent the wheel
- Comments, suggestions, thoughts, feedback, missing references … are very welcome
- <i class="fa-brands fa-google"></i> [Google Classroom](https://classroom.google.com/c/MjMwODQyMTcwODBa?cjc=wkqxriz)
- <i class="fa-brands fa-github"></i> [https://andreavitaletti.github.io/BC/](https://andreavitaletti.github.io/BC/)

---

# Goal

Achieve **consensus** on what is a blockchain, the main tech ingredients to implement it, and describe its evolution ;-)

<div class="box">

### :dart: Learning Objectives
Understand the **distributed ledger** concept, the **consensus problem**, key **cryptographic primitives**, and the **evolution** from Bitcoin to smart contracts and Web3.

</div>

---

# The History of Blockchain Technology

| Era | Year | Milestone |
|-----|------|-----------|
| **Origin** | 1991–2008 | Stuart Haber & Scott Stornetta work on first Blockchain; Satoshi Nakamoto releases Bitcoin whitepaper (2008) |
| **Transactions** | 2009–2013 | First Bitcoin purchase (10,000 BTC); Bitcoin marketplace surpasses $1B |
| **Contracts** | 2013–2016 | Vitalik Buterin releases Ethereum whitepaper; Ethereum Genesis block created |
| **Applications** | 2016–2018 | EOS, Hyperledger, R3 consortium; Blockchain for business |

<div class="source"><a href="https://intellipaat.com/blog/wp-content/uploads/2022/02/History-of-Blockchain-Technology.jpg">Source: Intellipaat</a></div>

---

# A Transaction: The Exchange of an Asset

<div class="two-col">
<div>

A transaction is the **exchange** (or agreement for an exchange) **of an asset**

Key elements:
- **FROM** (state A)
- **TO** (state B)
- **WHEN**
- **ASSET** (what is transferred)

</div>
<div>

**Example — Bitcoin Transaction:**
- Hash ID: `68e9a945...`
- Amount: `0.00180720 BTC · €171.19`
- Fee: `232 SATS · €0.22`
- Status: ✅ Confirmed (3 confirmations, Block 882,524)

</div>
</div>

<div class="source"><a href="https://www.blockchain.com/explorer/transactions/btc/68e9a945414bc9b7a768be36ea1df992e08ffee5527a30c2b70d4474bfa8f9ec">blockchain.com</a></div>

---

# Financial Assets: The Evolution of Money

| Year | Form |
|------|------|
| 5000 B.C. | Barter System |
| 4000 B.C. | Gold |
| 7th Century B.C. | Metal Coins |
| 812 | Paper Money |
| 1928 | Plastic Cards |
| 1994 | Electronic Money |
| **2009** | **Crypto Currency** |

Money has always evolved alongside trust, technology, and governance.

<div class="source"><a href="https://thumbs.dreamstime.com/b/evolution-money-concept-set-abstract-diagram-222996275.jpg">Source: Dreamstime</a></div>

---

# Trust "Individuals" … or Servers ;-)

<div class="box">

### :lock: Black Box — Centralized Trust
Traditional financial systems rely on **trusted intermediaries** (banks, gateways) acting as black boxes with "**humans in the loop**". We trust individuals — or servers — to manage our assets correctly.

</div>

The fundamental question: **What happens when those intermediaries cannot be trusted?**

---

# Consensus from "Society" … or a Distributed Protocol

<div class="box">

### :white_check_mark: White Box — Decentralized Consensus
Blockchain replaces centralized trust with **algorithmic consensus** — a distributed protocol run by the "society" of network participants. The rules are open, transparent, and formally verifiable.

</div>

- **Black Box** → Trust individuals / servers
- **White Box** → Consensus via algorithms

---

# In the Networking World

<div class="two-col">
<div>

**Centralized**
One hub controls everything (e.g. Google servers)

**Decentralized**
Multiple hubs, each with their own spokes

**Distributed**
Every node is equal; no single point of failure

</div>
<div>

This taxonomy, introduced by **Paul Baran**, applies directly to blockchain architecture.

Blockchain is a **distributed** system — the ledger is replicated across all nodes with no central authority.

</div>
</div>

<div class="source"><a href="https://nvlpubs.nist.gov/nistpubs/ir/2018/NIST.IR.8202.pdf">NIST IR 8202</a></div>

---

# In Governance

<div class="two-col">
<div>

### Centralized: Trust
One party (individual, institution) is trusted to manage the ledger correctly.

- Easy to implement
- Single point of failure
- Opaque processes

</div>
<div>

### Decentralized: Consensus
The "society" of participants agrees on the state of the ledger through a protocol.

- More complex
- Resilient and open
- Transparent and verifiable

</div>
</div>

---

# Creation: CryptoCurrency vs Currency

<div class="two-col">
<div>

### CryptoCurrency
- A **distributed cryptographic protocol**
- Money is "minted" according to protocol rules
- Authenticity via **digital signature**

</div>
<div>

### Currency
- Issued by a **Central Bank**
- Authenticity via:
  - Physical watermarking (bills)
  - Bank security systems (digital)

</div>
</div>

*Credits: Alessandra Scafuro*

---

# Payments: CryptoCurrency vs Currency

<div class="two-col">
<div>

### CryptoCurrency
1. Sender shares their public key (PK_B)
2. Broadcasts signed transaction
3. Nodes validate
4. **Consensus protocol** selects block
5. Transaction is official ✅

</div>
<div>

### Currency
1. Swipe card at merchant
2. Merchant's bank contacts gateway (e.g. Visa)
3. Gateway contacts source bank
4. Banks exchange ledger entries
5. Settlement occurs 🏦

</div>
</div>

---

# Correctness: CryptoCurrency vs Currency

<div class="two-col">
<div>

### CryptoCurrency
- The **protocol is open**
- We have **formal proofs**
- **Everyone** can check every transaction on the ledger

</div>
<div>

### Currency
- We **trust** the correctness of banks' systems and gateways
- Subject to **auditing** by regulators

</div>
</div>

---

# Privacy: Digital Currency

In traditional digital payments, the following parties **see your transactions**:

- The **source bank**
- The **destination bank**
- The **gateways** (e.g. Visa, Mastercard)

Payments flow through a chain of trusted intermediaries, each of which maintains a record.

---

# Privacy: Cryptocurrencies

In a permissionless blockchain like Bitcoin:

- **All** network participants can see all transactions
- Transactions are pseudonymous (public keys, not names)
- The full transaction graph is publicly visible on the ledger

<div class="box">

### :eye: Pseudonymity ≠ Anonymity
Linking public keys to real identities (e.g. via KYC at exchanges) can de-anonymize users.

</div>

---

# Traditional vs Blockchain Networks

| | Traditional | Blockchain |
|---|---|---|
| **Messaging** | Through central infrastructure | Peer-to-peer |
| **Processing** | Centrally, batch or per transaction | Decentralized, in 'blocks' |
| **Ledger** | Central, closed (one trusted party) | Decentralized, public |
| **Front-end** | Unchanged | Unchanged |

<div class="source"><a href="https://www.paymentscardsandmobile.com">paymentscardsandmobile.com</a></div>

---

# Transaction

A transaction is an **atomic event** supported by the protocol:

- **Andrea → Maria 1 BTC** (simple payment)
- **State 1 → State 2** in the world computer (smart contract execution)

```
FROM: Andrea    TO: Maria
WHEN: timestamp  WHAT: 1 BTC
↓
Grouped into a Block
↓
Block added to the chain (time →)
```

<div class="source"><a href="https://upload.wikimedia.org/wikipedia/commons/thumb/f/fe/CanadianCheque.svg/1920px-CanadianCheque.svg.png">Wikipedia</a></div>

---

# Atomic Transactions

<div class="box">

### :zap: Atomicity
A transaction either **fully succeeds** or **fully fails** — there is no intermediate state. Sending 10 coins from a wallet of 50 must result in exactly 40 remaining — no partial transfers.

</div>

This prevents:
- Coins being deducted from the sender without being credited to the receiver
- Double-spending exploits mid-transfer
- Inconsistent ledger states across nodes

---

# Ledger of Transactions

The blockchain is fundamentally a **ledger** — an ordered log of transactions:

| FROM | TO | WHEN | WHAT |
|------|----|------|------|
| A | B | a/b/c | 10 |
| B | C | e/f/g | 5 |
| B | D | e/f/g | 7 |
| … | … | … | … |

The key challenge: **where** is this ledger stored, and **who** controls it?

---

# Ledger of Transactions: WHERE

<div class="two-col">
<div>

**Centralized (Easy)**
- Intermediaries (banks) manage the ledger
- Built on **trust** in individuals
- Single point of control

</div>
<div>

**Distributed (Difficult)**
- No intermediaries — **disintermediation**
- Requires **consensus** among peers
- No single point of failure or control

</div>
</div>

The core challenge of blockchain: achieving consensus in a distributed setting without trusted intermediaries.

---

# WHERE — Centralized

A **single ledger** sits at the center. All participants connect to it and trust it to be correct.

- ✅ Easy to implement
- ✅ High performance
- ❌ Single point of failure
- ❌ Requires trust in the central party

---

# WHERE — Distributed

**Every node** holds a copy of the ledger. All copies must stay synchronized through a consensus protocol.

- ✅ Resilient — no single point of failure
- ✅ Censorship-resistant
- ❌ Complex consensus required
- ❌ Lower throughput

---

# What is Blockchain?

<div class="box">

### :link: Definition
A **distributed ledger** that can record transactions in an **immutable, verifiable, and permanent** way.

</div>

**Two key dimensions:**

1. **Who writes?** (CONSENSUS)
   - *Permissioned* — only approved participants
   - *Permissionless* — anyone can propose blocks

2. **Who reads?**
   - *Private* — restricted access
   - *Public* — open to all

> **EASY** = making an immutable, verifiable ledger  
> **DIFFICULT** = achieving decentralized governance (from trust to consensus)

---

# Trust vs Consensus

<div class="two-col">
<div>

### (Individuals) TRUST
Traditional systems: banks, gateways, governments manage the ledger.

</div>
<div>

### CONSENSUS (Society)
Blockchain: the network of peers collectively maintains and validates the ledger.

</div>
</div>

This shift from **trust** to **consensus** is the defining innovation of blockchain technology.

---

# Simple Experiment: Network Latency

Try this at home to observe how information travels across the Internet:

```bash
# Resolve Yahoo Japan's IP
nslookup Yahoo.co.jp        # → 183.79.135.206

# Find where the server is located
curl http://api.geoiplookup.net/?query=183.79.135.206

# Measure latency (packet travel time)
ping 183.79.135.206 -c 20

# Repeat for a local server
nslookup www.uniroma1.it
ping <ip> -c 20
```

What do you observe? Why does this matter for **distributed consensus**?

---

# Information Asymmetry and Consensus

**Delay, packet loss, and network partitions** lead to:

<div class="box">

### :balance_scale: Information Asymmetry
Different nodes in a distributed network may observe **different states of the world** at any given moment. This makes agreeing on the correct ledger state genuinely hard.

</div>

This is why **consensus** — the process of reaching agreement among distributed, potentially unreliable nodes — is the central technical challenge of blockchain.

---

# Order of Events

In a distributed network, two conflicting transactions might arrive at different nodes in **different orders**:

- Node A sees: *Andrea → Maria* first, then *Andrea → Bob*
- Node B sees: *Andrea → Bob* first, then *Andrea → Maria*

**The double-spend problem**: if Andrea only has enough for one transaction, which one is valid?

The blockchain resolves this by establishing a **canonical order** of events through consensus.

---

# Ordering Events with Blocks

<div class="box">

### :chains: Finality
Once a transaction is added to the chain, it is **irreversible** and can no longer be altered or reversed.

</div>

- Pending transactions wait in a **mempool**
- Valid transactions are bundled into **blocks**
- Blocks are chained in order: Block 20 → Block 21 → Block 22 …
- Finality can be **deterministic** (e.g. BFT-based) or **probabilistic** (e.g. Bitcoin's Proof of Work)

<div class="source"><a href="https://marmelab.com/">Source: marmelab.com</a></div>

---

# Ipse Dixit — Silvio Micali (Algorand)

> "If the majority of the money is in honest hands, the system works."

When asked how he can guarantee that the majority of users will act benevolently, Micali replied:

> "If a society doesn't have an honest majority, it no longer exists. In our society, do we have criminals? Absolutely — but it's a relatively small percentage. If nobody follows our rules, there is no society."

This captures the **social contract** underlying permissionless blockchains.

---

# The Problem of Consensus

<div class="box">

### :question: Core Question
**How do we select which blocks are recorded in the blockchain, and in what order?**

This is the **consensus problem** — the hardest part of building a decentralized system.

</div>

Consensus must be:
- **Safe** — all honest nodes agree on the same chain
- **Live** — valid transactions eventually get confirmed
- **Fault-tolerant** — resistant to malicious or faulty nodes

---

# Validation vs Consensus

- **Validation**: A blockchain validator verifies that transactions are **legal** (e.g. you have enough coins). It checks consistency with the protocol — not whether the real-world data is genuine.

- **Consensus**: Determining the **ordering** of events in the blockchain — coming to agreement on that order.

<div class="box">

### :rotating_light: Key Distinction
Consensus = agreeing on the **ordering** of validated transactions → **fair selection of blocks** ← this is where attacks are possible.

</div>

<div class="source"><a href="https://businessandleaders.it/2019/02/27/blockchain-validation-vs-consensus/">businessandleaders.it</a></div>

---

# How Does a Transaction Get Into the Blockchain?

1. Transaction **request raised** by a node
2. Transaction **broadcast** on the P2P network
3. Transaction is **validated and verified** by nodes
4. Verified transaction is **added to a proposed block**
5. **Consensus** selects which block is appended to the chain
6. **Transaction complete** ✅

> ⚠️ Different nodes might have **different views** of the current chain state — this is why consensus is needed.

---

# How to Achieve Consensus

<div class="two-col">
<div>

### Human Algorithms
Democratic processes, voting, governance — humans reason about complex situations and reach agreement over time.

</div>
<div>

### Algorithms on a PC
Cryptographic protocols — deterministic rules executed by software on distributed nodes. Fast, but require careful design.

</div>
</div>

Blockchain uses **algorithms** to automate consensus — removing the need for human intermediaries in the loop.

---

# Consensus: A Brief History

Key milestones in the development of consensus algorithms:

- **1962** — Paul Baran: distributed communications networks
- **1979** — Byzantine Generals Problem published
- **1988** — Practical Byzantine Fault Tolerance (PBFT)
- **1997** — Proof of Work consensus first discussed (Adam Back)
- **1999** — Proof of Work developed
- **2008** — Bitcoin (Nakamoto consensus / PoW)
- **2012** — Proof of Stake developed
- **2015+** — Ethereum, Algorand, Hyperledger and many more

<div class="source"><a href="https://images.squarespace-cdn.com/content/v1/57cafc06893fc06c8c430b02/1477820612716-DK2V3UR1C2BPKJG49Z9L/image-asset.png">Source</a></div>

---

# Blockchain Trilemma

> **Vitalik Buterin** identified a fundamental trade-off in blockchain design:

Any blockchain can achieve at most **two of three** properties simultaneously:

- 🔒 **Security** — resistant to attacks
- 📈 **Scalability** — high throughput, low latency
- 🌐 **Decentralisation** — no central points of control

Most real-world blockchains make deliberate compromises among these three.

---

# Transaction Speeds: Crypto vs Traditional

| System | Transactions per Second |
|--------|------------------------|
| **Visa** | 24,000 |
| **Ripple** | 1,500 |
| **PayPal** | 193 |
| **Litecoin** | 56 |
| **Dash** | 48 |
| **Ethereum** | 20 |
| **Bitcoin** | 7 |

Scalability remains one of the biggest open challenges for public blockchains.

<div class="source"><a href="https://cdn.howmuch.net/articles/crypto-transactions-compared-ce3b.jpg">howmuch.net</a></div>

---

# Technologies of a Blockchain

<div class="two-col">
<div>

- <i class="fa-solid fa-filter"></i> **Hash Functions**
- <i class="fa-solid fa-key"></i> **Asymmetric Encryption**
- <i class="fa-solid fa-sitemap"></i> **Merkle Trees**
- <i class="fa-solid fa-database"></i> **Key-Value Databases**

</div>
<div>

- <i class="fa-solid fa-network-wired"></i> **P2P Communication Protocols**
- <i class="fa-solid fa-people-group"></i> **Consensus Algorithms**

</div>
</div>

All of these building blocks combine to produce a system that is distributed, immutable, and trust-minimized.

---

# Properties of Distributed Ledger Technology (DLT)

| Property | Description |
|----------|-------------|
| **Distributed** | All participants have a copy for complete transparency |
| **Immutable** | Validated records are irreversible and cannot be changed |
| **Time-stamped** | A transaction timestamp is recorded on each block |
| **Unanimous** | All network participants agree to the validity of records |
| **Anonymous** | Participant identity is anonymous or pseudonymous |
| **Secure** | All records are individually encrypted |
| **Programmable** | A blockchain is programmable (i.e. Smart Contracts) |

<div class="source">Euromoney Learning 2020</div>

---

# Censorship Resistance

<div class="box">

### :shield: A Core Property of Public Blockchains
Because no single party controls a permissionless blockchain, **no one can prevent a valid transaction from being included** in the ledger — provided the sender pays the required fees. This makes blockchain inherently resistant to censorship.

</div>

This property is especially valuable in:
- Jurisdictions with unstable financial systems
- Cross-border payments bypassing capital controls
- Applications requiring neutrality (e.g. public voting, supply chain)

<div class="source"><a href="https://news.bitcoin.com/deploying-censorship-resistance-to-uphold-decentralization/">news.bitcoin.com</a></div>

---

# DB vs Blockchain: CRUD → CRAB

Traditional databases use **CRUD**: Create, Read, Update, Delete.

Blockchain uses **CRAB**: Create, Read, Append, **Burn**.

<div class="box">

### :fire: What is "Burn"?
Deleting from a blockchain conflicts with immutability. Instead, assets are transferred to an **unspendable public key** (e.g. `BurnBurnBurn…`). The data is never deleted — only the keys controlling it are lost.

</div>

> The **data itself is never deleted** — only the keys to control the transfer of data are lost in a burn operation.

---

# Privacy and Blockchain

<div class="box">

### :eu: GDPR Tension
The European Parliament has studied whether distributed ledgers can be reconciled with the **General Data Protection Regulation (GDPR)**. Blockchain's immutability conflicts with the "right to be forgotten" — a core GDPR principle.

</div>

Key conflicts:
- **Right to erasure** vs **immutability**
- **Data minimization** vs **full transaction transparency**
- **Controller accountability** vs **decentralized governance**

---

# Blockchain for Sustainable Development Goals

Blockchain has been proposed as a tool for achieving all 17 UN SDGs:

- **No Poverty** — Efficient access to credit, financial traceability
- **Zero Hunger** — Traceable food production systems
- **Good Health** — Patients own their secured health data
- **Quality Education** — Verifiable education records
- **Reduced Inequality** — Financial inclusion, sharing economy
- **Climate Action** — Accountability for rapid decarbonization
- **Sustainable Cities** — Smart IoT management, peer-to-peer markets

> A rich narrative — but **in many cases still unmet** in practice.

<div class="source"><a href="https://www.intechopen.com/media/chapter/72069/media/F1.png">InTechOpen</a></div>

---

# Do We Need Blockchain?

A decision framework by **Wüst & Gervais**:

```
Do you need to store state?
├── No  → Don't use Blockchain
└── Yes → Are there multiple writers?
           ├── No  → Don't use Blockchain
           └── Yes → Can you use an always-online TTP?
                      ├── Yes → Don't use Blockchain
                      └── No  → Are all writers known?
                                 ├── No  → Permissionless Blockchain
                                 └── Yes → Are all writers trusted?
                                            ├── Yes → Is public verifiability required?
                                            │          ├── Yes → Public Permissioned Blockchain
                                            │          └── No  → Private Permissioned Blockchain
                                            └── No  → Public Permissioned Blockchain
```

<div class="source"><a href="https://eprint.iacr.org/2017/375.pdf">Wüst & Gervais, 2017</a></div>

---

# Current Situation (Italy Focus)

Three main application areas, with varying maturity:

😊 **Internet of Value**
Cryptocoins, stablecoins, and Central Bank Digital Currency (CBDC) — actively growing.

😐 **Blockchain for Business**
Impact of blockchain technologies and tokenization on business ecosystems — promising but uneven.

😞 **Decentralized Web (Web3)**
Still emerging; widespread adoption lags behind the narrative.

<div class="source"><a href="https://www.osservatori.net/blockchain-web3/">osservatori.net</a> | <a href="https://charts.bitbo.io/price/">Bitcoin price history</a></div>

---

# Blockchain Evolution: Web3 Era (2016–2018+)

Following the history of blockchain:

| Year | Event |
|------|-------|
| 2016 | EOS unveiled as new Blockchain protocol for decentralized apps |
| 2016 | R3 consortium formed (40+ legacy financial companies) |
| 2016 | Bug in Ethereum DAO code exploited and attacked |
| 2017 | Linux Foundation unveils Hyperledger |
| 2018+ | Web 3.0 architecture emerges |

<div class="source"><a href="https://intellipaat.com/blog/wp-content/uploads/2022/02/History-of-Blockchain-Technology.jpg">Intellipaat</a></div>

---

# Ethereum: State Transition System

Ethereum can be seen as a **world computer** — a P2P consensus-based state machine:

- **State** — current status of all Ethereum accounts (each with nonce, ETH balance, contract code, storage)
- **Transaction** — core cryptocurrency functionality + optional data field accessible by smart contracts
- **State Transition Function** — applies a transaction to the current state, progressing the EVM; capable of processing arbitrary code

```
State  +  Transaction  →  State Transition Function  →  State'
```

<div class="source"><a href="https://inevitableeth.com/home/ethereum/evm/state-machine">inevitableeth.com</a></div>

---

# Smart Contracts

<div class="two-col">
<div>

```solidity
pragma solidity >=0.7.0 <0.9.0;

contract Storage {
  uint256 number;

  function store(uint256 num) public {
    number = num;
  }

  function retrieve() public view
    returns (uint256) {
    return number;
  }
}
```

</div>
<div>

Computer programs that:
- Encode **agreements, policies, rules and penalties**
- **Cannot be arbitrarily altered** once deployed
- **Autonomously run** on the blockchain
- **Transfer digital assets** between parties

Try it: [remix.ethereum.org](https://remix.ethereum.org/)

</div>
</div>

<div class="source"><a href="https://etherscan.io/contractsVerified">etherscan.io/contractsVerified</a></div>

---

# The "World Computer": Web3

<div class="box">

### :globe_with_meridians: From App to DApp
In Web3, the traditional backend (server + database) is **replaced** by smart contracts running on the Ethereum Virtual Machine (EVM), with decentralized storage (IPFS/Swarm) and a cryptographic signer (MetaMask) replacing the login system.

</div>

Architecture: Browser → Provider (Alchemy, Infura…) → EVM → Smart Contracts + IPFS

<div class="source"><a href="https://www.preethikasireddy.com/post/the-architecture-of-a-web-3-0-application">preethikasireddy.com</a></div>

---

# Oracles: Bridging On-Chain and Off-Chain

<div class="box">

### :crystal_ball: The Oracle Problem
Blockchain smart contracts are **deterministic** — they cannot access external data directly, because different nodes might observe different real-world values at different times.

</div>

**Oracles** solve this by:
1. Smart contract requests external data
2. Oracle queries the real-world source (e.g. a sensor, API)
3. Oracle submits the data as a **blockchain transaction**
4. The data becomes part of the immutable ledger
5. All nodes process it **deterministically**

<div class="source"><a href="https://assets-global.website-files.com/5f6b7190899f41fb70882d08/6148588af8ce998ca21d8db8_Blockchain%20Oracle%20Problem.jpg">Chainlink</a></div>

---

# Can I Prove That What Is On-Chain Is True?

**Very simply … no, you cannot!**

The blockchain guarantees:
- ✅ That data has **not been tampered with** after recording
- ✅ That transactions follow the **protocol rules**
- ✅ That the **order** of transactions is agreed upon

The blockchain does **not** guarantee:
- ❌ That the **real-world data entered was accurate**
- ❌ That the **off-chain assets** correspond to on-chain tokens

> But remember: **when you cheat, it is there forever**. Your reputation — and the evidence — is permanently on-chain.

---

# Personal Opinion — On Asset Creation

<div class="box">

### :thought_balloon: Andrea Vitaletti
*"I have no problem in dealing with assets that are **created by trusted entities** (i.e. centralised), provided that their **management is fully decentralised**."*

</div>

**Self-Sovereign Identity (SSI)** is a good example:
- Identity credentials are issued by trusted authorities (governments, universities)
- But their management and presentation is controlled by the user, without intermediaries

---

# Personal Opinion — On Transparency

<div class="box">

### :thought_balloon: Andrea Vitaletti
*"Blockchain (public/permissionless) is undoubtedly superior when **transparency is a requirement**."*

</div>

Use cases where transparency is non-negotiable:
- Public procurement and government spending
- Supply chain traceability for consumers
- Decentralized voting systems
- Open financial protocols (DeFi)

---

# Thank You!

### Questions?

<i class="fa-solid fa-at"></i> vitaletti@diag.uniroma1.it  
<i class="fa-brands fa-github"></i> [https://andreavitaletti.github.io/BC/](https://andreavitaletti.github.io/BC/)

**Further reading:**
- [https://arxiv.org/pdf/2501.15962](https://arxiv.org/pdf/2501.15962)
- [https://eprint.iacr.org/2017/375.pdf](https://eprint.iacr.org/2017/375.pdf) — Wüst & Gervais: Do you need a blockchain?
- [https://inevitableeth.com](https://inevitableeth.com) — Ethereum architecture deep dives

---

# Image & Content Sources

- Slides 1–2: Sapienza University of Rome / Andrea Vitaletti
- Blockchain history timeline: [intellipaat.com](https://intellipaat.com/blog/wp-content/uploads/2022/02/History-of-Blockchain-Technology.jpg)
- Bitcoin transaction example: [blockchain.com](https://www.blockchain.com/explorer)
- Evolution of money: [dreamstime.com](https://thumbs.dreamstime.com/b/evolution-money-concept-set-abstract-diagram-describing-years-particular-measure-was-used-vector-illustration-222996275.jpg)
- Networking diagram: [NIST IR 8202](https://nvlpubs.nist.gov/nistpubs/ir/2018/NIST.IR.8202.pdf)
- DLT Properties: Euromoney Learning 2020
- Consensus history: [squarespace-cdn.com](https://images.squarespace-cdn.com/content/v1/57cafc06893fc06c8c430b02/1477820612716-DK2V3UR1C2BPKJG49Z9L/image-asset.png)
- Transaction speeds: [howmuch.net](https://cdn.howmuch.net/articles/crypto-transactions-compared-ce3b.jpg)
- Do you need blockchain?: [Wüst & Gervais 2017](https://eprint.iacr.org/2017/375.pdf)
- Ethereum state machine: [inevitableeth.com](https://inevitableeth.com/home/ethereum/evm/state-machine)
- Web3 architecture: [preethikasireddy.com](https://www.preethikasireddy.com/post/the-architecture-of-a-web-3-0-application)
- Blockchain for SDGs: [intechopen.com](https://www.intechopen.com/media/chapter/72069/media/F1.png)
- Censorship resistance: [news.bitcoin.com](https://news.bitcoin.com/deploying-censorship-resistance-to-uphold-decentralization/)
