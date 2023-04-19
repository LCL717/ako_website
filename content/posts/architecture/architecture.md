---
title: "Architecture"
date: 2023-04-18T22:55:34-04:00
draft: false
tags: ["Developments"]
categories: ["Software Engineering"]
---

## Layered Architecture 分层架构
- Each layer represents a level of abstraction or specificity
  1. Provides higher-level services to the layer above it
  2. Relies on lower-level services from the layer below it

  ![20230418231905](https://raw.githubusercontent.com/LCL717/images/main/images/20230418231905.png)

### Pure Form: Only Adjacent Layers Communicate. 只有相同的层之间可以通信。
![20230418232959](https://raw.githubusercontent.com/LCL717/images/main/images/20230418232959.png)
#### Pros:
**Abstraction**: One layer builds on another.

**Portability**: Lower-level layers can be easily replaced.
#### Cons:
**Performance**: Communicating through layers.

**Limited functionality**: No access to specialized features in lower layers.

### Relaxed Form: Cross-Layer Optimazation
在分层架构中，有时为了优化性能或功能，需要允许非相邻层之间进行通信。(ceph: bluestore)
![20230418233143](https://raw.githubusercontent.com/LCL717/images/main/images/20230418233143.png)

- Dependency on Layer **Below** (not above) 原则上是这样的，但是在relaxed form中反转一下也不是不行
  - eg: Callback Interface

  ![20230418233735](https://raw.githubusercontent.com/LCL717/images/main/images/20230418233735.png)

### Exception Handing Strategies 异常处理策略
-  Exceptions can be handled in layer where they occurred or passed up
    - May need to transform exceptions into layers understood by upper layers

      异常可以在发生它们的层级中处理或者向上传递。有时需要将异常转换为上层能够理解的形式。
-  Best to handle <font color = "red">**in layer they occur**</font>
    - Usually most information needed is available there
    - Upper layers may be confronted with error they don’t understand
    - Passing exceptions up increases **coupling** 增加耦合性

### Consequences

- Pros:
  - Understanding system by abstraction levels
  - Insulation(隔离) from changes in lower levels
  - Different implementations of a level can be interchanged

- Cons:
  - Potential performance problems
  - Not all systems easily structured in layers 不是适合所有系统

### What are examples of layered systems?

ISO OSI (which is me的噩梦)


FTP TCP/IP (me通信网68分)

### Two Special Cases Of Layered Architectures
#### Interpreters
##### Interpreters
-  Execute programs in a computer language
-  Ojen represent a kind of layer in a system
-  Subject to layered architecture consequences

##### Virtual Machines

-  A software implementation of a machine
-  A special kind of interpreter (previous slide) 
-  May be implemented as just-in time compiler

##### Hypervisors

#### Tiered architectures

- Layered architecture used enterprise systems 
  - They evolved from monolithic to multi-tier

## Call-And-Return Architectures

### Main Program and Subroutines

**Hierarchical decomposition into subroutines**
将大型计算机程序分解为小的子程序
-  Imperative, mutable state 势在必行的可变的状态？
-  Classic style since 60s aka “Structured programming” 结构化编程
-  Effective for smaller systems 对小系统有效