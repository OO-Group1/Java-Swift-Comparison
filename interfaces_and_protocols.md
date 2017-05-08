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
* Note how the method signitures are ended with a semicolon, not brackets.

* This Interface would then be implemented in the definition of a class, something like this,

```java

public class myTV implements Television {

    private int currentChannel;
    private int currentVolume;
    private boolean powerState;
    
    
    // some getters and setters
    
    int increaseChannel(int currentChannel){
        return currentChannel++;
    }
    
    int decreaseChannel(int currentChannel){
        return currentChannel-1;
    }
    
    int increaseVol(int currentVolume){
        return currentVolume++;
    }
    
    int decreaseVol(int currentVolume){
        return currentVolume-1;
    }
    
    boolean togglePower(boolean powerState){
        if(powerState)
        {
            return !powerState;
        }
        else
        {
            return !powerstate;
        }
    }


}
```
* It is worth noting that Java only supports multiple inheritance with Interfaces only, as it only supports multiple inheritance of type. 
* Implementing multiple interfaces would look something like this,

```java
public class myNewTV implements Television, HDTV { 
    // Define an HD TV here 
}
```


## Swift Protocols

* A Protocol in Swift is very similar to an Interface in Java in that they set certain method signitures for methods that must be implemented, but they also may define properties, and other requirements that an implementing member must fully implement.

* Protocols are defined using the "protocol" keyword, for example 

```swift
protocol Television {
    // protocol goes here
}
```

### Properties

* Protocols may define property names and corrosponding types, and whether or not getters or setters are required
    * Properties defined without a requirement for a getter or setter may be implemented as either a stored property or a computed propety.
    * Required properties must always be declared as variables with the "var" keyword
    * Type properties must also use the static prefix
    
```swift
protocol Television {

    var currentChannel: Int { get set }
    var currentVolume: Int { get set }
    var powerState: bool { get set }
    
    //Methods go here

}
```
### Methods

* Methods are defined in much the same way as in Java.
* Type methods must be prefixed with the "static" keyword

```swift
protocol Television {

    var currentChannel: Int { get set }
    var currentVolume: Int { get set }
    var powerState: bool { get set }
    
    func increaseChannel(currentChannel: Int) -> Int 
    
    func decreaseChannel(currentChannel: Int) -> Int
    
    func increaseVol(currentVolume: Int) -> Int
    
    func decreaseVol(currentVolume: Int) -> Int

    func togglePower(powerState: bool) -> bool
}
```

### Implementation

* Unlike Java there is no keyword to use when defining an object (class, struct, etc.) which might implement the protocol. Instead a colon is put at the end of the name of the object, followed by the name of the protocol.
* Classes and other objects may confrom to multiple protocols in the same way Java classes may implement multiple interfaces.
   



```swift
class myTV: Television {
    
    var currentChannel: Int { get set }
    var currentVolume: Int { get set }
    var powerState: bool { get set }
    
    func increaseChannel(currentChannel: Int) -> Int  {
        return currentChannel + 1
    }
    
    func decreaseChannel(currentChannel: Int) -> Int  {
        return currentChannel - 1
    }
    
    func increaseVol(currentVolume: Int) -> Int  {
        return currentVolume + 1
    }
    
    func decreaseVol(currentVolume: Int) -> Int {
        return currentVolume - 1
    }

    func togglePower(powerState: bool) -> bool {
        if(powerState)
        {
            return !powerState
        }
        else
        {
            return !powerstate
        }
    }


}
```
 * Multiple protocols in Swift are seperated by commas, like this,
 ```swift
class myTV: Television, HDTV { //myTV code}
 ```


[Back to Table of Contents](README.md)