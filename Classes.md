# General Class Compairison

* [Defining a class](#defining-a-class)
* [Constructing / initializing](#constructing--initializing)
* [Instantiation](#instantiation)
* [Garbage Collection](#garbage-collection)

## Defining a class

### Java

* Classes are defined using the “Class” Keyword, and are private, protected, or public. 
    * Each public class must be defined in its own source file. 
    * Private and protected classes may be included in a source 
    
* Attributes should be defined at the start of the class
    
```java
public class Pet {

    private String name;
    private String type;
    private int age;
    //This is a class in java

}
```

### Swift

* Swift Classes are also defined using the "Class" keyword, but do not need to be defined as private, protected, or public.
    * Multiple classes may be defined in the same source file. 
    * It is recommended to include small similar classes that are closely linked to each other in the same file, and to seperate large classes and unrelated classes into their own source files
    
```swift

class Pet {
    
    var name
    var type
    var age 

}

```


## Constructing / Initializing

### Java

* Classes do not require a constructor, all classes inherit an empty constructor, which will create an instance of the class, but does not set any attribute values. For this reason it is highly recommended to write a constructor to go with each class.
    * Constructors must have the same name as the class. 
    * Constructors must be either public or protected. 
    
```java
public class Pet{

    private String name;
    private String type;
    private int age;
    
    
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

    private String name;
    private String type;
    private int age;
    
    
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

### Swift

* Rather than using the name of the class as its constructor method, Swift uses the "init()" method.
* Swift provides a default initializer if no "init()" method is defined, but default values of properties are. 
    * When called it assigns the default values defined in the class to its attributes.
* One class may define multple init methods to account for different use cases. 

```swift

class Pet {
    
    var name
    var type
    var age 

    init(name: String, type: String, age: int) {
    
        self.name = name
        self.type = type
        self.age = age
    
    }
    
    init(puppy name: String) {
    
        self.name = name
        self.type = "Dog"
        self.age = 1
    
    }



}
```

## Instantiation

### Java

* When instantiating a class, the "new" keyword must be used to allocate memory for the new object.

* It is then most common to initilize the object using (one of) its constructor(s)

```java

// some code here

//create a new pet
Pet myPet = new Pet(Charlie, dog, 2); // Using the full constructor

Pet puppy = new Pet(Scout) // Using the constructor which assigns a name to a 1 year old dog

//More code...

```
### Swift

* New instances of Swift classes do not require any special keyword. 
    * They are treated like any other variable.
    * It is good practice to instantiate them using the let keyword, which defines the class as a constant value.
    
```swift
// some code here

let myPet = Pet(Charlie, dog, 2)

let myPuppy = Pet(puppy: Scout)

//More code...

```

## Garbage Collection

### Java
    
* Java is a garbage collecting language and therefore does not require users to do any deconstruction.
    * All classes inherit the "finalize()" method, which should be used as a programmer's last resort to release resources
    * "finalize()" is only called at the discretion of the garbage collector at runtime.


### Swift

* Swift uses automatic reference counting or ARC and deallocates resources once there are no more references to that resource.
    * Programmers are not required to do any extra programming to deallocate resources. 
    * The best practice is to make sure reference variables are set to nil once they are no longer needed so that the ARC garbage collection can function properly and not allow the program to hog resources



 [Back to home Table of Contents](README.md)

