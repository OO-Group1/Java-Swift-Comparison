# Errors and Exception Handling

* [Java](#java)
* [Swift](#swift)


## Java

Java errors / exceptions are sublcasses of a generic class called `Throwable` which represents any issue an app has. `Error` is used to, "indicate problems that a reasonable application would not try to catch. Most such errors are abnormal conditions." Usually this means the application entered into an unrecoverable state.

Most of the time Java programmers don't consider those and instead work with `Exceptions` (and the subclasses thereof). Java's Exception API is very extensible; here are some examples:

```java
try {
  //The constructor may throw (cause) a FileNotFoundException
  FileInputStream in = new FileInputStream("input.txt");

} catch (FileNotFoundException e) {
  //handle exception. ex) print stack trace to the log
  e.printStackTracke();
}
```

Somewhere in the FileInputStream constructor, there is an operation which may cause a FileNotFoundException. The constructor is defined with `throws FileNotFoundException` after the parameters.

```java
class FileInputStream {

  public FileInputStream(String name) throws FileNotFoundException {
    //Open input stream
  }
  
  //...
}
```

Methods may throw multiple types of Exceptions and it is also possible to catch multiple types of exceptions. ex)

```java
try {
  //The constructor may throw (cause) a FileNotFoundException
  FileInputStream in = new FileInputStream("input.txt");

} catch (FileNotFoundException e) {
  //Called if file is not found... Do A.

} catch (NullPointerException e) {
  //Called if filename is provided is null... Do B.
}
```


FileInputStream documentation says that NullPointerException may be thrown, but one doesn't normally catch it because it is a type of `RuntimeException`. RuntimeExceptions are similar to `Errors` in that you don't want to catch them (usually), but while `Errors` represent an unrecoverable state, `RuntimeExceptions` represent a recoverable one.

## Swift

Swift implements what they call do-catch blocks in a similar fashion to Java's try-catches visually, but with some notable differences. They also have try? and try! statements which are essentially shortcut oneliners for handling the errors. 

Errors in Swift are referred to as `Errors`, not `Exceptions`, and `Errors` are enumerations with cases representing differnet types of related errors rather than being subclasses of some generic `Error` class.

```swift
enum VendingMachineError: Error {
    case invalidSelection
    case insufficientFunds(coinsNeeded: Int)
}
```

In each enum case, you may define custom parameters that are passed back to the caller in the form of closures. 

To mark a functions as one that throws an exception(s), you must add `throws` to the end like in Java, but the types of exceptions thrown are inferred based on the code within rather than stated by the programmer.

```swift
class VendingMachine {
  func vend(itenName: String) throws {
    throw VendingMachineError.invalidSelection
  }
}
```

At some level, each case of the Error enumeration *must* be handled, but a single do-catch block need not handle each so long as an enclosing do-catch block does or the function it resides in throws.

```swift
var vendingMachine = VendingMachine()
do {
    try vendingMachine.vend(itemName: "ChocolateBar")

} catch VendingMachineError.invalidSelection {
    //Do A
}
```

Here we catch each of the `VendingMachineErrors` that are thrown by `VendingMachine#vend()`. The shorthand I spoke of before can be implemented like this:

```swift
let x = try? vendingMachine.vend(itemName: "ChocolateBar")
x?.blah()
```

If the function does throw, then the value of x will be nil, and not nil otherwise. If you are sure that your function call will not throw even though it is marked as throws, you may use `try!` to disable error propogation. This gives you and non-optional data type to work with, but will throw a runtime error if an error does in fact occur.

```swift
let y = try! venchindMachine.vend(itemName: "ChocolateBar")
y.blah()
```