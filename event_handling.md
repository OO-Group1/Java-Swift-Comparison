# Event Handling

## Java

* Java uses the Delegation Event Model to handle events. Sources and Listeners are the primary aspects to this model.
* Sources are the objects on which events occur. Sources provide information on the event.
* Listeners generate responses to events. Listeners wait until they receive an event and then act accordingly.

```Java

public class someClass {
	public someFunction() {
		Button okButton = new Button("OK");
		okButton.setActionCommand("OK");
		okButton.addActionListener(new ButtonClickListener());
	}
	
	private class ButtonClickListener implements ActionListener {
		public void actionToPerform(ActionEvent e) {
			String command = e.getActionCommand();
			
			if (command.equals("OK")) {
				//perform some action
			}
		}
	}
}

```

## Swift

* Native solutions for event handling do not exist in Swift. Workarounds have to be implemented.

```Swift

class Event<T> {

	typealias EventHandler = T -> ()

	private var eventHandlers = [EventHandler]()

	func addHandler(handler: EventHandler) {
		eventHandlers.append(handler)
	}

	func raise(data: T) {
		for handler in eventHandlers {
			handler(data)
		}
	}
}

```


[Back to Table of Contents](README.md)
