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

Group

## Namespaces

* Java uses the concept of *packages*. Packages are named collections of classes that are grouped together. Every Java program starts with a base package name which is prefixed to all class definitions. The names of subpackages, classes and their inner classes are appended to give the full class namespace. Package names usually correspond to folders where the class files are stored, although it is more complex than that.

Ex) The `String` class lives in the `java.lang` package as a fundamental part of the Java programming language. The "simple name" is `String`, while its namespace, "unique name" or "fully qualified name" is `java.lang.String`.

Multiple classes of the same name can exist so long as they do not reside in the same package.

* Swift



# General

## Types

Trenton

## References vs values

Jacob


## Null/nil references

Trenton

## Errors and exception handling

Jacob


## Lambda expressions, closures, functions as types

Trenton





# Classes

## General

David

[General Compairson of Classes in Java and Swift](Classes.md)


## Instance reference

Trenton

## Properties

David
[Properties](properties.md)


## Interfaces / Protocols

David

## Inheritance / Extension

Trenton

## Reflection

Jacob




# Other

## Listeners and event handlers

Trenton

## Singletons

David

## Multithreading

Jacob

## Memory management

Trenton