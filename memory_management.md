# Memory Management

## Java Memory Management

* Java objects live inside of the heap. When the heap becomes full, objects that are no longer being used are cleared, making room for new objects.
* In some cases, the heap is split into two groups: A new group and an old group.
* New objects are put into the new group just like how a single heap adds new objects to itself, except that unused objects are moved to the old group instead.
* The old group functions like the original heap mentioned here; when it becomes full, the unused objects are deleted.
* These things are handled for the user.

```Java

```

## Swift Memory Management

* Allocation and deallocation of memory is done on the behalf of the user using Automatic Reference Counting (ARC).
* Since trying to access an instance that no longer exists would crash the program, ARC will only deallocate an instance if there are exactly zero active references to an instance that still exist.
* In the example below, the reference variable will ensure that the new Cat isn't deallocated.

```Swift

class Cat {

	let name: String
	
	init(name: String) {
		self.name = name
	}
	
	deinit {
	}
}

var reference: Cat?

reference = Cat(name: "Scaredycat")

```