## Grammar Rules

```
program         = declarations EOF
```

### Declarations
```
declaration     = class_decl
                | fun_decl
                | var_decl
                | statement

class_decl      = "class" IDENTIFIER ( "from" IDENTIFIER )? "{" ( fun_decl | NEWLINE )* "}"
fun_decl        = "fun" IDENTIFIER "(" parameters? ")" block
var_decl        = "let" IDENTIFIER ( "=" expression )? NEWLINE
```

### Statements
```
statement       = expr_stmt
                | for_stmt
                | print_stmt
                | return_stmt
                | while_stmt
                | empty_stmt
                | block

expr_stmt       = expression
for_stmt        = "for" IDENTIFIER "in" expression block
print_stmt      = "print" expression
return_stmt     = "return" expression
while_stmt      = "while" expression block
empty_stmt      = 
block           = "{" declarations "}"
```

### Expression
The levels of expressions represent the order of precedence of each operation.
```
expression      = assignment

assignment      = ( call "." )? IDENTIFIER "=" assignment
                | if_expr
if_expr         = "if" logic_or block ( "else if" logic_or block )* ( "else" block )?
                | logic_or
logic_or        = logic_and ( "or" logic_and )*
logic_and       = equality ( "and" equality )*
equality        = comparison ( ( "==" | "!=" ) comparison )*
comparison      = range ( ( ">" | "<" | ">=" | "<=" ) range )*
range           = addition (( ".." | "..." ) addition)?
addition        = multiplication ( ( "+" | "-" ) multiplication )*
multiplication  = unary ( ( "*" | "/" ) unary )*
unary           = ( "!" | "-" )* call
call            = primary ( "(" arguments? ")" | "." IDENTIFIER )*
primary         = "true" | "false" | "nil" | "self" | "super"
                | NUMBER | STRING | IDENTIFIER | "(" expression ")"
```

### Utility
```
declarations    = (declaration (NEWLINE declaration)*)?
parameters      = IDENTIFIER ( "," IDENTIFIER )* ","?
arguments       = expression ( "," expression )* ","?
```

## Rules Regarding Newlines
Since Dove does not use semicolons to separate statements, newlines are important to parsing the code correctly; however, newlines are also used sometimes to maintain readability while not affecting the code. The parser uses the following rules.

By default, newlines are treated as statement separators; however, they are ignored when:
- They are directly within a pair of parantheses `()`, brackets `[]`, or braces representing a dictionary literal `{}`.
    ```swift
    let x = 1 * (2 +
        // Newlines are ignored here
        33 - 5
        - 10
    )

    let arr = [
        // Also ignored here
        1,
        2,
        3,
    ]

    function_with_many_args(
        // And here
        arg1,
        arg2,
        if some_condition {
            // However, newlines are not ignored here
            // since it is not directly within the parantheses
            let a = 5
            let b = 10
            b + a
        } else {
            arg3
        },
    )
    ```

- The newline is immediately followed by a dot `.` to allow chained method calls.
    ```swift
    let transformed = some_collection
        .map(process_elem)
        .filter(some_predicate)
    ```

- A backslash `\` is present at the end of the previous line. The first method is preferred - only use this when absolutely necessary.
    ```swift
    let x = 1 + 2 + \
            3 + 4 + 5

    // This should be used instead
    let x = (1 + 2 +
             3 + 4 + 5)
    ```
