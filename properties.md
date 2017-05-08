# Properties

* [Getters & Setters](#getters--setters)
* [Backing Variables](#backing-variables)
* [Computed Properties](#computed-properties)

## Getters & Setters

### Java

* All properties in Java require the programmer to write the accessers and modifiers, or getters and setters.
    * Each property requires its own set and get method. 
    * Getters and Setters should be made public to access and modify the properties, while the properties themselves should be made as private. This is to achieve proper encapsulation of data.
    * Some Java IDEs do provide tools to auto generate the getters and setters.

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
    
    public void setName(String name) {
        this.name = name;
    }
    
    public void setType(String type) {
        this.type = type;
    }
    
    public void setAge(int age) {
        this.age = age;
    }
    
    public String getName() {
        return this.name;
    }
    
    public String getType() {
        return this.type;
    }
    
    public int getAge() {
        return this.age;
    }

}
```



### Swift

* Stored properties (properties that are not calculated by the class) do not require getters or setters to access.
* Computed properties use the "get" and "set" methods to access and modify their contents, respectivly. 
    * For read-only computed properties only a return statement is needed.


```swift

class Pet {
    
    var name
    var type
    var age //in years
    //No getters or setters needed here! But lets say we want to convert the age of the pet from years to months
    
    var months: ageInMonths {
            
        get {
            return self.age * 12
        }
    
        set(newAge) {
            self.age = newAge
        }
    
    
    }
    
    
    
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




## Backing Variables

### Java

* Java does not support or incorperate backing variables.

### Swift
    
* Backing variables are done behind the scenes in Swift. Meaning that the programmer does not have access to the backing store for a property.  
    


## Computed Properties

### Java

* If a property requires any computation, it is most often done in the propert's get and set methods at runtime

```java
public class Pet{

    private String name;
    private String type;
    private int age;
    
    //lets add an age in months here too
    private int monthsOld;
    
    
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
    
    public void setName(String name) {
        this.name = name;
    }
    
    public void setType(String type) {
        this.type = type;
    }
    
    public void setAge(int age) {
        this.age = age;
    }
    
    public String getName() {
        return this.name;
    }
    
    public String getType() {
        return this.type;
    }
    
    public int getAge() {
        return this.age;
    }
    
    public int getMonthsOld {
        return this.age * 12;
    }
    
    public void setMonthsOld() {
        this.monthsOld = this.age * 12;
    }
    

}
```

### Swift

* Computed properties are not defined with a set value, and instead provide a getter and optional setter to access and modify other properties indirectly 
* For an example of this see the code block in the [Getters & Setters](#getters--setters) section.







[Back to Table of Contents](README.md)