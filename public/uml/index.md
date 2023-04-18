# UML——Class Diagrams


# Class Diagrams

A dass diagram describes the types of objects in the System and the various kinds of static relationships that exist among them.

类图描述了系统中对象的类型以及它们之间存在的各种静态关系。

## Attributes 特性
The attribute notation describes a property as a line of **text within the class box** itself. The full form of an attribute is:

`visibility name: type multiplicity = default {property-string}`

访问控制符（visibility） + 属性名称（name） + 冒号（:）+ 属性类型（type）+ 多重性（multiplicity）+ 等号（=）+ 默认值（default）+ 花括号（{}）+ 属性字符串（property-string）

- This visibility marker indicates whether the attribute is public (+) or private (-);
- The name of the attribute - how the class refers to the attribute - roughly corresponds to the name of a field in a programming language.
  属性的名称（attribute name）指的是类如何引用该属性，大致对应于编程语言中字段（field）的名称。
- The type of the attribute indicates a restriction an **what kind of object**（string, int, bool, etc.） may be placed in the attribute. You can think of this as the type of a field in a programming language.
- The default value is the value for a newly created object if the attribute isn't specified during creation.
- The {property-string} allows you to indicate additional properties for the attribute. In the example, I used {readOnly} to indicate that clients may not modify the property. If this is missing, you can usually assume that the attribute is modifiable. 

An example of this is:

`name: String [1] = "Untitled" {readOnly}`

*Only the **name** is necessary.*

![Screenshot-2023-04-16-at-9-27-11-PM.png](https://i.postimg.cc/kXNf4MMT/Screenshot-2023-04-16-at-9-27-11-PM.png)

## Associations 关系

An association is a **solid line** between two classes, directed from the source class to the target class.

  ![Screenshot-2023-04-16-at-9-25-55-PM.png](https://i.postimg.cc/WpCQr4vj/Screenshot-2023-04-16-at-9-25-55-PM.png)

## Multiplicity 多重性
The multiplicity of a property is an indication of how many objects may fill the property. The most common multiplicities you will see are:

1. **1** (An order must have exactly one customer.)
2. **0..1** (A corporate customer may or may not have a single sales rep.)
3. **\*** (A customer need not place an Order and there is no upper limit to the number of Orders a Customer may place-zero or more orders.)

More generally, multiplicities are defined with a <font color="red">**lower bound**</font> and an <font color="red">**upper bound**</font>. The lower bound may beany positive number or zero; the upper is any positive number or `*` (for unlimited). If the lower and upper bounds are the same, you can use one number; hence, `1` is equivalent to `1..1`.Because it's a common case, `*` is short for `0..*`.

![Screenshot-2023-04-16-at-9-29-31-PM.png](https://i.postimg.cc/1zbpBb5g/Screenshot-2023-04-16-at-9-29-31-PM.png)

## Generalization 继承？

![Screenshot-2023-04-16-at-9-34-02-PM.png](https://i.postimg.cc/gcsxkfFv/Screenshot-2023-04-16-at-9-34-02-PM.png)

## Aggregation and Composition 聚合和组合

- 聚合是一种关系，其中一个对象包含对另一个对象的引用，但被包含的对象可以独立于容器对象而存在。换句话说，**被包含的对象并不是容器对象所拥有的**。聚合通常用一个指向被包含类的菱形表示，例如汽车和其轮子之间的关系。

  ![Screenshot-2023-04-16-at-9-08-34-PM.png](https://i.postimg.cc/50XRY5Y1/Screenshot-2023-04-16-at-9-08-34-PM.png)

- 组合是一种关系，**其中一个对象拥有另一个对象**，并且所拥有的对象的生命周期与拥有对象的生命周期相同。换句话说，被拥有的对象不能在没有拥有它的对象的情况下存在。组合通常用一个填充的菱形表示，例如汽车和其引擎之间的关系。

  ![Screenshot-2023-04-16-at-9-11-02-PM.png](https://i.postimg.cc/rs8RZj12/Screenshot-2023-04-16-at-9-11-02-PM.png)

## Interfaces and Abstract Classes 接口和抽象类

- An abstract class is a class that cannot be directly instantiated. The most common way to indicate an abstract dass or operation in the UML is to <font color="red">*italicize*</font> the name, you can also use the label : `{abstract}` .

- An interface is a class that has <font color="red">**no**</font> implementation ; that is, all its features are abstract. You mark an interface with the key-word `<<interface>>`.

# Object Diagrams 

An object diagram is a snapshot of the objects in a System at a point in time. Because it Shows instances rather than classes, an object diagram is often called an **instance diagram**.

![Screenshot-2023-04-16-at-9-58-03-PM.png](https://i.postimg.cc/BvwBPXKG/Screenshot-2023-04-16-at-9-58-03-PM.png)


