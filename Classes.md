# Class Compairison

* [Defining a class](#defining-a-class)
* [Constructing/initializing](#constructing/initializing)
* [Instantiation](#instantiation)
* [Deconstructing/de-initializing](#deconstructing/de-initializing)

## Defining a class

### Java

* Classes are defined using the “Class” Keyword, and are private, protected, or public. 
    * Each public class must be defined in its own source file. 
    * Private and protected classes may be included in a source 
    
* Attributes should be defined at the start of the class
    
```java
public class Pet {

    String name;
    String type;
    int age;
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


## Constructing / Initiailizing

### Java

* Classes do not require a constructor, however, one is recommended to more precicely control how a class behaves.
    * Constructors must have the same name as the class. 
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

### Swift


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






## Deconstructing/de-initializing

### Java

### Swift




