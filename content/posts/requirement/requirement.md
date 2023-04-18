---
title: "Requirement Engineering"
date: 2023-04-17T20:54:29-04:00
draft: false
tags: ["Developments"]
categories: ["Software Engineering"]
---

A systematic approach to eliciting, organizing, and documenting the requirement of the system, and a process that establishes and maintains agreement between the **customer** and the **project team** on the changing requirements of the system.

![20230417213125](https://raw.githubusercontent.com/LCL717/images/main/images/20230417213125.png)

What does requirement mean?
- the things that the product must do to achieve its purpose
  - <font color="red">**functional requirements** </font>
    - What the system does
- the qualities the product must have
  - <font color="red">**quality (aka non-functional) requirements**</font>
    - How well the system does

## Functional vs. quality requirements

1. **Functional requirements** describe what a system or product must do to achieve its intended purpose. 

2. **Quality requirements**, on the other hand, describe the non-functional characteristics or attributes that a system or product must possess to meet user expectations and achieve its objectives. 

**Example**: One of the <font color="red">*functional requirements*</font> of the control software for a PBX is to automatically detect line faults. Detection of line faults is a functional requirement. Now let us say that a fault must be detected within 20 minutes. This is a <font color="red">*performance requirement*</font> — a quality one

## Necessary properties of requirements

- **Unambiguous**
  - the meaning should be clear
- **Consistent**
  - one requirement must not contradict another
- **Complete**
  - E.g.: “The process is terminated if the wrong PIN has been entered more
than a certain number of times.” (What is that number?) • Verifiable (possible to test)
  - a requirement that cannot be tested is not a requirement
  - E.g.: “The system should work in real-time mode.” (What is “real time” here?)

## A desirable property of requirements
- Free of implementation bias 
  - E.g.,
    + “The system shall accept a password when data is accessed.” ——— This has a requirement to use password.  显然就是说不太行
    + “The system shall ensure that the data can be accessed only by authorized users.” ——— This gives you an opportunity to search for alternatives 
- Feasible 可行性
  - It should be realizable with reasonable effort

