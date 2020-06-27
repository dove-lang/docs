## Functions

### Declaration
A function is a block of code that can be called and reused multiple times. To declare a function, we use the keyword `fun`, followed by an identifier, any number of arguments between `(` and `)`, and a block of code `{}`. To call a function, follow its identifier with argumenets between `()`.

```swift
// Declare a function named greet
fun greet(name) {
    print "Hello " + name + "!"
}

// Calls the function
greet("Dove") // "Hello Dove!"
```

Functions are first-class in Dove, which means they can be passed around just like other values. They can be assigned to variables, passed to another function as an argument, etc.

### Returns
A function can have a return value, which will by default be `nil`. A value can be explicitly returned by using the `return` statement, it can be implicitly returned by being the last expression in the block.
```swift
fun fib(n) {
    if n <= 1 {
        // Explicit return
        return n
    }
    
    // Implicit return
    fib(n - 1) + fib(n - 2)
}

print fib(4) // 3
```

### Closure
Functions can be declared inside other functions. It can hold on to all the local variables in the scope in which it is decalred. We can use this to create a simple counter.
```swift
fun make_counter() {
    let count = 0
    fun count() {
        count += 1
        print count
    }
    count
}

let count = make_counter()
count() // 1
count() // 2
```

### Lambdas
Lambdas are also known as anonymous functions. They can be declared and used without a name. To declare a lambda, use the `lambda` keyword, followed by its arguments, an arrow `->`, and the code block `{}` to be executed. The braces can be omitted if the lambda only contains one statement. Lambda behave exactly like functions if they are assigned to a variable.
```swift
fun run_twice(f, x) {
    f(x)
    f(x)
}

run_twice(lambda x -> print 2 * x, 3)
// This prints:
// 6
// 6

// This is the same as the fib function above
let fib;
fib = lambda n -> {
    if n <= 1 {
        n
    }
    fib(n - 1) + fib(n - 1)
}
```
