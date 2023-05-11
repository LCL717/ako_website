---
title: "Verification & Validation and Testing"
date: 2023-04-17T23:01:02-04:00
draft: false
tags: ["Developments"]
categories: ["Software Engineering"]
---

## Verification & Validation

- Verification
  - The process of evaluating a system/component to determine whether the products of a given **development activity** satisfy the conditions imposed at the start of that activity. 确定它是否符合早期定义的需求、标准和规范。
- Validation
  - The process of evaluating a system/component during or **at the end of the development process** to determine whether the software does what the user really requires.

### Dynamic and static verification
- Dynamic V & V Concerned with exercising and observing product behavior.
    
    "Dynamic V&V" 是指动态验证和确认，是软件开发和测试中的一种技术，其关注点是对产品行为的测试和观察。
- Static verification Concerned with analysis of the static system representation to discover problems (i.e., without executing the program)

    静态验证是指对静态系统表示进行分析，以发现问题的过程（即在不执行程序的情况下）。

![20230417234323](https://raw.githubusercontent.com/LCL717/images/main/images/20230417234323.png)

## Testing

### Testing stages

- **Unit testing**（单元测试）
  + Testing of individual components
- **Integration testing**（集成测试，测试组件之间的连接）
  + Testing to expose problems arising from the combination of components
- **System testing**（系统测试）
  + Testing the complete system prior to delivery
- **Acceptance testing**（可能就是咱常说的AC）
  + Testing by users to check that the system satisfies requirements. Sometimes called alpha testing

### Types of testing

- **Defect testing** 缺陷测试
  - Tests designed to discover system defects.
  - A successful defect test is one which reveals the presence of defects in a system.
- **Operational profile** 操作特征模型，便于性能测试，负载测试等
  - Statistical tests designed to reflect the frequency of user inputs.
  - Used for reliability estimation and performance testing.

### Some Terminology

#### Failure
A failure is said to occur whenever the external behavior **does not conform to system spec**.

指系统在实际运行中无法按照规范和要求正常工作的情况。
#### Error
An error is a <font color = "red">**state**</font> of the system which, in the absence of any corrective action, could lead to a failure. 
#### Fault
An <font color = "red">**adjudged cause**</font> of an error. 故障的原因

![20230418152744](https://raw.githubusercontent.com/LCL717/images/main/images/20230418152744.png)

### Testing and debugging

<font color = "red">Testing</font> is concerned with confirming the **presence** of errors. <font color = "red">Debugging</font> is concerned with **locating and repairing** these errors

#### Debugging Activities
![20230418154821](https://raw.githubusercontent.com/LCL717/images/main/images/20230418154821.png)

### Testing Activities
![20230418155634](https://raw.githubusercontent.com/LCL717/images/main/images/20230418155634.png)

### Testing Strategy

#### Black-box Testing
Approach to testing where the program is considered as a ‘black-box’
-  The program test cases are based on the system specification. Test case是基于系统说明书
-  Test planning can begin early in the software process.可以在早期开始
-  Possible test design strategy 一种可能的设计策略

    +  Equivalence partitioning **等价划分**是一种测试设计策略，它将软件系统的输入数据划分为具有相似行为的组或等价类。这种方法的目标是减少测试系统所需的测试用例数量，同时确保覆盖所有重要的情景。

#### White-box testing

+ Derivation of test cases according to program structure. Knowledge of the program is used to identify additional test cases. 根据程序结构推导测试用例。这种策略利用对程序内部结构和代码逻辑的了解，来识别额外的测试用例。
+ Possible test design strategy
  - Equivalence partitioning
  - Code coverage

#### Code Coverage
##### Statement coverage 语句覆盖

Select a test set T such that by executing P for each case in T, each statement of P is executed at least once.

测试集合T中的测试用例可以使P中的每个statement执行至少一次

##### Branch/Edge coverage 分支覆盖
Select a set T such that, by executing P for each member in T, each edge of P’s control-flow graph is traversed at least once.
##### Condition coverage 条件覆盖
All possible values of the constituents of compound conditions are exercised at least once.
##### Path coverage 路径覆盖
Select a test set T such that, by executing P for each member of T, **all paths** leading **from the initial node to the final node** of P’s control-flow graph are traversed.

### quiz

1. What is the difference between **acceptance** and **system** testing?
- Acceptance Testing: focus on customers' requirements.
- System Testing: considers the system design.<br><br>

2. What is the key benefit of unit testing as compared to system testing?

    **Error localization**<br><br>

3. What is the difference between black-box and white box testing?

    **Black-box** tests are designed with respect to requirements and interfaces; **white-box** tests take design and implementation into account.

4. What is structural coverage?
    Structural coverage is the coverage of design and code. (white box)