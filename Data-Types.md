## Data Types

### Booleans
There are two boolean literals: `true` and `false`.

Every Dove value is either truthy or falsey, so that they can be used like a boolean in a logic operation.

Dove follows Ruby's simple truthiness rule: `false` and `nil` are falsey, and everything else is truthy.

### Numbers
There is only one numeric type in Dove: double precision floating-point number which is 64 bits in size.
```swift
0
123
-123
12.345
-12.345
```

### Strings
String literals starts and ends with `"`.
```swift
"Hello World"
```

### Arrays
An array is an ordered collection of items. An array literal is declared by any number of expressions between `[` and `]`, separated by `,` commas. They can contain values of any data type, including another array.
```swift
[1, 2, "hello", [4, 5]]
```

Elements in an array can be accessed by their index. A new value can also be assigned. Remember that indices start at zero!
```swift
let arr = [1, 2, 3]
print arr[1] // 2
arr[1] = 4
print arr // [1, 4, 3] 
```

### Tuples
Tuples are immutable collections of items. They contain any number of items between `(` and `)`, separated by `,` commas. A tuple with only one element must have a trailing comma to differentiate it from a group. They are similar to arrays, except that they are immutable, meaning that you cannot assign new values to it.
```swift
let tup = ("hello", "world")
print tup[0] // "hello"
tup[0] = "hi" // ERROR!

(1,) // Tuple with a single element
```

### Dictionaries
A dictionary is a collection of key value pairs. Each key in the dictionary is associated with a value. Unlike arrays and tuples, dictionaries are unordered. A dictionary can be declared by having key value pairs in the format `key: value`, between `{` and `}`, separated by `,` commas. Currently, only `String`s and integers (a `Number` that ends with `.0`) are allowed as dictionary keys. Like arrays, values in the dictionary can be accessed by their corresponding key, and they are also mutable.
```swift
let dict = {
    "name": "Der",
    "age": 21,
    123: [4, 5, 6],
}
print dict["name"] // "Der"
```

