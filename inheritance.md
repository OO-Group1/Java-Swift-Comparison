# Inheritance

## Java

* Classes in Java support Inheritance.
* Java has a base class Object upon which all other classes are built upon.
* Classes that are inherited from are known as superclasses.
* Classes that inherit from a class are known as a subclass of that superclass they inherit from.
* Classes may only inherit from one class, and no more.
* Subclasses inherit from superclasses through the extends keyword.
* Functions from the superclass can be accessed through the super keyword.

```Java

public class Mammal {
	private int age;
	private String name;
	
	void makeNoise() {
		//not sure what to put here; what noise does a "mammal" make?
	}
}

public class Cat extends Mammal {
	//overrides function in the superclass
	public void makeNoise() {
		System.out.println("Meow!");
	}
}

```

## Swift

* Classes in Swift also support Inheritance.
* Classes that do not inherit from other classes are known as Base Classes.
* Classes that are inherited from are known as a superclass.
* Classes that inherit from a class are known as a subclass of that superclass they inherit from.
* Classes may only inherit from one class, and no more.
* Swift does not have a universal base class.
* Subclasses inherit from superclasses through the : character.
* Functions from the superclass can be accessed through the super keyword. (super.someMethod())
* Functions can be overridden through the override function.

```Swift

class Mammal {
	var age = 0.0;
	var name: String?
	func makeNoise() {
		//we don't know what noise to make
	}
}

class Cat: Mammal {
	override func makeNoise() {
		print("Meow!");
	}
}

```

[Back to Table of Contents](README.md)
