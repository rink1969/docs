# 介绍

`CITA-Cloud`由国内区块链行业的先驱和资深人士创建，他们致力于克服区块链技术在企业应用领域的难点。

通过早期在国产高性能联盟链`CITA`上开发以及落地应用方面的经验积累，发现联盟链虽然在架构上和公链大体一致，但在技术选型，规模、运维、互操作性等方面有很大的不同。

`CITA-Cloud`是一个面向企业场景，**灵活**，**开放**，**可互操作**和**云原生**的区块链框架。

## 灵活

企业场景非常多变，单独一种实现无法满足所有场景。

`CITA-Cloud`采用微服务架构，组件可以灵活替换，针对场景定制最适合的链。

### 快速定制

每个微服务可以有多种不同的实现，相互之间可以替换。

用户根据需要选择适合的组件，无需底层开发，就可以快速定制一条适合具体场景链。


*比如，客户原来使用`Fabric`，因此已经积累了一些使用`chaincode`编写的智能合约。*

*但是因为在某些项目中必须使用国密算法，而无法使用`Fabric`。*

*使用`CITA-Cloud`框架，只要`executor_chaincode`和`kms_sm`两个微服务实现的组合，就能同时实现复用`chaincode`编写的智能合约和支持国密的目标。*

---

*在企业场景中，用户需求场景非常多变，共识算法也可以有不同的选择。*

*使用`CITA-Cloud`框架，在`consensus_bft`和`consensus_raft`两个共识微服务实现之间选择即可，不用任何的额外工作。*

### 场景定制

如果已有的组件都不能满足用户需求，可以针对场景定制某个组件。

同时可以复用其他已有的组件，达到快速定制的目标。

*例如，某著名科研机构使用`CITA-Cloud`框架，只用了两周的时间就完成其自主研发的国密算法实现到微服务的封装，快速完成特定场景的定制。*

## 开放

`CITA-Cloud`使用`Apache 2.0`开源协议，并提供定制所需的架构、开发工具，以及一个开放的社区。

### 架构

使用标准的微服务架构，本身只规定了微服务间的接口，给具体微服务实现留有非常大的发挥空间。

微服务划分采用正交分解方式，实现核心流程可定制，功能组件可替换的能力。

*借鉴控制面和数据面分离的架构思想。将区块链相关的核心流程和核心数据全部集中在名为`controller`的微服务中，其他五个微服务则类似于数据平面，被动调用。*

---

*每一个微服务都能独立完成某项功能，接口能够自洽，保证每个微服务都是标准组件。*

### 语言无关

微服务间通信使用`gRPC`和`ProtoBuf`的组合，各种语言的开发者都可以方便的参与。

*在开发过程中可以选择最适合的语言，方便复用已有的软件栈或者库。*

## 可互操作

随着联盟链在金融，政企领域的应用，越来越多的同构和异构的区块链应运而生。

在促进区块链生态环境日渐丰富的同时，也呈现出割裂和碎片化的趋势。

如何实现区块链之间的互操作，使不同区块链能够协同工作，这是一个非常重要的挑战。

### 智能合约生态

`CITA-Cloud`可以通过替换`executor`微服务的实现来兼容多种智能合约引擎。

*目前兼容了`以太坊`和`Fabric`两个最大的智能合约生态，未来还可以针对具体场景兼容更多的链的生态。*

*比如针对隐私，支持基于零知识证明的合约引擎。*

### 跨链协议

`CITA-Cloud`兼容[陆羽跨链协议](https://gitee.com/luyu-community/luyu-cross-chain-protocol)，实现对异构链的互操作。

*`陆羽跨链协议`是一个面向可信源的互操作协议，旨在成为一套灵活、统一、可靠的互操作协议，实现对不同可信源的便捷接入与可靠操作。*

## 云原生

区块链与云原生都是非常基础的分布式技术，采用云原生已有的发展思路对区块链来说是一条捷径，可以复用云原生社区成熟的资源。

联盟链的生态相比公链差很多，只有借助云原生社区的生态，才能有足够的发展空间。

区块链相比云原生更侧重去中心化的特性，两者可以互补。

### 复用成熟组件

区块链涉及的技术非常多，包括网络，存储，共识，智能合约引擎等。

完全自己开发，投入非常大，且达到企业级可靠性需要的时间比较漫长。

但是其中很多技术在云原生社区已经有成熟的组件。

`CITA-Cloud`可以方便的将已有的成熟技术封装成微服务实现。

*前面提到的`Raft`共识算法，复用`PingCAP`的[Raft](https://github.com/tikv/raft-rs)实现。*

*此实现在`PingCA`的产品中使用多年，经过生产环境的检验。*

*复用此实现，节省了大量的开发测试人力，也使得该微服务实现可靠性直接达到生产可用级别。*

### BaaS服务
借助云原生的能力，`CITA-Cloud`可以提升相关资源管理能力，实现自动化运维。

*支持同一条链的多个节点部署在异地集群，甚至是不同实体的多个集群中。*
