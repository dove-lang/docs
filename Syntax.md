## Syntax
Dove uses the most elegant, mordern syntax you can ever find on the planet Earth.

### Comments
Line comments start with `//` and ends where Dove finds a new line.
```C
// This is a comment.
```
Block comments start with `/*` and ends with `*/`.
```C
/*
    This is a block comment.
    It can continue for many lines.
*/
```

### End of Lines
Using `;` to end lines is deprecated and is not supported in Dove. 
`\n` is meaningful in Dove - it end lines.
```Swift
// Below are two statements:
let a = 3 // End of this line.
let b = 4
```

### Identifiers
Dove identifiers is case-sensitive and should start with a letter or underscore, and may follow by letters, digits, and underscores.
#### Naming Conventions
Variables should be lower case snake case.
```C
dove_variable
```
Constants should be upper case snake case.
```C
DOVE_CONSTANT
```
Private variables/constants should have a leading underscore.
```C
_private_var
_private_const
```

### Blocks
The braces `{}` are used for blocks of code. Blocks are used in function/method definitions, control flows, or anywhere in your Dove code.
```C
{
    statement1
    statement2
    statement3
}
```


