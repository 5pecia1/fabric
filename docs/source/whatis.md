# 소개

일반적으로 블록체인은 _피어 노드(peer node)_들의 분산 네트워크로 유지되는 
불변의 트랜잭션(transaction) 원장입니다. 이 노드들은 이전의 블록에 각각의 
블록을 바인딩 하는 해시를 포함하는 그룹화된 _합의 프로토콜_에 의해 인증된 
트랜잭션들을 사용함으로써 각각 원장의 복사본을 관리합니다.

첫 번째이자 가장 널리 알려진 블록체인의 활용 사례는 다른 사람들도 그 발자취를 
따라가고 있는  [비트코인](https://en.wikipedia.org/wiki/Bitcoin) 암호화폐입니다.
대안 암호화폐인 이더리움은 비트코인과 같은 특징들을 많이 통합하지만, 그와 더불어
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

## 하이퍼레저 패브릭

Hyperledger Fabric은 엔터프라이즈 컨텍스트에서 사용할 수 있게 디자인된, 
오픈소스 엔터프라이즈 수준의 허가형(permissioned) 분산 원장 기술(distributed 
ledger technology, DLT) 플랫폼으로, 다른 유명한 분산 원장 또는 
블록체인 플랫폼과 비교하여 차별화된 핵심 능력들을 제공합니다.

차별화된 핵심적인 특징 중 하나는 Hyperledger는 끈끈하게 유지되는 커뮤니티들과
번성하는 생태계를 자라게 하는 **오픈 거버넌스** 밑에서 오픈소스 프로젝트들을 
양성하는데 있어 길고 굉장히 성공적인 역사를 가지고 있는 Linux Foundation 
산하에서 설립되었다는 점입니다. Hyperledger는 다양한 기술적인 위원회와 여러 
조직으부터 온 다양한 메인테이너들이 Hyperledger Fabric 프로젝트를 관리합니다.
최초의 커밋 이래로 35개 이상의 조직과 거의 200명 정도되는 개발 커뮤니티로 
발전했습니다. 

Fabric은 은행과, 재정, 보험, 건강보험, 인사, 공급체인과 심지어는 디지털 음악 
유통까지 포함하는 넓은 범위의 산업 활용 사례들을 위한 혁신과 다 기능성 및 
최적화를 가능하게 하는 고도의 **모듈방식**과 **설정 가능**한 구조를 가지고 
있습니다.

Fabric은 부자연스러운(constrained) 도메인 특화 언어(domain-specific languages, 
DSL)보다는 Java나 Go 그리고 Node.js와 같은 **범용 프로그래밍 언어들로 작성할 수 
있는 스마트 컨트랙트들을 지원**하는 최초의 분산 원장 플랫폼입니다. 이것이 뜻하는 
바는 대개의 기업들은 이미 스마트 컨트랙트들을 개발하기 위해 필요한 기술을 가지고 
있고 DSL이나 새로운 언어를 배우기 위한 훈련이 추가로 필요하지 않다는 것입니다.

Fabric 플랫폼은 또한 **허가형(permissioned)**입니다. 그 말이 무슨 뜻이냐면 
퍼블릭 무허가형 네트워크(public permissionless network)와는 다르게, 참가자들은 
익명이라서 _완전히_ 신뢰받지 못하기보다는 서로를 알고 있습니다. 이 말인즉슨 
참가자들은 서로를 완전히 믿지는 못하더라도 (예를 들면 같은 산업의 경쟁자일 수도 
있습니다) 네트워크는 법적인 합의나 분쟁 해결을 위한 체제와 같이 참가자들 간의 
신뢰에 의해 _기반_하여 구축된 거버넌스 모델에 의해 운영될 수 있습니다.

Fabric 플랫폼의 가장 중요한 차별점 중 하나는 특정한 활용 사례들과 트러스트 
모델(trust models)에 효과적으로 쓰이도록 맞춰진 플랫폼이 될 수 있게 하는 
**장착형 합의 프로토콜(pluggable consensus protocols)**을 지원한다는 점입니다.
예를 들면 단일 엔터프라이즈 내에 배치되거나 신뢰할 수 있는 기관에 의해 운영 
될때, 완전한 비잔틴 장애 허용 합의(fully byzantine fault tolerant consensus)는 
불필요하다고 간주될 수 있고 성능 및 처리량에 과도한 부담이 될 수 있습니다. 
그러한 상황들에서는 
[crash fault-tolerant](https://en.wikipedia.org/wiki/Fault_tolerance) (CFT)
합의 프로토콜은 적절한 반면, 멀티 파티(multi-party)이고 분산된 사용 사례에서는 
전통적인 
[byzantine fault tolerant](https://en.wikipedia.org/wiki/Byzantine_fault_tolerance)
(BFT) 합의 프로토콜이 요구될 수 있습니다.

Fabric은 비싸게 채굴을 하거나 스마트 컨트랙트들을 실행하기 위해 보상금을 
지불하기 위한 **자신만의 암호화폐(native cryptocurrency)를 필요로 하지 않는** 
합의 프로토콜에게 영향력을 발휘할 수 있습니다.  암호화폐를 쓰지 않는 것은 상당한 
risk/attack vectors를 감소시킵니다. 그리고 암호화 마이닝 작업이 없다는 점은 
플랫폼이 다른 분산 시스템과 거의 동일한 운영 비용으로 플랫폼을 구축할 수 있음을 
뜻합니다.

이러한 차별화된 설계 기능을 결합한 것이 Fabric을 트랜잭션 처리와 트랜잭션 확인 
대기 시간 측면에서 **보다 우수한 성능의 플랫폼** 중 하나로 만들며, 그것이 
**프라이버시**와 트랜잭션들과 그 트랜잭션들을 시행하는 스마트 트랜잭션들 
(Fabric이 “체인코드"라고 부르는 것)의 **기밀성**을 가능하게 합니다.

이 차별화된 특징들을 더 자세히 살펴보도록 하시죠.

## 모듈성

Hyperledger Fabric은 모듈 방식 아키텍처를 갖도록 특별히 설계되었습니다. 장착형 
합의이던가 LDAP나 OpenID Connect와 같은 장착형 신원 관리 프로토콜(pluggable 
identity management protocols), 키 관리 프로토콜 혹은 암호화 라이브러리 
이건 간에 플랫폼은 엔터프라이즈 사용 사례 요구 사항의 다양성을 충족하고 
구성되도록 설계되었습니다.

높은 수준에서는 Fabric은 다음과 같은 모듈러 요소들로 구성되어 있습니다.

- 장착형 _ordering service_는 트랜잭션 순서에 대한 합의를 확립한 다음 블록을 피어들에게 브로드 캐스트 합니다.
- 장착형 _membership service provider_는 네트워크의 
엔티티들을 암호화 신원(cryptographic Identities)과 연관시키는 역할을 담당합니다.
- 부가적인 _peer-to-peer gossip service_는 ordering service에 의해 다른 피어에게 
블록을 전파합니다.
- 스마트 컨트렉트들("chaincode")은 컨테이너 환경 (예:Docker) 내에서 격리되어 실행됩니다. 표준 프로그래밍 언어로 작성될 수 있지만 원장 상태에 직접 액세스할 
수는 없습니다.
- 원장은 다양한 DBMS를 지원하도록 구성할 수 있다.
- 애플리케이션별로 독립적으로 구성할 수 있는 장착형(pluggable) endorsement와 인증 
정책이 있습니다.

산업에는 "다른 블록체인들보다 훨씬 뛰어난/모두를 지배하는 하나의 블록 체인"은 
없다는 공정한 합의가 있습니다. Hyperledger Fabric은 여러 산업 분야에서 사용되는 
다양한 솔루션 요구 사항을 충족시키기 위해 여러 가지 방법으로 구성될 수 있습니다.

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
