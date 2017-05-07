# Java Vs Swift Class Compairison

# Java

## Defining a class

* Classes are defined using the “Class” Keyword, and are private, protected, or public. 
    * Each class must be defined in its own file. 
    
```java
public class Pet{

    String name;
    String type;
    int age;
    //This is a class in java

}
```

## Constructors

* Classes do not require a constructor, however, one is recommended to more precicely control how a class behaves.
    * Constructors must be either public or protected. 
    
```java
public class Pet{

    String name;
    String type;
    int age;
    
    
    public Pet(String name, String type, int age) {
        this.name = name;
        this.type = type;
        this.age = age;

    }
    

}
```

* Classes may also have multiple constructors, as long as each one has a unique signiture. This allows for different use cases of the class to be instantiated in different ways.
    * This is common practice when a class might have a very common initial condition, for example, the 1-year-old dog shown below

```java
public class Pet{

    String name;
    String type;
    int age;
    
    
    public Pet(String name, String type, int age) {
        this.name = name;
        this.type = type;
        thid.age = age;

    }
    
    public Pet(String name) {
        this.name = name;
        this.type = 'Dog';
        this.age = 1;
    }

}
```
## ABstraction

* Abstraction is supported in Java. This is to say that a class can be created with


## Garbage Collection


Must be own file
Can be Abstract
New instances with “new {className}” convention
Dont need
Without, compiler creates a no argument constructor, which calls the superclass’s no arg constructor.
Can (and should) Create
Can have multiple with different signatures
Different use cases of object
 No Destructing 
All classes inherit finalize method, only used as a last resort to release resources, and only really called at the garbage collector’s discretion


