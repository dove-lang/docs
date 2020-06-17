## Control Flow

### If Expressions
The `if` expression is used to control the execution of code based on a condition. It starts with `if` followed by a boolean and a block of code in `{}`. No parantheses `()` is needed around the boolean value.

It can be followed by any number of `else if`'s, and optionally end with an `else`.
```swift
if a == 1 {
    print("a is 1")
} else if a == 2 {
    print("a is 2")
} else {
    print("a is something else")
}
```

An `if` expression returns the value of the last line of the executed branch. If that branch is empty or does not exist, it will return `null`.
```swift
let x_string = if x == 1 {
    "one"
} else if x == 2 {
    "two"
}
// x_string is "one" if x is 1, "two" if x is 2, and otherwise null
```

### Loops

#### While Loops
A `while` loop allows the repeated execution of a block of code while a condition is `true`. It starts with `while` followed by a boolean and a block of code in `{}`. No parantheses `()` is needed around the boolean value.
```swift
let a = 0;
while a < 10 {
    print("a is less than 10")
    a += 1
}
```

The `break` statement can be used to exit the loop immediately.
```swift
let condition_met = false
// This loop will loop twice, exiting on the second time
while true {
    if condition_met {
        break
    }
    condition_met = true
}
```

#### For loops
A `for` loop facilitates iterating over elements of a collection, such as iterating through an array. It uses the following syntax, where `arr` is the collection to iterate, and `elem` is the corresponding element in `arr` each iteration.
```swift
let arr = [1, 2, 3]
for elem in arr {
    print(elem)
}
```

It is identical to the following `while` loop, but much more simple.
```swift
let arr = [1, 2, 3]
let index = 0
while index < 3 {
    print(arr[index])
    index += 1
}
```

To iterate through a range of integers, we use the operations `...` and `..`. Given two integers `m` and `n`, `m...n` creates the collection of integers between `m` to `n`, inclusive, in ascending order . `m..n` creates the same numbers but excluding `n`.
```swift
for i in 0...3 {
    print(i)
}
// 0
// 1
// 2
// 3

for i in 0..3 {
    print(i)
}
// 0
// 1
// 2
```
