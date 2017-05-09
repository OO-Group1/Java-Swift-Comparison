# Lambda Expressions

## Java Lambda Expressions

* Lambda expressions can be used to pass functionality as an argument to other methods, essentially treating code as data.
* Lambda expressions also give coders the ability to write single-method classes in a concise and clean manner.

```Java

import java.util.function.Consumer;

public class LambdaExample {
	public int value = 0;
	
	class innerClass {
		public int value = 10;
		
		void myInnerFunction(int value) {
			Consumer<Integer> myConsumer = (other) ->
			{
				System.out.println("value = " + value); // Statement A
                System.out.println("other = " + other);
                System.out.println("this.value = " + this.value);
                System.out.println("LambdaScopeTest.this.value = " +
                    LambdaScopeTest.this.value);
            };
			
			myConsumer.accept(x);
		}
	}
}

```

## Swift Lambda Expressions

* Swift has support for closures, which are self-contained blocks of functionality that can be passed around like data.
* Closures are also known as lambda expressions in other programming languages.
* Types of parameters and return can be omitted, but it can cause runtime errors if they cannot be inferred.

```Swift

let names = ["Jacob", "Trenton", "David"]

func backward(_ s1: String, _ s2: String) -> Bool {
    return s1 > s2
}
var reversedNames = names.sorted(by: backward)
// reversedNames is equal to ["David", "Trenton", "Jacob"]

```

[Back to Table of Contents](README.md)
