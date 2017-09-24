





# Factom and Tierion: Securing Business Processes on the Blockchain

Aside from serving as a ledger for financial transactions, securing data through timestamping and hashing is one of the most tangible and easy to understand applications of blockchain technology. Things like land registries, titles, patents, audits and inspections all rely on having a trusted source of record keeping. By applying a cryptographic hash function to a document, then recording it to the Bitcoin blockchain, one can verify that the document existed at a certain point in time.

However, there are a few problems that make large-scale use of a Bitcoin-based record system impractical. Using a transaction to record the hash of a single document is wasteful and becomes more so as Bitcoin fees increase. Additionally, Bitcoin's 10-minute block creation time acts as a bottleneck on throughput. Essentially, any system seeking to use Bitcoin as a distributed audit log or notary system will be subject to the same scaling issues faced by Bitcoin itself.

Both projects discussed here, Tierion and Factom seek to alleviate these issues by 

1) Providing a protocol for accepting data from users, formatting it, and securing the data until it can be persisted on the Bitcoin blockchain in a single batch, saving on fees and decreasing throughput.
2) Incentivizing individuals to operate the infrastructure carrying out #1 while maintaining security.

In light of the increasingly common revelations of corporate accounting scandals and falsification of records, such a system would seem to solve a salient need. Technologically speaking, it is also low-hanging fruit since it's only a minor adaptation of Bitcoin's current use as a financial ledger. Projects that attempt to serve this need and solve the remaining problems mentioned above have a high likelihood of success and deserve attention.


## Factom

Factom is a decentralized protocol that makes the process of recording business records onto the Bitcoin blockchain more efficient. Potential use cases are numerous, but essentially any business process that benefits from immutable, auditable record keeping would be candidates. Currently, the Factom Inc. website lists two products:

#### Factom Harmony
Built to secure and verify documents associated with various processes involved in the creation and administration of mortgage loans.

#### dLoc
dLoc is a partnership with RFID technology company SmartTrac. The dLoc product combines RFID tags with data persisted via Factom to augment and authenticate physical documents and records like medical charts or birth certificates.

In addition to the use cases on display in the above-mentioned products, Factom has also received a grant from the US Department of Homeland Security to develop solutions for securing IOT devices like cameras and other sensors being used by the agency to monitor US borders.

### Technical Overview
Bitcoin offers several ways to encode data into transactions or block headers and any application can utilize this as a place to store arbitrary data. Factom acts as an extra protocol layer on top of the Bitcoin blockchain. 

Factom's group of Federated Servers are tasked with receiving data sent by client applications, organizing the data and producing a Merkle-tree based data structure, then recording it onto a Bitcoin block every 10 minutes. Because of this, Factom relies on the consensus of the Factom servers for up to 10 minutes (prior to submitting the BTC network) then on the integrity of Bitcoin from then on.

Currently, Factom operates Federated servers centrally, but their roadmap specifies that this will be opened to the community. In order to incentivize Factom servers to build blocks and write them to the Bitcoin blockchain, it has developed a two-token system. Applications wishing to record data via the Factom network must pay for the right to record the data by purchasing 'Entry Credits'. Entry credits can be purchased directly with Factoids, the native token of the Factom network or indirectly through the Factom Foundation.

Having two tokens allows keep the price of network usage stable and isolated from the volatility that cryptocurrencies are often criticized for. While Factoids are a free-floating, openly transactable cryptocurrency, Entry Credits cannot be sent to other addresses and once created, can only be used to write data. The Factom protocol dynamically adjusts the Factoid-Entry Credit exchange rate to maintain a rough USD peg of $0.001.


### Prospects for Adoption

Factom is best suited to applications where access to records is required across organization boundaries, as is the case with medical records or an individual's credit record. The actual data need not be stored directly with Factom to gain advantages from it. Instead, Factom can (and is more suited to) use as a sort of index for other files. Factom would store a hash of a given record and perhaps a pointer to a location to retrieve the file (IPFS, cloud storage, etc.). This allows for parties to verify the existence and handling of files while maintaining privacy.

As a technology aiming for adoption primarily by large enterprises, Factom will face the same objections seen by other public blockchain projects because it records data publicly, on the Bitcoin blockchain. This is in contrast to private blockchain technologies like Hyperledger that are currently seeing trials in many organizations.

Factom is even more likely to find itself compared to traditional DBMS currently used by large organizations. Where the cost of operations, or read/write speed is concerned, Factom and most other blockchain technologies are currently primitive compared to open and closed source DBMS. Where traits such as auditability or guaranteed long-term immutable storage are valued, Factom becomes much more attractive.

It seems that Factom's ability to win out against private blockchains and traditional DBMS will require the company to clearly communicate its advantages to CIOs and CTOs. Adoption will be contingent on it finding a use case with benefits that outweigh concerns regarding public blockchain technology. In short, Factom's marketing and sales organizations may be as important, if not more than the engineering organization in driving adoption.

### Potential Issues and Risk Factors

#### Reliance on Bitcoin Blockchain 
Factom records data on the Bitcoin blockchain and is heavily dependent on its continued, secure operation. Generalizing or otherwise adapting the Factom protocol so that it can use other ledgers as a persistence layer would be a good way to de-risk this. There is some evidence that the Factom team plans to begin persisting data to the Ethereum blockchain as well but to my knowledge, other blockchains are not supported at this time.

#### Price
8,745,089 of the 8,753,219 created Factoids are still in existence. Since anyone wishing to use Factom to record data must directly or indirectly convert Factoids to Entry Credits - burning some Factoids in the process, it seems obvious that the price would go up with increased usage. However, as with most cryptocurrencies, the current price is not driven by usage but rather by speculation. According to the Factom website, 10,189,635 entries have been recorded on the Factom blockchain, burning 8,130 Factoids (8,753,219 - 8,745,089). Since the Factom protocol attempts to keep the price of writing data fixed at roughly $0.001, the total cost to record that data should have been roughly $10,189 or $1.25 per Factoid burned. In order for the current FCT price to reflect actual usage, we would expect the number of current entries to be more than 14x greater. Any investor looking to take a position in FCT would be wise to incorporate this into their plans.

#### Trust
The point of creating a system on top of Bitcoin is to increase capacity by consolidating the data, requiring fewer expensive and slow transactions with the Bitcoin blockchain. The problem now is that we have to trust Factom as well as the Bitcoin blockchain. In Factom, there are two types of servers, Federated servers which are tasked with writing data to the blockchain, and Audit servers which audit Entries. Whether a server is acting as an Auditor or a Federated server is determined by the server rank. The ranking is done every 4 hours and is a function of user votes, weighted according to the user's past use of the system. Votes from users that have written larger amounts of more recent Entries will be given higher weighting. If a single entity owns the most highly ranked servers at once, they would be voted in as Federated servers and would have a chance to control what is written to the blockchain. Factom argues that misbehavior would be noticed by the network and the offending servers would be voted out. However, this still leaves the possibility that heavily weighted users could conspire with server operators to influence the network. It's unclear if such an attack would be economically feasible but it should be further investigated.

## Tierion

### Market
Tieron is a decentralized system with an ERC-20 token (TNT) that is used to secure data on the blockchain for the purposes of verifying, timestamping, and auditing it. This makes it the closest competitor to Factom that I've been able to find. As such, the potential use cases are similar. Any business process that requires read or write access to data be shared across organization boundaries, where the level of trust is lower. Tierion (and Factom) are intended to improve the transparency and auditability of business processes in a wide range of industries.

### Technical Overview

The basic functionality of Tierion (and Factom), recording hashed data into a public blockchain is already easily accomplished with minimal additional infrastructure. Both projects were intended to improve the efficiency and cost-effectiveness of doing so. Tierion takes a similar approach to Factom by maintaining its own blockchain of hashes of data, which it calls the Global Calender. This blockchain of hashed data is then "anchored" to both the Bitcoin and Ethereum blockchains. Tierion refers to this protocol as Chainpoint, and they have actually offered it as a centralized service for several years. 

In an attempt to make Chainpoint a less-centralized product Tierion has added an additional type of server to their system, so now the architecture consists of two components; Core and Nodes. The servers that comprise Core are centrally operated by Tierion and their partners to maintain the Global Calendar and interact with the blockchains. The Nodes are decentralized servers that can be run by anyone, and act as mirrors of the Global Calendar and host an API which client apps use to interact with the Tierion system. Nodes benefit the protocol by providing redundancy and additional capacity to the network but actually don't change the trust model. To use Tierion, you still must place trust in the partners running the Core.

With the addition of Nodes, Tierion has also introduced an ERC-20 token, called TNT. According to Tierion documentation, TNT exists to pay Node operators for their service. However, they are not compensated directly. Node operators must pay a set number of TNT to be eligible for a 'lottery' that is periodically held amongst the nodes and pays out in TNT. TNT is also not needed by the end-users of the Tierion network, the clients that wish to record proof on the blockchain must use fiat to purchase access as in the previous SaaS version.


### Prospects for Adoption
The need for and potential use cases for an immutable, cryptographically secure proof of records amongst businesses and government is easy to understand. This is what is driving much of the interest in blockchains from enterprises. As with Factom, it's unclear if businesses will value the benefits of public blockchains enough to prefer them over traditional DBMS or even permissioned ledgers. The fact that Tierion maintains centralized control over the Core servers is disconcerting to proponents of fully-decentralized systems but it might make enterprise users more comfortable. Also, Microsoft's seeming involvement in the project may carry weight amongst Tierion's potential customers. 

### Potential Issues and Risk Factors

#### Purpose of Token
It's not entirely clear how necessary the TNT token is to the success of the system. Users do not need to purchase it in order to use Tierion but instead pay Tierion directly via fiat. TNT is used to incentivize Node operators by being periodically distributed to a randomly selected Node. In the ICO whitepaper, there is mention of Tierion adding additional services which will make use of the TNT token. Perhaps they hope to transition away from a centralized system so Tierion users will eventually pay Node operators directly via TNT. However, none of their plans are clearly laid out so it's difficult to understand how the token should be valued.

#### Centralization
Tierion currently operates the Core servers on their network, supposedly in partnership with Microsoft. While currently the same is true of Factom, Factom's development roadmap lays out a timeline for transition to a fully decentralized system. Currently, Tierion looks more like a semi-decentralized service, operated by a traditional company but making use of decentralized infrastructure (Tierion Nodes and the Ethereum/Bitcoin blockchains).


## Summary
Factom and Tierion are both projects that have been created to efficiently record hashes of business data on public blockchains. They accomplish this by introducing their own tokens and networks of servers to consolidate and secure the data and record the data to either the Bitcoin or Ethereum blockchain.

Factom is currently operating in a temporarily centralized state but is designed to be fully-decentralized and has a clear roadmap to get there. They have developed a clever 2-token system to stabilize the price of recording data via Factom. Tierion has operated their Chainpoint protocol for recording hashed data onto the blockchain as a centralized service since 2015. They recently held an ICO for their TNT token and are attempting to transition to a decentralized infrastructure, but there are still some large, unanswered questions about how they plan to get there. Both projects are attempting to solve a clearly-defined business problem and the basic building blocks of their projects are already in use and relatively well-understood. This means the bulk of their challenges lie in convincing their potential users in the enterprise to adopt the technology. If I had to choose one project to invest in I would choose Factom. The investment case for the Factoid token is much clearer at this stage and the team has a roadmap for decentralizing their system. Tierion could very well end up being a more successful business than Factom, but it's not obvious how important the TNT token will be to this success.

