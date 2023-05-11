---
title: "Modularity"
date: 2023-04-19T15:12:12-04:00
draft: false
tags: ["Developments"]
categories: ["Software Engineering"]
---

- **MODULE**: A module is a unit of system decomposition with a well-defined purpose and interface.

- **INTERFACE**: An interface is a contract between a module and its environment. module和环境之间的契约？

![20230419152043](https://raw.githubusercontent.com/LCL717/images/main/images/20230419152043.png)

## Syntactic vs. Semantic Interface

**Syntactic interface** => how to invoke it
-  Service/operation signatures
-  Protocols – valid orders of calling operations

**Semantic interface** => what it does
-  Effect of opera3ons, e.g., how they modify state
-  Performance specification
-  Reliability specification 
-  ...

## module implementation

A module implementation is the secrets hidden inside it

**Examples of Secrets**
-  Representation of data
-  Properties of a device, other than required
properties that need to be exposed
-  Implementation of world models
-  Mechanisms that support policies

Also: Separate aspects that change at different rates. 通过分离不同的aspects可以增强系统的可维护性。

**Interfaces should be based on abstractions that are unlikely to change**  接口应当基于稳定的抽象概念。

## Module Organization 模块组织

### Simple Designs

Software designs that are easy to understand, modify, and maintain

- Prefer simpler designs
  - Fewer modules and dependencies
-  Easier to implement correctly and maintain

### Hierarchical Decomposition 层次分解

将一个大型系统分解成更小、更易于管理的子系统或模块的过程。

### Axiom of Independence 独立性定理

模块之间相互独立，一个模块的实现不依赖于其他的模块。

In a good design, specific module can be adjusted to satisfy its corresponding requirement **without affecting other requirements**.

*Good designs reduce **crosscutting** and **tangling** of key requirements.*
好的设计应该尽量减少关键需求之间的交错和缠结。

#### **Crosscuting**

![20230419162311](https://raw.githubusercontent.com/LCL717/images/main/images/20230419162311.png)


#### **Tangling**

![20230419162417](https://raw.githubusercontent.com/LCL717/images/main/images/20230419162417.png)

*<font color = "red">Quality</font> requirements are difficult to impossible to localize.* 
质量需求因为涉及到整体性的因素，所以很难将它看作是局部的问题。

*Requirements that are more likely to <font color = "red">change</font> are more important to localize.* 
将易于变化的需求优先局部化处理，这样有利于系统的修改和更新



 