---
title: Java and OOP
date: 2024-04-10 11:20:00 +0800
categories: [Software Construction, en]
tags: [Java, Software Construction, OOP]
math: true
---

## Three Basic Characteristics of OOP

> The three basic characteristics of OOP is encapsulation, inheritance and polymorphism. 
>
> The concepts of OOP is too abstract for many to understand so I prefer to illustrate it by giving examples. 

### Encapsulation

#### A Brief Introduction to Encapsulation

Encapsulation is to objects in many circumstances. An object have its internal **fields** (aka. **properties** in Java, and ***rep*** in ADT designing) and external "operations". Commonly external operations through methods are considered as safe, while mutating fields directly may be unsecure, destructive or even catastrophic to cooperating projects. So encapsulation is what ensures the internal security when designing the ADTs. Encapsulation is the primary characteristic of OOP.

#### An Example of Encapsulation

I will use an excellent example of letting a student stand up provided by Weng Kai in a C++ lecture to illustrate encapsulation. In the following paragraphs of this part, we suppose the student's name is Eric.

When using structured programming languages, such as C, you should stimulate his certain **muscles** to stand up, but not using his **brain**, **spinal cord** and **nerve**. If you want to enhance the robustness, you should check if he will be blocked by obstacles when standing up, but not using his **eyes**. These operations are much like a kind of programmers' overstepping behaviour.

But when using OOP languages, such as C++ and Java, his muscles are private, so you have no permission to stimulate them. But his external ears are public to hear sounds. So if you want to let him stand up, you should **say that to him** and let himself to "execute" the standing up operation. 

So when object-oriented, he hear someone let himself stand up, first he use his **eyes** and **memory** to judge if he'll be blocked when standing up, use his **brain** to choose his position and which muscles to use, then send the instructions to **muscle** through **spinal cord** and **nerve**. This is consistent with the way humans think. 

When using structured programming, we can found the functions are highly coupled. For example, the `stand()` has at least 4 groups of parameters, the first is Eric, **whom was let to stand**, the second is his **position**, the third is his **surroundings**, the fourth is his **physical status**, etc. In fact, each of the groups of parameter can contain many items from other functions. High coupling cannot be more terrible in teamwork, because we should know all about your teammate's code or interfaces.

But things will get better when using OOP, when using OOP, the only data interaction can be from objects. Eric is a complex object composited of his **physiological systems**, **organs**, **tissues**, or even **cells**. So the coupling relationships are simpler and clearer, and each of the parts has to do its best, which's already enough. 

#### How Does Encapsulation Implemented?

Encapsulation, essentially, is varying the permission of access. **Access modifiers** can set the permissions of classes, interfaces, methods, fields, etc. The following is the four access modifiers in Java.

| Access Modifier | Meaning |
| :-: | :-: |
| `public` | All classes can access it. |
| `protected` | All classes in the same package can access it, but <br>even the derived classes cannot access its instances' <br>methods if they are in different packages. |
| (default) | All classed in the same package can access it. |
| `private` | No class except itself can access it.  |

Notice:
- `private` and `protected` cannot specify a class' access.
- For members of `interface`, the default access modifier is `public`.

#### Why C++ is not a Completely OOP Language?

That's because the pointer. Even if a field is declared as `private`, it can still be modified through pointers. But Java offers JVM which ensures the `private` attributes will not be accessed unexpectedly.

### Inheritance

#### Interfaces and Abstract Classes

#### Inheritance Tree

#### Method Overriding

### Polymorphism

#### Ad Hoc Polymorphism, Method Overloading

> Method Overloading and Method Overriding

#### Parametric Polymorphism, Generic

#### Subtype Polymorphism and Liskov Substitution Principle






