---
title: "软件工程的复习——设计模式"
date: 2023-04-15T16:36:49-04:00
draft: false

tags: ["Developments"]
categories: ["Software Engineering"]

---
 
# Design Patterns 设计模式

我第一次学习设计模式是在北京实习的时候突然给我派了一个攒一整个测试系统的工作，我开始研究哪一种设计模式是最合适的。虽然最后做出来一坨大便，但是确实是我第一次为一个系统从0开始独自写了千行以上的代码，虽然是一坨大便，但是个人成长最大的一次经历，之后 involve in 更大的项目之后都没有那一坨大便让人印象深刻。

## What is a design pattern? (Overview)
A design pattern is a solution to a re-occurring design problem.

在软件开发中，经常会遇到一些相似的问题，例如如何创建对象、如何处理对象之间的关系、如何处理对象之间的通信等等。这些问题在不同的项目中可能会多次出现。设计模式是针对这些重复出现的问题所提供的解决方案。它们是被普遍接受的、经过验证的、可重用的和可扩展的设计方案，可以用来解决特定类型的问题。

Design patterns follow a general format consisting of:

1. Design problem, including the relevant context
2. Design solution
3. Design consequences, including positive andnegative impacts of the solution on system qualities.

### Design Solution

- The design solution typically includes a **structural part**, consisting of **elements with dedicated roles** and **relationships among them**; this aspect is usually represented using a **class diagram**. 

  结构性方面通常由一些具有专门角色和彼此之间关系的元素组成，这些元素可以使用类图（class diagram）进行表示。类图用于表示软件系统中类（class）、接口（interface）、对象（object）之间的关系，包括继承（inheritance）、关联（association）、聚合（aggregation）和组合（composition）等。通过类图，我们可以清晰地看到软件系统中各个元素之间的关系和依赖。

- Some patterns also involve **behavioral aspects**, that is, **interactions among the elements** of the structure; this aspect is typically represented using **sequence diagrams**, but statecharts and activity diagrams can also be used.

  行为性方面则通常涉及到元素之间的交互，这些交互可以使用序列图（sequence diagram）、状态图（statechart）和活动图（activity diagram）等进行表示。序列图用于表示软件系统中对象之间的交互顺序，状态图用于表示软件系统中对象的状态和状态之间的转换，活动图用于表示软件系统中的活动和活动之间的流程。

### Design Consequences

The design consequences are positive impacts and negative impacts on system qualities (maintainability, complexity, performance, etc.). Some of the impacts may be conditional on the specific implementation variant of the design pattern.

设计模式（design pattern）有一个重要特点，即设计模式需要经过实践的检验才能被认可为有效的设计解决方案。
为了避免设计模式过于专业化，一个设计解决方案只有在被至少用于三个不同的系统中，也就是需要应对反复出现的设计问题，才能被认为是一个设计模式。这意味着设计模式需要经过多次实践的检验，才能被广泛地应用于软件设计和开发中。

## Composite 组合模式

- Intent
  - Treat individual objects and multiple, recursively- composed objects uniformly
- Applicability
  - Objects must be composed recursively
  - No distinction between individual and composed elements
  - Objects in the structure can be treated uniformly

在“Composite”模式中，通常会定义一个抽象的“Component”类，它声明了组合对象和单个对象之间的公共接口。然后定义一个“Composite”类，它表示一个组合对象，可以包含其他组合对象和单个对象。同时还定义一个“Leaf”类，它表示一个单个对象，即不能再包含其他对象的最小单位。这样，“Composite”模式就形成了一个树形结构，其中“Component”类是根节点，而“Composite”类和“Leaf”类是其子节点。
通过这种结构，“Composite”模式可以让客户端在不知道具体对象的情况下，统一地处理组合对象和单个对象。客户端可以通过“Component”类的接口，调用组合对象和单个对象的方法，而无需关心它们之间的具体差异。

![Screenshot-2023-04-16-at-10-09-05-PM.png](https://i.postimg.cc/zfX1XPnc/Screenshot-2023-04-16-at-10-09-05-PM.png)

当涉及到图形界面时，可以使用“Glyph”类来表示界面元素，例如文本、图形、按钮等。在这种情况下，如果要实现一个包含多个“Glyph”的组合对象，可以使用“Composite”模式。

例如，假设我们要实现一个文本编辑器，它可以显示文本、图像和按钮等元素。我们可以定义一个“Glyph”类作为所有元素的基类，然后定义一个“CompositeGlyph”类，它表示一个组合对象，可以包含多个“Glyph”对象。同时，我们还可以定义一个“SimpleGlyph”类，它表示一个单个的“Glyph”对象。

通过这种结构，“CompositeGlyph”类可以包含多个“SimpleGlyph”对象和其他“CompositeGlyph”对象，从而形成一个树形结构。客户端可以通过“Glyph”类的接口，调用组合对象和单个对象的方法，例如调用“CompositeGlyph”的“Draw”方法，就会递归地调用它包含的所有“Glyph”对象的“Draw”方法，从而将整个界面绘制出来。

使用“Composite”模式可以使代码更加简洁、灵活和易于扩展。例如，如果我们想要添加一个新的元素类型，只需要定义一个新的“Glyph”子类，并将其添加到“CompositeGlyph”对象中即可。这样可以很容易地扩展编辑器的功能，而不需要修改大量的代码。

### Structure

![Screenshot-2023-04-16-at-10-12-17-PM.png](https://i.postimg.cc/kGNjS7CF/Screenshot-2023-04-16-at-10-12-17-PM.png)

+ Component (Graphic)
  - declares the interface for objects in the composition.
  - implements default behavior for the interface common to all classes, as appropriate.
  - declares an interface for accessing and managing its child components.
  - (optional) defines an interface for accessing a component's parent in the recursive structure, and implements it if that's appropriate.
+ Leaf (Rectangle, Line, Text, etc.)
  - represents leaf objects in the composition. A leaf has no children.
  - defines behavior for primitive objects in the composition.
+ Composite (Picture)
  - defines behavior for components having children.
  - stores child components.
  - implements child-related operations in the Component interface.
+ Client
  - manipulates objects in the composition through the Component interface.


- Consequences
  - Uniformity: treat components the same regardless of
complexity
  - Extensibility: new Component subclasses work wherever old ones do
  -  Overhead: might need prohibitive numbers of objects
- Implementation
  - Do Components know their parents?
  - Uniform interface for both leaves and composites? 
  - Responsibility for deleting children

### Typical Instance Diagram:

  ![Screenshot-2023-04-16-at-10-13-35-PM.png](https://i.postimg.cc/nrVmdx71/Screenshot-2023-04-16-at-10-13-35-PM.png)

## Decorator 装饰器模式

Decorator = **Transparent wrapper**

装饰器模式（Decorator Pattern）的意图和适用性描述。
装饰器模式的主要意图是为对象添加新的职责或功能，而不需要修改原有的对象结构。通过动态地将装饰器对象包装在原有对象的外部，可以在不改变原有对象接口的情况下，为其添加新的行为或功能。这种模式是一种替代继承的方式，避免了深度嵌套和复杂的继承体系。

装饰器模式的适用性包括以下情况：

- 当使用子类继承方式扩展对象功能时不实际或不可行
- 当需要动态地为对象添加新的行为或功能，而不希望修改原有对象的接口
- 当需要为对象添加的行为或功能可以灵活地添加或删除，以满足不同的需求

装饰器模式的优点是允许在运行时动态地为对象添加新的行为或功能，而不需要修改原有的对象代码。它还可以避免类的深度嵌套和复杂的继承体系。但是，装饰器模式会增加代码的复杂性，因为需要创建多个装饰器对象来实现额外的功能。

### Structure

![Screenshot-2023-04-16-at-10-30-22-PM.png](https://i.postimg.cc/CMN8tRcH/Screenshot-2023-04-16-at-10-30-22-PM.png)

+ Component (VisualComponent)
  - defines the interface for objects that can have responsibilities added to them dynamically.
• ConcreteComponent (TextView)
  - defines an object to which additional responsibilities can be attached.
+ Decorator
  - maintains a reference to a Component object and defines an interface that conforms to Component's interface.
+ ConcreteDecorator (BorderDecorator, ScrollDecorator)
  - adds responsibilities to the component.

### Consequences
**Pros:**
+ Responsibilitiescanbeadded/removedatrun-time
+ Avoidssubclassexplosion
+ Recursivenestingallowsmultipleresponsibilities

**Cons:**
- Interface occlusion
  - Doesnotinheritchildmethods,andthusneedtoimplement
forwarding methods
- Split identity (aka identity crisis, object schizophrenia)
  - Clientsmightbyaccidentpointtothechildratherthanthedecorator

## Adaptor
### Intent
Convert the interface of a class into another interface clients expect. Adapter lets classes work together that couldn't otherwise because of incompatible interfaces. 使不兼容的接口兼容。
### Structure
![Screenshot-2023-04-16-at-11-47-12-PM.png](https://i.postimg.cc/PJZNWztY/Screenshot-2023-04-16-at-11-47-12-PM.png)

+ Target (Shape)
  - defines the domain-specific interface that Client uses.
+ Client (DrawingEditor)
  - collaborates with objects conforming to the Target interface.
+ Adaptee (TextView)
  - defines an existing interface that needs adapting.
+ Adapter (TextShape)
  - adapts the interface of Adaptee to the Target interface.
### Adaptor VS Decorator

Decorator enhances another object without changing its interface. A decorator is thus more transparent to the application than an adapter is. As a consequence, Decorator supports recursive composition, which isn't possible with pure adapters.

装饰器模式可以增强一个对象的功能而不改变其接口，因此它对应用程序更加透明，比适配器模式更容易理解。此外，装饰器模式支持递归组合，而适配器模式则不支持。

## Factory Method

参考下这个吧 [Factory Method](https://refactoring.guru/design-patterns/factory-method)

Define an interface for creating an object, but let subclasses decide which class to instantiate. Factory Method lets a class defer instantiation to subclasses.

工厂方法（Factory Method）是一种创建型设计模式，它定义了一个用于创建对象的接口，但是将具体的对象创建过程延迟到子类中去完成。也就是说，工厂方法模式允许一个类在不直接实例化对象的情况下，将对象的创建任务委托给子类来完成。即，工厂方法模式将对象的创建延迟到子类中，由子类来决定创建哪种具体对象。

![20230417162131](https://raw.githubusercontent.com/LCL717/images/main//images/20230417162131.png)

Use the Factory Method pattern when
- a class can't anticipate the class of objects it must create. 当一个类无法预测它必须创建的对象的类。
- a class wants its subclasses to specify the objects it creates. 当一个类希望它的子类指定它创建的对象。
- classes delegate responsibility to one of several helper subclasses, and you want to localize the knowledge of which helper subclass is the delegate. 当一个类委托职责给多个辅助子类中的一个，并且需要将关于哪个子类是委托者的知识局部化？？？

## Abstract Factory

[Abstract Factory](https://refactoring.guru/design-patterns/abstract-factory)

Provide an interface for creating **families of related** or **dependent objects** without specifying their concrete classes.

抽象工厂模式提供了一个接口，用于创建一组相关或依赖对象，而无需指定其具体类。当一个系统需要独立于其产品如何被创建、组合或表示，并且需要提供一个单一的工厂接口来创建一组相关对象时，可以使用该模式。
### Structure

![20230417161745](https://raw.githubusercontent.com/LCL717/images/main/images/20230417161745.png)

### Abstract Factory and Factory Method

- Many designs start by using Factory Method (less complicated and more customizable via subclasses) and evolve toward Abstract Factory, Prototype, or Builder (more flexible, but more complicated). Abstract Factory classes are often based on a set of Factory Methods.  抽象工厂基于Factory Method。
- The main difference between the Abstract Factory and Factory Method patterns is the **level of abstraction**. The Factory Method pattern is used to create a single object, while the Abstract Factory pattern is used to create families of related objects. 工厂方法模式用于创建单个对象，而抽象工厂模式用于创建相关对象族群。

## Strategy

Define a family of algorithms, encapsulate each one, and make them interchangeable. Strategy lets the algorithm vary independently from clients that use it.

涉及定义一组算法，将每个算法封装成一个单独的类，并使它们可以相互替换。这样可以让算法独立于使用它的clients。

### Structure

![20230417172101](https://raw.githubusercontent.com/LCL717/images/main/images/20230417172101.png)

+ Strategy (Compositor)
  - declares an interface common to all supported algorithms. Context uses this interface to call the algorithm defined by a ConcreteStrategy.

    这是指一个通用的算法接口，它可以支持所有的排版算法。上下文（Context）使用这个接口调用由具体策略（ConcreteStrategy）定义的算法。
+ ConcreteStrategy (SimpleCompositor, TeXCompositor,ArrayCompositor) 
  - implements the algorithm using the Strategy interface.
+ Context (Composition)
  - is configured with a ConcreteStrategy object.

    被配置为使用一个具体策略对象。
  - maintains a reference to a Strategy object.

    维护对策略对象的引用。
  - may define an interface that lets Strategy access its data.

    定义一个接口，以便让策略访问其数据。

### Understand how strategy supports dynamic reconfiguration thanks to object composition.

策略模式(Strategy)通过使用对象组合(Composite)，支持在运行时动态地重新配置应用程序的行为。

## Template Method 模版方法

[Template Method](https://refactoring.guru/design-patterns/template-method)

Define the skeleton of an algorithm in an operation, deferring some steps to subclasses. Template Method lets subclasses redefine certain steps of an algorithm without changing the algorithm's structure.
模板方法是一种行为型设计模式，它在一个操作中定义算法的框架，同时将某些步骤推迟到子类中去实现。模板方法允许子类重新定义算法的某些步骤，而不改变算法的整体结构。

### Structure

![20230417200424](https://raw.githubusercontent.com/LCL717/images/main/images/20230417200424.png)

- AbstractClass (Application)
  - **defines** abstract primitive operations that concrete subclasses define to implement steps of an algorithm.
  - implements a template method defining the skeleton of an algorithm. The template method calls primitive operations as well as operations defined in AbstractClass or those of other objects.

- ConcreteClass (MyApplication)
  - **implements** the primitive operations to carry out subclass-specific steps of the algorithm.

### Key Points

1. How to vary steps in template method subclass. 

    如何在模板方法子类中改变步骤：
  模板方法是一种设计模式，它定义了一个算法的骨架，将具体实现留给子类来实现。在子类中，可以通过重写某些步骤来改变算法的具体实现，而不改变算法的整体结构。这种方式可以让模板方法更加灵活和可扩展，同时避免了代码重复的问题。

2. Understand the fragile base class problem and why object composition
and interfaces are often a better alternative.

    脆弱基类问题以及对象组合和接口为什么是更好的选择：
在模板方法中，子类必须依赖于抽象类的具体实现细节，这可能导致所谓的“脆弱基类”问题，即如果抽象类的实现发生变化，可能会导致子类的实现失效。

    为了避免这种问题，可以使用对象组合和接口来代替继承和虚函数。对象组合可以允许对象在运行时动态组合，从而更加灵活和可扩展。接口可以定义对象之间的通信协议，从而解耦对象之间的具体实现细节。这两个技术通常被认为是更加健壮和灵活的设计模式，可以避免脆弱基类问题。

## Observer

*ROS*

Define a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

### Structure

![20230417203232](https://raw.githubusercontent.com/LCL717/images/main/images/20230417203232.png)

- Subject
  - knows its observers. Any number of Observer objects may observe a subject.知道它的Observer。一个Subject可以有任意多个Observer。
  - provides an interface for attaching and detaching Observer objects. 提供删除/增加Observer的接口
- Observer
  - defines an updating interface for objects that should be notified of changes in a subject. Observer定义了一个更新接口，用于在Subject的状态发生变化时通知观察者。任何对象都可以成为Observer，只需实现Observer接口即可。
- ConcreteSubject
  - stores state of interest to ConcreteObserver objects. ConcreteSubject存储感兴趣的状态。
  - sends a notification to its observers when its state changes. 其状态发生变化时通知观察者。
- ConcreteObserver
  - maintains a reference to a ConcreteSubject object. ：ConcreteObserver维护对ConcreteSubject对象的引用
  - stores state that should stay consistent with the subject's. 存储应该与主题保持一致的状态。
  - implements the Observer updating interface to keep its state consistent with the subject's. 它实现了Observer接口中的更新方法，以便在Subject状态发生变化时更新自己的状态。

### getting full update vs. selective registration and update. 完全更新 vs. 选择性注册和更新

ChatGPT says:
- 完全更新：
  - 在完全更新变体中，主题在其状态发生变化时向观察者发送所有数据。这意味着观察者接收到主题数据的完整更新，即使只有一小部分数据发生了变化。这种方法实现简单，但如果主题数据很大或数据变化频繁，则效率可能较低。
- 选择性注册和更新：
  - 在选择性注册和更新变体中，主题只向已注册接收该数据更新的观察者发送特定的数据。这意味着观察者只接收到他们感兴趣的数据的更新，而不是接收所有数据的完整更新。这种方法实现更复杂，但如果主题数据很大或数据变化频繁，则可能更有效。