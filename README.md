# Java-Swift-Comparison
Comparing the languages features of Java and Swift including code examples.

# Team

- Jacob Muchow, jam9rd, 16136303
- David Schneider, djs6g7, 12380240
- Trenton Thompson, tstwxc, 16107209

# Table of Contents

[**Introduction**](#introduction)
  * [Language Purpose / Genesis](#language-purpose--genesis)
  * [Procedural / Function Programming](#procedural--functional-programming)
  * [Unique features](#unique-features)
  * [Namespaces](#namespaces)

[**General**](#general)
  * [Types](#types)
  * [References vs values](#references-vs-values)
  * [Null/nil references](#nullnil-references)
  * [Errors and exception handling](#errors-and-exception-handling)
  * [Lambda expressions, closures, functions as types](#lambda-expressions-closures-functions-as-types)

[**Classes**](#classes)
  * [General](#general-1)
  * [Properties](#properties)
  * [Interfaces and Protocols](#interfaces-and-protocols)
  * [Inheritance / Extension](#inheritance--extension)
  * [Reflection](#reflection)

[**Other**](#other)
  * [Listeners and event handlers](#listeners-and-event-handlers)
  * [Singletons](#singletons)
  * [Multithreading](#multithreading)
  * [Memory management](#memory-management)

# Introduction

## Language Purpose / Genesis

### Java

Java was created by James Gosling, Mike Sheridan and Patrick Naughton at Sun Microsystems starting in 1991 and was released publicly in 1995. Interestingly, Java was originally intended to be used for "interactive television", but this did not come to fruition because of limitations in the cable industry. 

Java's primary selling point was the slogan "Write Once, Run Anywhere". This was considered a big plus compared to its main competitiors, C and C++, which much be compiled for the end-user's specific machine which could lead to headaches. Unlike C/C++, Java runs on top of a virtual machine which interfaces with the machine. So long as the Java Virtual Machine (JVM) can run on a machine, so too can a Java program, and without the need for compilation.

Java was also a little higher-level than its competitors, featuring built in managed memory, more security features and better file I/O.

### Swift

Swift was first conceptualized in 2010 by Chris Lattner, an Apple employee, as a replacement for Objective-C (Obj-C), the main programming language used for application programming on Mac OS X and iOS. It was publicly released in 2014 and is backed by Apple as the main programming language for iOS developement going into the future.

Swift was designed from the ground up as a, "modern object-oriented programming language," to replace Obj-C starting on iOS. While Objective-C server Apple well, it is widely considered a "hack" so to speak on top of C. It allowed programmers to use object-oriented principles in their code, meanwhile converting everything back to C in the pre-processor phase of compilation. This solution "worked", but there were several inconsistincies with the language as well as performance issues at runtime.

Swift incorporates what many Apple developers felt were the best features of a wide variety of programming languages while maintaining interoperability with Obj-C, C and C++. It is meant to be elegant while mainting the performance benefits of compiled languages. One of Swift's main hallmarks is safety, introducing the idea of Optionals as a first-class citizen in the language with operators for unwrapping them, all meant to prevent the most common type of crash: null pointer exceptions. A lot could be said about unique features in Swift, but we will get into these later.

## Procedural / Functional Programming

* Java is an etirely Object Oriented language and does not support procedural programming

* Swift does support procedural programming, however it is not recommended. 
    * Swift is first and foremost an Object Oriented language.

## Unique Features

* Swift does not require semicolons at the end of lines.
* Swift has a "lazy" keyword, to denote objects that should be lazily instantiated
* Swift has first class characters for unwrapping Optionals:

  * `!`: used when certain the data will be there or to force it.
  * `?`: used when uncertain the data will be there, continues in code if wrapped data is nill.

## Namespaces

### Java 

Java uses the concept of *packages*. Packages are named collections of classes that are grouped together. Every Java program starts with a base package name which is prefixed to all class definitions. The names of subpackages, classes and their inner classes are appended to give the full class namespace. Package names usually correspond to folders where the class files are stored, although it is more complex than that.

Ex) The `String` class lives in the `java.lang` package as a fundamental part of the Java programming language. The "simple name" is `String`, while its namespace, "unique name" or "fully qualified name" is `java.lang.String`.

Multiple classes of the same name can exist so long as they do not reside in the same package. For any class, it's package can be defined like so:

```java
package com.oo_design;
```

To use a class you must import its package or the class itself. By defining a class as part of a package, you implicitly include all the classes that are also in that package.

```java
import java.io.*;       //All classes in java.io package
import java.io.File;    //File class from java.io package
```

Modern IDEs should automatically add the imports for you on the fly if they are unambiguous. If there are multiple classes with the same name, they may ask you which to import. You can also use a namespace directly in the Java code to resolve conflicts. 

Ex) If I have already imported java.io.File, I must either remove that import line and replace it with mine to just reference `File` in code, or do it like this:

```java
com.oo_design.File file = new File("my_file.txt");
```

### Swift

In Swift, each file or class you create, unless otherwise specified, is available throughout your entire application without the need for importing. Code that comes from other sources is based on a concept called "modules". A module can be either a framework or an application and is considered to be "a single unit of code distribution." To use code from another module, one must use the `import` keyword, which is used to import code from an entire module. Ex)

```swift
import Alamofire
```


\^Note: Alamofire is a popular networking framework for iOS.

Given this there has been much debate over how to best make global constants. Since there are no namespaces in the usual sense within a module, a constant in one place could conflict with a constant in another if named the same. One such way is to leverage Swift's power of extension with enumerations:

```swift
enum Login { }

extension Login {
  struct Data {
    let username: String
    let password: String
  }
}
```

For implementations related to login, we can do:

```swift
extension Login {
  class LoginViewController {
    //Do stuff
  }
}
```

In here, we can refer to `Login.Data` as simply `Data` since `LoginViewController` is and extension of `Login`. Elsewhere, we would refer to it as `Login.Data` still, which gives us some kind of concept of a namespace.

For constants, others have use uninitializable structs to provide something of a namespace:

```swift
struct Colors {
  private init() {}

  static let Red = UIColor(red: 1.0, green: 0.0, blue: 0.0, alpha: 1.0)
}
```

Users of this struct can then refer to `Red` globally by `Colors.Red`, rather than thinking up some unique variable name that won't cause problems now or in the future, which is how Swift works by default.




# General

## Types

[Types](types.md)

* [Java](types.md#java-data-types)
* [Swift](types.md#swift-data-types)

## References vs. values

[References vs. Values](RefVsValue.md)

* [Java](RefVsValue.md#java)
* [Swift](RefVsValue.md#swift)

## Null/nil references

[Null or nil?](null_nil.md)

* [Java](null_nil.md#Java-Null/Nil-references) 
* [Swift](null_nil.md#Swift-Null/Nil-references)

## Errors and exception handling

[Errors and Exception Handling](errors_and_exceptions.md)

* [Java](errors_and_exceptions.md#java)
* [Swift](errors_and_exceptions.md#swift)

## Lambda expressions, closures, functions as types

[Lambda Expressions / Closures](lambda.md)





# Classes

## General

[General Compairson of Classes in Java and Swift](Classes.md)


## Properties

[Properties](properties.md)

* [Getters & Setters](properties.md#getters--setters)
* [Backing Variables](properties.md#backing-variables)
* [Computed Properties](properties.md#computed-properties)

## Interfaces / Protocols

[Interfaces and Protocols](interfaces_and_protocols.md)

* [Java](interfaces_and_protocols.md#java-interfaces)
* [Swift](interfaces_and_protocols.md#swift-protocols)

## Inheritance / Extension

[Inheritance / Extension](inheritance.md)

## Reflection

[Reflection](reflection.md)

* [Java](reflection.md#java-interfaces)
* [Swift](reflection.md#swift-protocols)

# Other

## Listeners and event handlers

[Listeners and event handlers](event_handling.md)

## Singletons

[Singletons](singleton.md)

* [Java](singleton.md#java)
* [Swift](singleton.md#swift)
    
## Multithreading

[Multithreading](multithreading.md)

* [Java](multithreading.md#java)
* [Swift](multithreading.md#swift)

## Memory management

[Memory Managment](memory_management.md)