# Inheritance

## Java

* Classes in Java support Inheritance.
* Java has a base class Object upon which all other classes are built upon.

## Swift

* Classes in Swift also support Inheritance.
* Classes that do not inherit from other classes are known as Base Classes.
* Classes that are inherited from are known as a superclass.
* Classes that inherit from a class are known as a subclass of that superclass they inherit from.
* Swift does not have a universal base class.

```Swift

class Mammal {
	var age = 0.0;
	var name: String?
	func makeNoise() {
		//we don't know what noise to make
	}
}

class Cat: Mammal {
	func makeNoise() {
		print("Meow!");
	}
}

```

[Back to Table of Contents](README.md)
