---
title: "Refactoring and Code Smells"
date: 2023-04-19T16:45:05-04:00
draft: false
tags: ["Developments"]
categories: ["Software Engineering"]
---
什么是重构？

<font color = "red">**Refactoring**</font> is improving design without changing functionality.

Refactoring may involve a simple code transformation such as renaming a method or a class, or moving a method up in the inheritance hierarchy, or a more complex transformation such as applying or removing an instance of a design pattern.

## When to apply refactorings?

In agile development, each commit should have a clear objective. 在敏捷开发中，每一个commit都应该有一个明确的目的

- **Floss refactoring**: 
  
  "FLOSS" 是 "Free/Libre and Open Source Software" 的缩写，指的是自由/开源软件。因此，"FLOSS refactoring" 指的就是在自由/开源软件项目中进行的重构活动。

  这种重构活动通常由社区维护，拥有广泛的用户和贡献者。重构的目的是改进软件的质量、可维护性和可扩展性，以便更好地满足用户需求和社区期望。通过重构，可以消除软件中的设计缺陷、代码冗余、性能问题等，使得软件更加健壮、高效和易于维护。
- **Root-canal refactoring**

  "Root-canal refactoring"（根管治疗重构）是一种软件重构的术语，通常用于描述一种极端的重构活动，旨在消除软件中的严重缺陷和质量问题。

  这种重构活动通常发生在软件质量非常糟糕、难以维护、不稳定或存在安全漏洞的情况下。与牙髓治疗（root-canal therapy）类比，这种重构活动可能需要耗费大量时间和精力，但是可以避免更加严重的问题和风险。

  在进行"Root-canal refactoring"时，通常需要对软件的整体架构和设计进行深入的分析和评估，逐步消除软件中的设计缺陷、代码冗余、性能问题等。这种重构活动可能会涉及到多个模块或组件，需要进行全面的测试和验证，以确保软件的稳定性和可用性。

## Technical Debt and Incremental Design 技术债务？和增量设计

### Incremental Design

Refactoring should be done **frequently**; it should be considered after adding new feature or fixing a bug. Such a continuous refactoring approach is a form of incremental design.

Frequent refactoring avoids the accumulation of design problems.

### Technical Debt

Each time a new feature is added and the design is not improved as needed, design problems will accumulate like debt.

## Test-Driven Design

Refactoring requires a **comprehensive test suite**, both system-level and unit- level, to ensure that the code changes do not introduce bugs.

**System Level**: Tests are normally written based on the requirements specification.

**Module Level**: Writing unit tests can be thought as **a form of specification**; the tests capture what the module should do. Writing unit tests can help flesh out module interfaces; also, well-designed interfaces should be easy to test.

The idea of <font color = "red">**driving the creation of module interfaces through unit tests**</font> is known as test-driven design.

## Code Smells
Code smells are indications of possible design problems in code. 表明code种可能存在design problem。

### Duplicated code 重复的代码

**Drawbacks:**
- **Parallel maintenance**: new features and bug fixes applied to one copy of the duplicated code need to be propagated to the other copies; this propagation is particularly problematic if all duplicates cannot be easily identified; 解bug的时候每一个使用了重复代码的地方都得改，就是说很容易出错。
- **More code**: code duplication increases the amount of code that needs to be maintained.

但也不是完全没有优点：
- Independent development: code clones can be evolved independently.
- Simpler code in context: A duplicate can be customized for the specific target use.
- Potentially higher performance: A duplicate can be optimized for the specific target use.

### Long Method

Long methods should be broken up into smaller ones. 

### Large class (also known as God class)

<span style="background-color:yellow">**God Class**</span><br><br>

A class that has a lot of **methods** (e.g., 50+) has likely too many **responsibilities**.

The solution is to **break it up into smaller classes**.

### Comment

However, comments inside method implementations are often signs of opaque, complicated, and inscrutable code. Rather than explaining opaque code, restructure it. The composed method is an example of such restructuring.

### Switch Statement
就是说，这说明了程序员对于多态的掌握不够。所以需要使用switch为同一个函数实现不一样的但类似的功能。

### Primitive obsession 滥用基本类型
Some developers, especially those who have recently switched from C to an object-oriented language, may tend to use **primitive types**, such as bool, string, and double, in places where a <font color = "red">**user-defined object**</font> type would be more appropriate.

### Long parameter list 

Long parameter lists make methods difficult for clients to understand. There are different possible causes for long parameter lists:

- The method is assuming too many responsibilities. The solution is to break it up into sub-tasks.
- The method is “too far from home”, that is, it operates on data that resides in other objects and this data needs to be passed in as parameters. A potential solution is to move the method or its parts to the classes that contain the data.
- The method takes too many disparate member variables. A potential solution is to gather up parameters as member variables of a cohesive object. 这句话的意思是，某个方法涉及的成员变量过多且不相关，这会导致方法的参数列表过长，使代码难以理解和维护。解决这个问题的一个潜在方法是将这些参数收集到一个具有内聚性的对象中。

### Feature envy
This smell describes a situation where method seems more interested in another class than the one it’s defined in. 过耦合。

### Data clumps
A set of variables seem to “hang out” together, such as being passed as parameters, changed or accessed at the same time. This usually means that these variables should be encapsulated into an object. 就是有一些变量老是一起玩。

### Shotgun surgery

Shotgun surgery occurs when a single, seemingly coherent change **requires changes to many classes**.
If such a change needs to be done more frequently, all these locations that require updates should be gathered into a single place. Such localization may not always be possible, however.

### Direct constructor call 直接调用构造函数

Calling constructors in client code directly often leads to brittleness. If a constructor of a particular class is called in multiple places, these calls will need to be updated if a subclass of the original class should be used instead.

A solution is to use a **factory method**, which localizes the constructor call and can be overridden in subclasses.

### Speculative generality 过度设计

Speculative generality occurs when code is extended with parameters and other mechanisms because **“they could be needed some day”**. 
解决办法是现在遵循kiss原则，未来的工作留给未来做。



