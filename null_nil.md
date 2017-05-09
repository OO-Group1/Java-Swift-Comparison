# Null/nil references


## Java Null/Nil references

* Java uses null as its reference for non-existent objects. In Java specifically, null == null.
* Objects in Java use the this keyword to reference themselves.

```Java
public class myClass {

	private Object obj = new Object();
	private int num;
	
	bool nullObject() {
		return obj.equals(null);
	}
	
	void setNum(int num) {
		this.num = num;
	}
}
```

## Swift Null/Nil references

* Swift uses nil as its reference for the absence of a value of a certain type. Only optionals can be set to nil.
* Objects in Swift use the self keyword to reference themselves.

```Swift

var str: String? = nil
s === nil // true

extension Int {
	double() -> Int {
		return self * 2
	}
}

```

[Back to Table of Contents](README.md)