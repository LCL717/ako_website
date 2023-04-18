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