# Reflection

* [Java](#java)
* [Swift](#swift)

## Java

The Java programming language provides a set of classes under the package `java.lang.reflect` for performing reflections in order to "introspect" code a runtime. It is best explained via an example:

```java
public class Main {
    public static void main(String[] args) {
        try {
            Class clazz = Class.forName("java.util.Stack");
            Method methods[] = clazz.getDeclaredMethods();

            for (Method m : methods) {
                System.out.println(m.getName());
            }
        } catch (Throwable e) {
            e.printStackTrace();
        }
    }
}
```

This code finds a Class reference for the fully qualified name given (in this case `java.util.Stack`. Then, it iterates through the methods declared in the class and calls `getName()` on each of them, printy their "simple names." For stack, the output looks like:

```
push
pop
peek
search
```

These APIs provide many other useful ways to introspect on classes at runtime and has a variety of purposes. For exapmple, this has been used to create GUI editors for generating code.

## Swift

Swift also provides APIs for performing reflection at runtime. These are based on a struct called `Mirror` (go figure) which will get filled with the reflected data at runtime. To get a `Mirror` reference, use the struct intiailizer which accepts anything for reflection (classes, structurs, enums, Tuples, Arrays... etc.).

```swift
class MyClass {
    let myBool = true
    let myInt = 10
}

let myClass = MyClass()
let myMirror = Mirror(reflecting: myClass)
```

The `Mirror` struct contains several data types you can use to learn about the class. These include:

* `let displayStyle: Mirror.DisplayStyle?`: the base type: class, struct, etc. May be nil in some cases where `DisplayStyle` does not cover the type, like for closures. ex) `myMirror.displayStyle` is `class`.

* `let children: Children`: The child elements of the subject -- includes both fields and functions. ex) `myMirror.children` is an array containing `myBool true` and `myInt 10`.

* `let subjectType: Any.Type`: The type of the subject. ex) `myMirror.subjectType` is `MyClass`.

* `func superclassMirror() -> Mirror?`: The superclass mirror (if type is a class). ex) `myMirror.superclassMirror()?` is nil (base classes do not have superclasses in Swift).