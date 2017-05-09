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