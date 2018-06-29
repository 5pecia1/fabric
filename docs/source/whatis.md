# 소개

일반적으로 블록체인은 _피어 노드(peer node)_들의 분산 네트워크로 유지되는 
불변의 트랜잭션(transaction) 원장입니다. 이 노드들은 이전의 블록에 각각의 
블록을 바인딩 하는 해시를 포함하는 그룹화된 _합의 프로토콜_에 의해 인증된 
트랜잭션들을 사용함으로써 각각 원장의 복사본을 관리합니다.

첫 번째이자 가장 널리 알려진 블록체인의 활용 사례는 다른 사람들도 그 발자취를 
따라가고 있는  [비트코인](https://en.wikipedia.org/wiki/Bitcoin) 가상화폐입니다.
대안 가상화폐인 이더리움은 비트코인과 같은 특징들을 많이 통합하지만, 그와 더불어
분산 애플리케이션을 위한 플랫폼을 만들기 위해 _스마트 컨트랙트_를 추가한 
다른 접근 방식을 취했습니다. 비트코인과 이더리움은 퍼블릭 무허가형
블록체인(public permissionless blockchain) 기술이라고 분류됩니다. 기본적으로, 
이들은 누구에게나 열려있고 참여자들이 익명으로 소통할 수 있는 퍼블릭 
네트워크입니다. 

비트코인의 인기로 이더리움과 다른 파생된 기술들도 발전되었고, 블록체인의 토대를
이루는 기술사용에 대한 관심과, 분산 원장과 분산 애플리케이션 플랫폼을 더 
혁신적인 _엔터프라이즈_ 사용 사례들에 활용하는 것에 대한 관심도 높아졌습니다. 
하지만 많은 엔터프라이즈 사용 사례들은 _무허가형 블록체인
(permissionless blockchain)_ 기술들이 현재로서는 전달할 수 없는 성능 특성을
(performance characteristics) 요구합니다. 게다가 Know-Your-Customer(KYC)와
 Anti-Money Laundering(AML) 규칙들을 따라야 하는 많은 금융 거래들과 같은 
 사용 사례들에서는 참여자들의 신원을 요구하는 것은 어렵습니다. 

엔터프라이즈 용도로는 우리는 다음과 같은 요구사항들을 고려해야 합니다.

- 참여자들은 신원이 확인 되어야만 하거나 확인될 수 있어야 합니다
- 네트워크들은 _허가받아져야만_ 합니다
- 높은 트랜잭션(high transaction) 처리를 할 수 있는 성능이 있어야 합니다
- 트랜잭션을 확인하는 데 걸리는 시간이 짧아야 합니다
- 프라이버시 트랜잭션과 비즈니스 트랜잭션이 관련된 데이터의 기밀성이 있어야 
합니다

초기의 블록체인 플랫폼들이 현재 엔터프라이즈 용도에 맞게 _맞춰지는 것에_ 반해,
 Hyperledger Fabric은 시작부터 엔터프라이즈 용도로 _디자인되었습니다_. 
뒤에 나올 부분들이 어떻게 Hyperledger Fabric이 다른 블록체인 플랫폼들과 
차별화하는지 그리고 그 아키텍처 결정에 대한 동기 중 몇몇을 설명할 것입니다.

## Hyperledger Fabric

Hyperledger Fabric is an open source enterprise-grade permissioned distributed
ledger technology (DLT) platform, designed for use in enterprise contexts,
that delivers some key differentiating capabilities over other popular
distributed ledger or blockchain platforms.

One key point of differentiation is that Hyperledger was established under the
Linux Foundation, which itself has a long and very successful history of
nurturing open source projects under **open governance** that grow strong
sustaining communities and thriving ecosystems. Hyperledger is governed by a
diverse technical steering committee, and the Hyperledger Fabric project by a
diverse set of maintainers from multiple organizations. It has a development
community that has grown to over 35 organizations and nearly 200 developers
since its earliest commits.

Fabric has a highly **modular** and **configurable** architecture, enabling
innovation, versatility and optimization for a broad range of industry use cases
including banking, finance, insurance, healthcare, human resources, supply
chain and even digital music delivery.

Fabric is the first distributed ledger platform to support **smart contracts
authored in general-purpose programming languages** such as Java, Go and
Node.js, rather than constrained domain-specific languages (DSL). This means
that most enterprises already have the skill set needed to develop smart
contracts, and no additional training to learn a new language or DSL is needed.

The Fabric platform is also **permissioned**, meaning that, unlike with a public
permissionless network, the participants are known to each other, rather than
anonymous and therefore fully untrusted. This means that while the participants
may not _fully_ trust one another (they may, for example, be competitors in the
same industry), a network can be operated under a governance model that is built
off of what trust _does_ exist between participants, such as a legal agreement
or framework for handling disputes.

One of the most important of the platform's differentiators is its support for
**pluggable consensus protocols** that enable the platform to be more
effectively customized to fit particular use cases and trust models. For
instance, when deployed within a single enterprise, or operated by a trusted
authority, fully byzantine fault tolerant consensus might be considered
unnecessary and an excessive drag on performance and throughput. In situations
such as that, a
[crash fault-tolerant](https://en.wikipedia.org/wiki/Fault_tolerance) (CFT)
consensus protocol might be more than adequate whereas, in a multi-party,
decentralized use case, a more traditional
[byzantine fault tolerant](https://en.wikipedia.org/wiki/Byzantine_fault_tolerance)
(BFT) consensus protocol might be required.

Fabric can leverage consensus protocols that **do not require a native
cryptocurrency** to incent costly mining or to fuel smart contract execution.
Avoidance of a cryptocurrency reduces some significant risk/attack vectors,
and absence of cryptographic mining operations means that the platform can be
deployed with roughly the same operational cost as any other distributed system.

The combination of these differentiating design features makes Fabric one of
the **better performing platforms** available today both in terms of transaction
processing and transaction confirmation latency, and it enables **privacy and confidentiality** of transactions and the smart contracts (what Fabric calls
  "chaincode") that implement them.

Let's explore these differentiating features in more detail.

## Modularity

Hyperledger Fabric has been specifically architected to have a modular
architecture. Whether it is pluggable consensus, pluggable identity management
protocols such as LDAP or OpenID Connect, key management protocols or
cryptographic libraries, the platform has been designed at its core to be
configured to meet the diversity of enterprise use case requirements.

At a high level, Fabric is comprised of the following modular components:

- A pluggable _ordering service_ establishes consensus on the order of
transactions and then broadcasts blocks to peers.
- A pluggable _membership service provider_ is responsible for associating
entities in the network with cryptographic identities.
- An optional _peer-to-peer gossip service_ disseminates the blocks output by
ordering service to other peers.
- Smart contracts ("chaincode") run within a container environment (e.g. Docker)
for isolation. They can be written in standard programming languages but do not
have direct access to the ledger state.
- The ledger can be configured to support a variety of DBMSs.
- A pluggable endorsement and validation policy enforcement that can be
independently configured per application.

There is fair agreement in the industry that there is no "one blockchain to
rule them all". Hyperledger Fabric can be configured in multiple ways to
satisfy the diverse solution requirements for multiple industry use cases.

## Permissioned vs Permissionless Blockchains

In a permissionless blockchain, virtually anyone can participate, and every
participant is anonymous. In such a context, there can be no trust other than
that the state of the blockchain, prior to a certain depth, is immutable. In
order to mitigate this absence of trust, permissionless blockchains typically
employ a "mined" native cryptocurrency or transaction fees to provide economic
incentive to offset the extraordinary costs of participating in a form of
byzantine fault tolerant consensus based on "proof of work" (PoW).

**Permissioned** blockchains, on the other hand, operate a blockchain amongst
a set of known, identified and often vetted participants operating under a
governance model that yields a certain degree of trust. A permissioned
blockchain provides a way to secure the interactions among a group of entities
that have a common goal but which may not fully trust each other. By relying on
the identities of the participants, a permissioned blockchain can use more
traditional crash fault tolerant (CFT) or byzantine fault tolerant (BFT)
consensus protocols that do not require costly mining.

Additionally, in such a permissioned context, the risk of a participant
intentionally introducing malicious code through a smart contract is diminished.
First, the participants are known to one another and all actions, whether
submitting application transactions, modifying the configuration of the network
or deploying a smart contract are recorded on the blockchain following an
endorsement policy that was established for the network and relevant transaction
type. Rather than being completely anonymous, the guilty party can be easily
identified and the incident handled in accordance with the terms of the
governance model.

## Smart Contracts

A smart contract, or what Fabric calls "chaincode", functions as a trusted
distributed application that gains its security/trust from the blockchain and
the underlying consensus among the peers. It is the business logic of a
blockchain application.

There are three key points that apply to smart contracts, especially when
applied to a platform:

- many smart contracts run concurrently in the network,
- they may be deployed dynamically (in many cases by anyone), and
- application code should be treated as untrusted, potentially even
malicious.

Most existing smart-contract capable blockchain platforms follow an
**order-execute** architecture in which the consensus protocol:

- validates and orders transactions then propagates them to all peer nodes,
- each peer then executes the transactions sequentially.

The order-execute architecture can be found in virtually all existing blockchain
systems, ranging from public/permissionless platforms such as
[Ethereum](https://ethereum.org/) (with PoW-based consensus) to permissioned
platforms such as [Tendermint](http://tendermint.com/),
[Chain](http://chain.com/), and [Quorum](http://www.jpmorgan.com/global/Quorum).

Smart contracts executing in a blockchain that operates with the order-execute
architecture must be deterministic; otherwise, consensus might never be reached.
To address the non-determinism issue, many platforms require that the smart
contracts be written in a non-standard, or domain-specific language
(such as [Solidity](https://solidity.readthedocs.io/en/v0.4.23/)) so that
non-deterministic operations can be eliminated. This hinders wide-spread
adoption because it requires developers writing smart contracts to learn a new
language and may lead to programming errors.

Further, since all transactions are executed sequentially by all nodes,
performance and scale is limited. The fact that the smart contract code executes
on every node in the system demands that complex measures be taken to protect
the overall system from potentially malicious contracts in order to ensure
resiliency of the overall system.

## A New Approach

Fabric introduces a new architecture for transactions that we call
**execute-order-validate**. It addresses the resiliency, flexibility,
scalability, performance and confidentiality challenges faced by the
order-execute model by separating the transaction flow into three steps:

- _execute_ a transaction and check its correctness, thereby endorsing it,
- _order_ transactions via a (pluggable) consensus protocol, and
- _validate_ transactions against an application-specific endorsement policy
before committing them to the ledger

This design departs radically from the order-execute paradigm in that Fabric
executes transactions before reaching final agreement on their order.

In Fabric, an application-specific endorsement policy specifies which peer
nodes, or how many of them, need to vouch for the correct execution of a given
smart contract. Thus, each transaction need only be executed (endorsed) by the
subset of the peer nodes necessary to satisfy the transaction's endorsement
policy. This allows for parallel execution increasing overall performance and
scale of the system. This first phase also **eliminates any non-determinism**,
as inconsistent results can be filtered out before ordering.

Because we have eliminated non-determinism, Fabric is the first blockchain
technology that **enables use of standard programming languages**. In the 1.1.0
release, smart contracts can be written in either Go or Node.js, while there are
plans to support other popular languages including Java in subsequent releases.

## Privacy and Confidentiality

As we have discussed, in a public, permissionless blockchain network that
leverages PoW for its consensus model, transactions are executed on every node.
This means that neither can there be confidentiality of the contracts
themselves, nor of the transaction data that they process. Every transaction,
and the code that implements it, is visible to every node in the network. In
this case, we have traded confidentiality of contract and data for byzantine
fault tolerant consensus delivered by PoW.

This lack of confidentiality can be problematic for many business/enterprise use
cases. For example, in a network of supply-chain partners, some consumers might
be given preferred rates as a means of either solidifying a relationship, or
promoting additional sales. If every participant can see every contract and
transaction, it becomes impossible to maintain such business relationships in a
completely transparent network -- everyone will want the preferred rates!

As a second example, consider the securities industry, where a trader building
a position (or disposing of one) would not want her competitors to know of this,
or else they will seek to get in on the game, weakening the trader's gambit.

In order to address the lack of privacy and confidentiality for purposes of
delivering on enterprise use case requirements, blockchain platforms have
adopted a variety of approaches. All have their trade-offs.

Encrypting data is one approach to providing confidentiality; however, in a
permissionless network leveraging PoW for its consensus, the encrypted data is
sitting on every node. Given enough time and computational resource, the
encryption could be broken. For many enterprise use cases, the risk that their
information could become compromised is unacceptable.

Zero knowledge proofs (ZKP) are another area of research being explored to
address this problem, the trade-off here being that, presently, computing a ZKP
requires considerable time and computational resources. Hence, the trade-off in
this case is performance for confidentiality.

In a permissioned context that can leverage alternate forms of consensus, one
might explore approaches that restrict the distribution of confidential
information exclusively to authorized nodes.

Hyperledger Fabric, being a permissioned platform, enables confidentiality
through its channel architecture. Basically, participants on a Fabric network
can establish a "channel" between the subset of participants that should be
granted visibility to a particular set of transactions. Think of this as a
network overlay. Thus, only those nodes that participate in a channel have
access to the smart contract (chaincode) and data transacted, preserving the
privacy and confidentiality of both.

To improve upon its privacy and confidentiality capabilities, Fabric has
added support for [private data](./private-data/private-data.html) and is working
on zero knowledge proofs (ZKP) available in the future. More on this as it
becomes available.

## Pluggable Consensus

The ordering of transactions is delegated to a modular component for consensus
that is logically decoupled from the peers that execute transactions and
maintain the ledger. Specifically, the ordering service. Since consensus is
modular, its implementation can be tailored to the trust assumption of a
particular deployment or solution. This modular architecture allows the platform
to rely on well-established toolkits for CFT (crash fault-tolerant) or BFT
(byzantine fault-tolerant) ordering.

In the currently available releases, Fabric offers a CFT ordering service
implemented with [Kafka](https://kafka.apache.org/) and
[Zookeeper](https://zookeeper.apache.org/). In subsequent releases, Fabric will
deliver a [Raft consensus ordering service](https://raft.github.io/) implemented
with etcd/Raft and a fully decentralized BFT ordering service.

Note also that these are not mutually exclusive. A Fabric network can have
multiple ordering services supporting different applications or application
requirements.

## Performance and Scalability

Performance of a blockchain platform can be affected by many variables such as
transaction size, block size, network size, as well as limits of the hardware,
etc. The Hyperledger community is currently developing [a draft set of measures](https://docs.google.com/document/d/1DQ6PqoeIH0pCNJSEYiw7JVbExDvWh_ZRVhWkuioG4k0/edit#heading=h.t3gztry2ja8i) within the Performance and Scale working group, along
with a corresponding implementation of a benchmarking framework called
[Hyperledger Caliper](https://wiki.hyperledger.org/projects/caliper).

While that work continues to be developed and should be seen as a definitive
measure of blockchain platform performance and scale characteristics, a team
from IBM Research has published a
[peer reviewed paper](https://arxiv.org/abs/1801.10228v1) that evaluated the
architecture and performance of Hyperledger Fabric. The paper offers an in-depth
discussion of the architecture of Fabric and then reports on the team's
performance evaluation of the platform using a preliminary release of
Hyperledger Fabric v1.1.

The benchmarking efforts that the research team did yielded a significant
number of performance improvements for the Fabric v1.1.0 release that more than
doubled the overall performance of the platform from the v1.0.0 release levels.

## Conclusion

Any serious evaluation of blockchain platforms should include Hyperledger Fabric
in its short list.

Combined, the differentiating capabilities of Fabric make it a highly scalable
system for permissioned blockchains supporting flexible trust assumptions that
enable the platform to support a wide range of industry use cases ranging from
government, to finance, to supply-chain logistics, to healthcare and so much
more.

More importantly, Hyperledger Fabric is the most active of the (currently) ten
Hyperledger projects. The community building around the platform is growing
steadily, and the innovation delivered with each successive release far
out-paces any of the other enterprise blockchain platforms.

## Acknowledgement

The preceding is derived from the peer reviewed
["Hyperledger Fabric: A Distributed Operating System for Permissioned Blockchains"](https://arxiv.org/abs/1801.10228v1) - Elli Androulaki, Artem
Barger, Vita Bortnikov, Christian Cachin, Konstantinos Christidis, Angelo De
Caro, David Enyeart, Christopher Ferris, Gennady Laventman, Yacov Manevich,
Srinivasan Muralidharan, Chet Murthy, Binh Nguyen, Manish Sethi, Gari Singh,
Keith Smith, Alessandro Sorniotti, Chrysoula Stathakopoulou, Marko Vukolic,
Sharon Weed Cocco, Jason Yellick
