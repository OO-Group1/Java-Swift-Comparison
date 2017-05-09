# Reference vs. values

* [Java](#java)
* [Swift](#swift)

## Java

Historically, the question of "pass-by-reference" or "pass-by-value" has caused much confused to Java developers. The reason is that Java is is always **pass-by-value**, but the values it passes may be references if the thing being passed is an object. When calling a method or instantiating a variable, it is always the value that is copied. For object, the value copied is the reference address underneath the hood.

So, if you can wrap your head around that, understand that primatives are values and objects are references, but method calls are pass-by-value.

## Swift

Like Java, Swift has both value and reference types and references refer to objects (class instatiations). However, Swift's value types are not primitives: they can be either struct, enum or tuple (programmers do not have access to primitives in swift, only their classes). These data types are intended for plain, simple sets of data as they are copied for each method call which can become expensive if not monitored. 

Since a class can be used almost exactly like either of these types, Apple advises considering carefully which method to use. Value types allow you to more easily reason about your code and provide safety from unwanted mutation to data, but they can come at a cost. References are usually much more efficient, but they can lead to bugs if not paid attention to.

