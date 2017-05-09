# Multithreading

* [Java](#java)
* [Swift](#swift)

### Java

Platforms based on Java may have different, higher level implementations for Threads, but at the most basic level Threads in Java are based off the `Thread` class. One must either:

1. Make a subclass of `Thread` and override the `run()` method, then instantiate the subclass and call `start()` on it OR

2. Make a subclass of `Runnable` and override its `run()` method, then pass this to the default `Thread` constructor and call `start()` on it.

The main difference between the two is that `Thread` is a class and has access to state data about the thread, while `Runnable` is an interface making the `Thread` state data essentially private.

```java
//MyThread.java
class MyThread extends Thread {

  public MyThread() {}

  public void run() {
    //Do things on thread
  }
}

//Main.java
class Main {
  public static void main(String[] args) {
    new MyThread().start();
  }
}
```

```java
//MyRunnable.java
class MyRunnable extends Runnable {

  public MyRunnable() {}

  public void run() {
    //Do things on thread
  }
}

//Main.java
class Main {
  public static void main(String[] args) {
    new Thread(new MyRunnable()).start();
  }
}
```

Alternatively, these classes may be anonymous:

```java
//Main.java
class Main {
  public static void main(String[] args) {
    new Thread(new Runnable() {
      //Do stuff on thread
    }).start();
  }
}
```

### Swift

Swift has a very different implentation of multithreading compared to Java. It relies on what is called a "Grand Central Dispacth" which is in charge of thread lifecycle (e.g. creating and starting threads). One must only call `dispatch_async()` with some queue and closure where the thread will run. Getting the queue to dispatch to is as easy as calling another method. To get the global queue (not main thread), call `dispatch_get_global_queue(priority, flags)`. To get the main queue, call `dispatch_get_main_queue()`. Ex)

```swift
dispatch_async(dispatch_get_global_queue(DISPATCH_QUEUE_PRIORITY_DEFAULT, 0), {
	//Do async things on thread

	dispatch_async(dispatch_get_main_queue(), {
		//Handle result on main thread
	}
}
```