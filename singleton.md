# Singleton
    
* [Java](#java)
* [Swift](#swift)

## Java
*  Singletons in Java can be implemented in a way that is both thread-safe and lazy as follows

```java
public class Singleton {
    private Singleton() {}

    private static class SingletonHolder {
        private static final Singleton INSTANCE = new Singleton();
    }

    public static Singleton getInstance() {
        return SingletonHolder.INSTANCE;
    }
}
```
**The above code example taken from [here](https://sourcemaking.com/design_patterns/singleton/java/1)


## Swift
* Since Swift v1.2 the one line singleton can be used. 

```swift
Class Singleton {
    static let singletonInstance = Singleton()
}
```
* This implementation of the Singleton concept is also both thread-safe and lazy.
* A slightly better implementation can be done with one extra line...
```swift
Class Singleton {
    static let singletonInstance = Singleton()
    private init() {}
}
```
* By making the init method private, we ensure that no other instance of "Singleton" can be instantiated

[Back to Table of Contents](README.md)