# Reference vs. values

* [Java](#java)
* [Swift](#swift)

## Java

Historically, the question of "pass-by-reference" or "pass-by-value" has caused much confused to Java developers. The reason is that Java is is always **pass-by-value**, but the values it passes may be references if the thing being passed is an object. When calling a method or instantiating a variable, it is always the value that is copied. For object, the value copied is the reference address underneath the hood.

So, if you can wrap your head around that, understand that primatives are values and objects are references, but method calls are pass-by-value. As a result, the `==` operator is use for determining equality of the value. This works fine for primitives, but for objects then the operator is comparing the address underneath the hood, which may not be what you expect. To handle equality at a higher level, each Java Object has a function called `equals()` which can be overridden to change how equality works. By default it acts like the `==` operator. `String` is a great example of how this works:

```java
String a = "hey";
String b = "hey";

if (a == b) {
  System.out.println("Equal");
} else {
  System.out.println("Not equal");
}
```

This would print "Not equal" to the log because two different string objects are created in memroy and we are comparing the references.

```java
if (a.equals(b)) {
  System.out.println("Equal");
} else {
  System.out.println("Not equal");
}
```

This would print "Equal" because it calls `Strings` implementation of the `equals()` method which compares the characters of the two strings to determine equality.

## Swift

Like Java, Swift has both value and reference types and references refer to objects (class instatiations). However, Swift's value types are not primitives: they can be either struct, enum or tuple (programmers do not have access to primitives in swift, only their classes). These data types are intended for plain, simple sets of data as they are copied for each method call which can become expensive if not monitored. 

Since a class can be used almost exactly like either of these types, Apple advises considering carefully which method to use. Value types allow you to more easily reason about your code and provide safety from unwanted mutation to data, but they can come at a cost. References are usually much more efficient, but they can lead to bugs if not paid attention to.

To compare values/references in swift, the `==` operator is used. Unlike Java, this operator can be overriden which means that `==` can be used to compare values rather than references.

```swift
let a = "hey"
let b = "hey"

if a == b {
  print("Equal")
} else {
  print("Not equal")
}
```

While the corresponding operation printed "Not equal" in Java, this actually prints "Equal" in Swift because the operator is overloaded for the `String` class. If you were interested in comparing the actual object references, Swift gives you the `===` and `!==` operators. Don't fear, this isn't JavaScript. It is just an explicit way to state you are comparing the references to see if the objects are the same instance. The people who created Swift wanted it to act how you expect it to rather than surprise you. The following example will print "Not equal" to the log:

```swift
let a = "hey"
let b = "hey"

if a === b {
  print("Equal")
} else {
  print("Not equal")
}
```