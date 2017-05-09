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
  * [General](Classes.md)
  * [Instance reference](#instance-reference)
  * [Properties](properties.md)
  * [Interfaces and Protocols](interfaces_and_protocols.md)
  * [Inheritance / Extension](#inheritance--extension)
  * [Reflection](#reflection)

[**Other**](#other)
  * [Listeners and event handlers](#listeners-and-event-handlers)
  * [Singletons](singleton.md)
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

## References vs values

### Java

Historically, the question of "pass-by-reference" or "pass-by-value" has caused much confused to Java developers. The reason is that Java is is always **pass-by-value**, but the values it passes may be references if the thing being passed is an object. When calling a method or instantiating a variable, it is always the value that is copied. For object, the value copied is the reference address underneath the hood.

So, if you can wrap your head around that, understand that primatives are values and objects are references, but method calls are pass-by-value.

### Swift

Like Java, Swift has both value and reference types and references refer to objects (class instatiations). However, Swift's value types are not primitives: they can be either struct, enum or tuple (programmers do not have access to primitives in swift, only their classes). These data types are intended for plain, simple sets of data as they are copied for each method call which can become expensive if not monitored. 

Since a class can be used almost exactly like either of these types, Apple advises considering carefully which method to use. Value types allow you to more easily reason about your code and provide safety from unwanted mutation to data, but they can come at a cost. References are usually much more efficient, but they can lead to bugs if not paid attention to.


## Null/nil references

[Null or nil?](null_nil.md)

* [Java](null_nil.md#Java-Null/Nil-references) 
* [Swift](null_nil.md#Swift-Null/Nil-references)

## Errors and exception handling

### Java

Java errors / exceptions are sublcasses of a generic class called `Throwable` which represents any issue an app has. `Error` is used to, "indicate problems that a reasonable application would not try to catch. Most such errors are abnormal conditions." Usually this means the application entered into an unrecoverable state.

Most of the time Java programmers don't consider those and instead work with `Exceptions` (and the subclasses thereof). Java's Exception API is very extensible; here are some examples:

```java
try {
  //The constructor may throw (cause) a FileNotFoundException
  FileInputStream in = new FileInputStream("input.txt");

} catch (FileNotFoundException e) {
  //handle exception. ex) print stack trace to the log
  e.printStackTracke();
}
```

Somewhere in the FileInputStream constructor, there is an operation which may cause a FileNotFoundException. The constructor is defined with `throws FileNotFoundException` after the parameters.

```java
class FileInputStream {

  public FileInputStream(String name) throws FileNotFoundException {
    //Open input stream
  }
  
  //...
}
```

Methods may throw multiple types of Exceptions and it is also possible to catch multiple types of exceptions. ex)

```java
try {
  //The constructor may throw (cause) a FileNotFoundException
  FileInputStream in = new FileInputStream("input.txt");

} catch (FileNotFoundException e) {
  //Called if file is not found... Do A.

} catch (NullPointerException e) {
  //Called if filename is provided is null... Do B.
}
```


FileInputStream documentation says that NullPointerException may be thrown, but one doesn't normally catch it because it is a type of `RuntimeException`. RuntimeExceptions are similar to `Errors` in that you don't want to catch them (usually), but while `Errors` represent an unrecoverable state, `RuntimeExceptions` represent a recoverable one.

### Swift

Swift implements what they call do-catch blocks in a similar fashion to Java's try-catches visually, but with some notable differences. They also have try? and try! statements which are essentially shortcut oneliners for handling the errors. 

Errors in Swift are referred to as `Errors`, not `Exceptions`, and `Errors` are enumerations with cases representing differnet types of related errors rather than being subclasses of some generic `Error` class.

```swift
enum VendingMachineError: Error {
    case invalidSelection
    case insufficientFunds(coinsNeeded: Int)
}
```

In each enum case, you may define custom parameters that are passed back to the caller in the form of closures. 

To mark a functions as one that throws an exception(s), you must add `throws` to the end like in Java, but the types of exceptions thrown are inferred based on the code within rather than stated by the programmer.

```swift
class VendingMachine {
  func vend(itenName: String) throws {
    throw VendingMachineError.invalidSelection
  }
}
```

At some level, each case of the Error enumeration *must* be handled, but a single do-catch block need not handle each so long as an enclosing do-catch block does or the function it resides in throws.

```swift
var vendingMachine = VendingMachine()
do {
    try vendingMachine.vend(itemName: "ChocolateBar")

} catch VendingMachineError.invalidSelection {
    //Do A
}
```

Here we catch each of the `VendingMachineErrors` that are thrown by `VendingMachine#vend()`. The shorthand I spoke of before can be implemented like this:

```swift
let x = try? vendingMachine.vend(itemName: "ChocolateBar")
x?.blah()
```

If the function does throw, then the value of x will be nil, and not nil otherwise. If you are sure that your function call will not throw even though it is marked as throws, you may use `try!` to disable error propogation. This gives you and non-optional data type to work with, but will throw a runtime error if an error does in fact occur.

```swift
let y = try! venchindMachine.vend(itemName: "ChocolateBar")
y.blah()
```

## Lambda expressions, closures, functions as types

[Lambda Expressions / Closures](lambda.md)





# Classes

## General

[General Compairson of Classes in Java and Swift](Classes.md)

## Instance reference

Trenton

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

Jacob




# Other

## Listeners and event handlers

Trenton

## Singletons

[Singletons](singleton.md)

* [Java](singleton.md#java)
* [Swift](singleton.md#swift)
    
## Multithreading

### Java

Platforms based on Java may have different, higher level implementations for Threads, but at the most basic level Threads in Java are based off the `Thread` class. One must either:

1. Make a subclass of `Thread` and override the `run()` method, then instantiate the subclass and call `start()` on it OR

2. Make a subclass of `Runnable` and override its `run()` method, then pass this to the default `Thread` constructor and call `start()` on it.

The main difference between the two is that `Thread` is a class and has access to state data about the thread, while `Runnable` is an interface making the `Thread` state data essentially private.

```java
//MyThread.java
class MyThread extends Thread {

  public MyThread() {}

  public void run() {
    //Do things on thread
  }
}

//Main.java
class Main {
  public static void main(String[] args) {
    new MyThread().start();
  }
}
```

```java
//MyRunnable.java
class MyRunnable extends Runnable {

  public MyRunnable() {}

  public void run() {
    //Do things on thread
  }
}

//Main.java
class Main {
  public static void main(String[] args) {
    new Thread(new MyRunnable()).start();
  }
}
```

Alternatively, these classes may be anonymous:

```java
//Main.java
class Main {
  public static void main(String[] args) {
    new Thread(new Runnable() {
      //Do stuff on thread
    }).start();
  }
}
```

### Swift

Swift has a very different implentation of multithreading compared to Java. It relies on what is called a "Grand Central Dispacth" which is in charge of thread lifecycle (e.g. creating and starting threads). One must only call `dispatch_async()` with some queue and closure where the thread will run. Getting the queue to dispatch to is as easy as calling another method. To get the global queue (not main thread), call `dispatch_get_global_queue(priority, flags)`. To get the main queue, call `dispatch_get_main_queue()`. Ex)

```swift
dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), {
	//Do async things on thread

	dispatch_async(dispatch_get_main_queue(), {
		//Handle result on main thread
	}
}
```

## Memory management

[Memory Managment](memory_managment.md)