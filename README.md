# 凤凰架构

凤凰架构，凤凰表示能够涅槃重生。在软件工程里，系统难免出现问题，允许问题的出现，如何打造出能够"涅槃重生"的系统，使用怎样的架构是需要思考的问题。

## 1. 架构的演进

### 原始分布式时代

计算机诞生初期受限于硬件算力，无法在单台服务器上完成一套软件系统的运行，因此就需要寻找多台计算机共同协作。不过从结果来看，分布式的问题不能一蹴而就解决，
不过历史上的伟大尝试用XX的话来阐述再适合不过：**这次尝试最大的收获就是对 RPC、DFS 等概念的开创，以及得到了一个价值千金的教训：
某个功能能够进行分布式，并不意味着它就应该进行分布式，强行追求透明的分布式操作，只会自寻苦果**

### 单体系统时代

- 单体只是表明系统中主要的过程调用都是进程内调用，不会发生进程间通信，仅此而已

随着计算机算力的提高（摩尔定律），在单台服务器上运行一套完整的系统成为可能，而且单体系统在进程内的调用使得它**简单、高效**，不过这也带来了**自治能力的欠缺和隔离性差**。
譬如部分代码出现进程空间的过度消耗，会影响整个系统的业务；譬如代码在一个进程内，不能隔离，也就没有办法实现单独停止部分代码、单独升级一部分代码。
更重要的是，单体系统难以兼容"Phoenix"的特性，因为它潜在的表达: 单体系统的每一处代码和每一个模块都尽可能没有缺陷，这与"出错是必然"的观念相悖，
随着单体系统不断地庞大起来，完成项目的交付的困难也随之增加，所以单体架构不得不改变和演进。

### SOA时代

- SOA 架构(Service Oriented Architecture): **面向服务的架构**是一次具体地、系统性地成功解决分布式服务主要问题的架构模式

它提出了像烟囱式架构、微内核架构和事件驱动架构等架构模式来对单体系统进行拆分，使拆分出的每一个子系统都能独立地部署、运行和更新。SOA本身是比较抽象的概念，
它不仅仅关注技术，而且还关注研发工程中的需求、管理和组织等问题，终极目标是希望总结出一套自上而下的软件研发方法论，
但是后来因为其过于严格的规范产生的复杂性使得它脱离群众，最终被淹没在了技术的海洋里。

### 微服务时代

- 微服务架构: 微服务是通过多个小型服务组合来构建单个应用的架构风格，这些服务**围绕业务能力**而非特定的技术标准来构建。各个服务可以采用不同的编程语言，
  不同的数据存储技术，运行在不同的进程之中。服务采取轻量级的通信机制和自动化的部署机制实现通信与运维。

微服务更加追求**自由实践**，几乎摒弃了SOA里所有可以摒弃的约束和规范。可是没有了约束，"跟踪治理""负载均衡""熔断隔离""分布式事务"等问题便没有了统一的解决方案，
涌现出了很多技术、框架来解决以上问题，出现了百家争鸣的盛况。微服务架构就像一把双刃剑一样，一刃劈向SOA复杂的技术标准，但是另一刃的泠泠寒光也映向自己。
