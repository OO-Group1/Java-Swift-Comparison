# Interfaces & Protocols

* [Java Interfaces](#java-interfaces)
* [Swift Protocols](#swift-protocols)


## Java Interfaces

* A Java interface, is essentially a skeleton for a class. 
* Defines a list of constants and method signitures
    * fully defined methods may be written into an interface, but these methods must be either default methods or static methods
* Interfaces cannot be instantiated.
* Interfaces are implmented using the *implements* keyword

* Interfaces are so called because they define how a class interacts, or interfaces, with the outside world. For example we can define how to operate a television on the most basic level.

```java
public interface Television {

    int increaseChannel(int currentChannel);
    
    int decreaseChannel(int currentChannel);
    
    int increaseVol(int currentVolume);
    
    int decreaseVol(int currentVolume);
    
    boolean togglePower(boolean powerState);

}
```
* This Interface would then be implemented in the definition of a class, something like this.

```java

public class myTV implements Television {

    private int currentChannel;
    private int currentVolume;
    private boolean powerState;
    
    
    // some getters and setters
    
    int increaseChannel(int currentChannel);
    
    int decreaseChannel(int currentChannel);
    
    int increaseVol(int currentVolume);
    
    int decreaseVol(int currentVolume);
    
    boolean togglePower(boolean powerState);


}




## Swift Protocols







[Back to Table of Contents](README.md)