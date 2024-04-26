---
title: Fundamental Java Syntax
date: 2024-03-05 18:30:00 +0800
categories: [Software Construction, en]
tags: [Java, Software Construction, OOP]
math: true
---

> I'm now learning Java with C# fundamental, for which I reckon it better to learn Java in comparison of C#

## Console Input and Output

|                                |            Java            |            C#             |
| :----------------------------: | :------------------------: | :-----------------------: |
|   Start a new line and print   | `System.out.println(...);` | `Console.WriteLine(...);` |
| Print but not start a new line |  `System.out.print(...);`  |   `Console.Write(...);`   |
|       Read the next line       |   `scanner.nextLine();`    |   `Console.ReadLine();`   |

> Note: When reading the next line, an instance of `Scanner` is mandatory. So remember to import it using `import java.util.Scanner;` and create the certain instance using `Scanner scanner = new Scanner(System.in);`

## Basic Data Types

### Mutability

In Java, a datatype can be mutable, or immutable. The data in the memory space where an immutable variable is stored will never change until its "death" and vice versa.

Each of the Java variables is pointer, in C++ terms, or more strictly speaking, a reference. So the mutability of a datatype is critical when programming with it. For a variable of a mutable datatype, it gets its pointed value changed when mutated. But for the one of immutable datatype, it will point to a new address storing the target value when "mutated".

It should be noticed that the "immutable" and "mutable" are attributes of a "variable entity", not the reference.

The reference can also be immutable when declared with `final`.

It's better to use immutable data types in most cases, because the mutable data types is relatively unsafe. But we can prevent the insecurity using "defensive copy", like belows:

```java
// Suppose that A is a mutable datatype.
// Suppose that A(A another) is a copying constructor.
A foo(A param) {
    A param_c = new A(param);   // Defensive copy for parameter(s)
    A rev;                      // The return value
    /* Some Operations */
    return new A(rev);          // Defensive copy for return value
}
```

With defensive copy, when other programmers modified these variables of mutable data types, the data we're using will not be affected.

### Number Types

|              Type               |     Java     |    C#     |                           Range                           |
| :-----------------------------: | :----------: | :-------: | :-------------------------------------------------------: |
|          8-Bit Integer          |    `byte`    |  `sbyte`  |                      $-128$ ~ $127$                       |
|     8-Bit Unsigned Integer      |      -       |  `byte`   |                        $0$ ~ $255$                        |
|         16-Bit Integer          |   `short`    |  `short`  |                  $-32\,768$ ~ $32\,767$                   |
|     16-Bit Unsigned Integer     |      -       | `ushort`  |                      $0$ ~ $65\,535$                      |
|         32-Bit Integer          |    `int`     |   `int`   |         $-2\,147\,483\,648$ ~ $2\,147\,483\,647$          |
|     32-Bit Unsigned Integer     |      -       |  `uint`   |                 $0$ ~ $4\,294\,967\,295$                  |
|         64-Bit Integer          |    `long`    |  `long`   |                  $2^{63}$ ~ $2^{63} - 1$                  |
|     64-Bit Unsigned Integer     |      -       |  `ulong`  |                    $0$ ~ $2^{64} - 1$                     |
| Single-Precision Floating-Point |   `double`   |  `float`  |                   7 significant figures                   |
| Double-Precision Floating-Point |   `double`   | `double`  |                  15 significant figures                   |
|       Big Decimal Integer       | `BigDecimal` |     -     |    $-10^{2\,147\,483\,647}$ ~ $10^{2\,147\,483\,647}$     |
|         Decimal Number          |      -       | `decimal` | $\pm 1.0 \times 10^{-28}$ ~ $\pm 7.922\,8 \times 10^{28}$ |
|      Big (Binary) Integer       | `BigInteger` |           |                 Theoretically infinitive                  |

### Text

|   Type    |   Java   |    C#    |
| :-------: | :------: | :------: |
| Character |  `char`  |  `char`  |
|  String   | `String` | `string` |

### Collections

Both Java and C# provides collection classes. You need to import them with `import java.util.[collection class]` in Java, but in C#, `using System.Collections` or `using System.Collections.Generic` will "import" all the collection classes.

From this we can also discover the difference between Java and C#: Java uses packages while C# uses namespaces.

In Java, almost all the collection classes with simple class name are mutable.
