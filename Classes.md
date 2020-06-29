## Classes

Like other Object-Oriented programming languages, Dove support classes. A class is a reusable template for creating objects. It can bundle data with shared behavior together, which makes code simpler and more readable.

To declare a class in Dove, use the keyword `class` followed by an identifier, and a block `{}` containing all its member functions.
```swift
class Button {
    fun press() {
        print "You pressed the button!"
        print "This button has width " + self.width.to_string()
    }
}
```

### Instance

To instantiate a class, we simply call the class by adding `()` after its idenfier, like a function call.
```swift
// This creates a Button instance
let button = Button()
```

An instance can contain an arbitrary number of fields, which is useful for storing data related to the instance. To access a field, we use the dot notation similar to most other OOP languages. Similarly, we can use this notation to set a field as well.
```swift
button.width = 10
print button.width // 10
```

### Member Functions

We can also call its member functions after instantiating. Recall the method `press` defined above. Notice that we did not need to explicitly assign a `press` field to `button`, it was instead declared in the class `Button`.
```swift
button.press()
// "You pressed the button!"
// "This button has width 10"
```
The `self` in the member functions of a class refers to the instance of the class on which the function is being called. In this case, the `self` refers to `button`, whose `width` field was set to `10` earlier.

### Initializers

The way above of initializing an instance is very error prone. What if we forgot to assign a value to the `width` field and tried calling `button.press()`? Accessing a field that does not exist will cause a runetime error. To solve this issue, we can create an initializer to the class by declaring a function called `init`.
```swift
class Button {
    fun init(width) {
        self.width = width
    }
    // ...
}
```

Notice that the initializer takes a parameter `width` and assign it to the `width` field of `self. This ensure that every `Button` instance created will have that field. To use this initializer, we instantiate the class like usual and pass the `width` argument. The `init` method will be called and the necessary fields will be initialized.
```swift
let big_button = Button(20)
print big_button.width // 20
```
