---
title: "Cohesion and Coupling"
date: 2023-04-19T23:36:22-04:00
draft: false
tags: ["Developments"]
categories: ["Software Engineering"]
---

- **Cohesion** is a measure of the coherence of a module amongst the pieces of that module
- **Coupling** is the degree of relatedness between modules
<div style="text-align: center; font-weight: bold;">
<font color="blue">You want high cohesion and low coupling.</font>

高内聚，低耦合
</div>

## How to achieve high cohesion?

Semantic Coherence
- Clear purpose for each module in a system 
- Functions realized by a module related by
  - Topic
  - Interaction
- Modules as abstractions
  - E.g., domain concepts, Abstract Data Types

Good design provides guidence on where to put new piece of code.

## God class/module:

when a class is too large.

## Coupling

### What types of dependencies induce coupling?

1. Data – providing data
2. Control – controlling another module
3. Service – calling a service
4. Identity – who is the target
5. Location – local or remote target
6. Quality of service – e.g., response time • Content – include, inherit