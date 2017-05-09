# Data Types

* [Java](#java-data-types)
* [Swift](#swift-data-types)

## Java Data Types

* Java supports primitive data types such as int, float, booleans, and characters
* Reference types are instantiable classes as well as arrays, such as String, int[], String[], etc.
* The double equals sign, ==, is used to compare contents of variables. Primitive values are compared, while addresses are compared for references.
* Primitive values are returned as the value itself, while returned references give the address.

```Java

private class myClass {
	private int num;//primitive data type
	private String name;//reference type
	
	int getNumber() {
		return num;//returns the current value in num
	}
	
	String getName() {
		return name;//returns the address of the variable name, and NOT a copy of the contents
	}
}

```

## Swift Data Types

* Swift supports two types of data types: named types and compound types.
* Named types include those that can be given a name when defined, such as classes, structures, enumerations, protocols, and even data types considered primitive types in other languages, like numbers, characters, booleans, and strings.
* Compound types are types without names. Only functions and tuples are compound types, and are defined in Swift itself.
* One can specify the type of a variable or expression with type annotation. In the example below, the parameter num is specified to have the type Int.

```Swift example of Type Annotation

func myFunction(num: Int) { /* implementation */ }

```

* Types in Swift all fall into one of two other categories: Value types and Reference types.
* Instances that keep a unique copy of their data are value types.
* Instances sharing a single copy of data are called reference types.



[Back to Table of Contents](README.md)
