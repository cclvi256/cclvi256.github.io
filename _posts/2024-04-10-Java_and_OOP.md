---
title: Java and OOP
date: 2024-04-10 11:20:00 +0800
categories:
  - Software Construction
  - en
tags:
  - Java
  - Software Construction
  - OOP
math: true
---

## Three Basic Characteristics of OOP

> The three basic characteristics of OOP is encapsulation, inheritance and polymorphism.
>
> The concepts of OOP is too abstract for many to understand so I prefer to illustrate it by giving examples.

### Encapsulation

#### A Brief Introduction to Encapsulation

Encapsulation is to objects in many circumstances. An object have its internal **fields** (aka. **properties** in Java, and **_rep_** in ADT designing) and external "operations". Commonly external operations through methods are considered as safe, while mutating fields directly may be unsecure, destructive or even catastrophic to cooperating projects. So encapsulation is what ensures the internal security when designing the ADTs. Encapsulation is the primary characteristic of OOP.

#### An Example of Field Encapsulation

In Java, the fields and properties are same, but in C# terms, they are different. In Java, we should write getter and setter methods for a field if necessary, but in C#, the getter and setter are defined in a property. Not rigorously but plainly speaking, you have money in your safe. If others ask you how much money you have in your safe, you can agree or refuse to tell. If you agree, you can count the amount for them, but I believe you won't let them open your safe and count it themselves. In this instance, the money is `private`, and you are `public`. When someone want to know the amount in your safe, they should ask you, like using the public getter method, or the getter of a property. And your consciousness of personal property, and the safe, are like the `private` modifier.

#### Another Example of Encapsulation

I will use an excellent example of letting a student stand up provided by Weng Kai in a C++ lecture to illustrate encapsulation. In the following paragraphs of this part, we suppose the student's name is Eric.

When using structured programming languages, such as C, you should stimulate his certain **muscles** to stand up, but not using his **brain**, **spinal cord** and **nerve**. If you want to enhance the robustness, you should check if he will be blocked by obstacles when standing up, but not using his **eyes**. These operations are much like a kind of programmers' overstepping behaviour.

But when using OOP languages, such as C++ and Java, his muscles are `private`, so you have no permission to stimulate them. But his external ears are `public` to hear sounds. So if you want to let him stand up, you should **say that to him** and let himself to "execute" the standing up operation.

So when object-oriented, he hear someone let himself stand up, first he use his **eyes** and **memory** to judge if he'll be blocked when standing up, use his **brain** to choose his position and which muscles to use, then send the instructions to **muscle** through **spinal cord** and **nerve**. This is consistent with the way humans think.

When using structured programming, we can found the functions are highly coupled. For example, the `stand()` has at least 4 groups of parameters, the first is Eric, **whom was let to stand**, the second is his **position**, the third is his **surroundings**, the fourth is his **physical status**, etc. In fact, each of the groups of parameter can contain many items from other functions. High coupling cannot be more terrible in teamwork, because we should know all about your teammate's code or interfaces.

But things will get better when using OOP, when using OOP, the only data interaction can be from objects. Eric is a complex object composited of his **physiological systems**, **organs**, **tissues**, or even **cells**. So the coupling relationships are simpler and clearer, and each of the parts has to do its best, which's already enough.

#### How Does Encapsulation Implemented?

Encapsulation, essentially, is varying the permission of access. **Access modifiers** can set the permissions of classes, interfaces, methods, fields, etc. The following is the four access modifiers in Java.

| Access Modifier |                                                                           Meaning                                                                           |
| :-------------: | :---------------------------------------------------------------------------------------------------------------------------------------------------------: |
|    `public`     |                                                                 All classes can access it.                                                                  |
|   `protected`   | All classes in the same package can access it, but <br>even the derived classes cannot access its instances' <br>methods if they are in different packages. |
|    `default`    |                                                       All classed in the same package can access it.                                                        |
|    `private`    |                                                            No class except itself can access it.                                                            |

Notice:

- `default` is also an access modifier.
- `private` and `protected` cannot specify a class' access.
- For members of `interface`, the `default` access modifier is `public`.

#### Why C++ is not a Completely OOP Language?

That's because the pointer. Even if a field is declared as `private`, it can still be modified through pointers. But Java offers JVM which ensures the `private` attributes will not be accessed unexpectedly.

### Inheritance

#### Interfaces and Abstract Classes

An abstract class is a class that cannot be instantiated. As for the other features, it's almost the same to normal classes. Abstract classes can have fields, methods, etc., can implement an interface, extend a class, or extended. Each of the methods in an abstract class is implicitly abstract, so there's no need to put `abstract` modifier.

Interface, is similar to class to some extent, but have many differences to class. First, like the abstract class, interfaces cannot be instantiated, either. Additionally, there's a strict limit to the interface members. Only methods, `public static final` fields are allowed to be a member of an interface. Like the abstract class, the methods of an interface is also implicitly abstract.

#### Why Interfaces and Abstract Classes?

When programming with OOP, we have to considered what entities are in our class, and if some of the ones have similar features. If some of the objects are similar, we should find some commonalities amongst them, such as some abilities.

I have to admit interface is difficult to understand, but fortunately, the C# naming conventions inspired me. In C# terms, it's recommended to name an interface like `I...able`, where `I` means that's an interface, and `able` is a description of some ability. In fact, the regulation is not always convenient, because we can define a group of abilities, such as a `List`, but it still makes it clear that interfaces define ability or a set of abilities.

When it comes to abstract classes, things come to be more concrete. The abstract class describes a set of object types, with no necessities to declare a variable with the abstract class itself, such as the relationship between animals and cat. As for the interface, it will define the ability to fly, to jump, etc.

#### Inheritance and The Inheritance Tree

Now it's easier to explain the inheritance. If we need some types of objects have commonalities, we should find out their shared abilities and encapsulate them by singles or by groups into interfaces, then if there're necessities to add abstract classes, then add them, finally use the concrete classes to instantiate objects.

Now is the inheritance. Inheritance can happen between classes, interfaces, which in Java is called extend. Inheritance can also take place from classes to interfaces, which is called implement. Inheritance can only happen to one class, but inheritance to many interfaces are allowed. Here are some examples:

```java
public interface IChirpable {}
public interface ITweetable extends IChirpable {}
public interface IFlyable {}
public interface ISwimmable {}
public abstract class Animal {}
public abstract class Bird extends Animal {}
public abstract class FlyableBird extends Bird implements IFlyable {}
public abstract class UnflyableBird extends Bird {}
public class Sparrow extends FlyableBird implements ITweetable {}
public class Swan extends FlyableBird implements IChirpable {}
public class WildGoose extends FlyableBird implements IChirpable {}
public class Ostrich extends UnflyableBird implements IChirpable {}
```

The complicated inheritance relationship forms an inheritance tree.

#### Method Overriding

In this part, I will still illustrate method overriding using the birds' examples. As we all know, most of the birds fly with the same principle, so in the `FlyableBird` class, there will be an implementation of `Fly` methods. But the wild geese will fly in "V" formation because of their special principle of flying, so their flying method should be different to that in the `FlyingBird` class. Then there's necessity to implement the related functions.

Suppose that the `Fly()` is one of the methods in the interface `IFlyable`:

```java
public interface IFlyable {
	void Fly();
	...
}

public abstract class FlyableBird extends Bird implements IFlyable {
	@Override    // This annotation informs the JVM
	public void Fly() {
		/* Implementation A */
	}
}

public class WildGoose extends FlyableBird implements IChirpable {
	@Override
	public void Fly() {
		/* Implementation B */
	}
}
```

In this example we can find out that the

### Polymorphism

#### Ad Hoc Polymorphism, Method Overloading

The method overloading is that some methods share the same name, but their parameters vary. The overloaded methods must have different parameter types, or the compiler cannot justify which method will be called.

Choosing which overloaded method to call takes place in the static type checking. It depends on which overloaded method have its parameter type complied.

This example shows the overloading.

```java
public int add(int p1, int p2) {
	return p1 + p2;
}

public double add(double p1, double p2) {
	return p1 + p2;
}
```

I have to admit it a good instance of method overloading, despite the meaninglessness in real development.

> Method Overloading and Method Overriding
>
> Method overloading is not overriding. Overloading is some methods have the same name but different parameter types, while overriding is some methods have the same name, parameters, return value type, but one is in the base class, the other is in the derived class.

#### Parametric Polymorphism, Generic

Generic is a feature that allows type as a parameter when declaring classes, interfaces, and methods. In fact, when learning data structures, we can slightly find why generic is necessary. Maybe you have implemented a stack for integers, but, if I want to have a stack of characters, you have to write another stack for characters. So, if the type can be the parameter when declaring stack and its methods, the stack code can be reused better. 

#### Subtype Polymorphism

> Software Reusability and Liskov Substitution Principle.
>
> Liskov substitution principle (LSP) means that we can use the subtype of a class and the user cannot find some difference from the base class. To be more exactly, this can be concluded as the following items:
>
> - The subtype should have the same or the stronger representation invariant, then the subtype always complies the base class' representation invariant.
> - The overridden methods should have stronger specification, including parameters, returned value, and exceptions.
