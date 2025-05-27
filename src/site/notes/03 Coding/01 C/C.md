---
{"dg-publish":true,"permalink":"/03-coding/01-c/c/"}
---


# C

- [[03 Coding/02 c++/Functions\|Functions]]
- [[03 Coding/01 C/mathFunctions/mathFunctions\|mathFunctions]]
- [[03 Coding/01 C/Pointers\|Pointers]]

## Data Types

#### Constant Strings

```c
const char *str = "Hello, World!";
```

#### Ternary

```c
if ( a > b){
a = 10;
}
else {
a = 20
}
```

```c
a = (a> b) ? 10 : 20
```

#### Switch Statement

[Source](https://www.geeksforgeeks.org/c-switch-statement/)

```c
switch(expression)
{
case value1: statement_1;
             break;
case value2: statement_2;
             break;
case value_n: statement_n;
              break;
default: default_statement;
}
```


## Operators
```c
varible = <operand> <operator> <operand> ;
```
#example 
```c
sum = a+b;
```

### Precedence

```c
float x = 1 / 10 + 1 ; // 1.1 
```


| Precedence | Operator(s)                                         | Description                                                                         | Associativity                                |               |               |
| ---------- | --------------------------------------------------- | ----------------------------------------------------------------------------------- | -------------------------------------------- | ------------- | ------------- |
| 1          | `()` `[]` `.` `->` `++` `--`                        | Parentheses, Array Subscript, Dot, Structure Ptr, Postfix inc/dec                   | Left-to-Right                                |               |               |
| 2          | `++` `--` `+` `-` `!` `~` `(type)` `*` `&` `sizeof` | Prefix inc/dec, Unary plus/minus, NOT, Bitwise NOT, Cast, Deref, Address-of, Sizeof | Right-to-Left                                |               |               |
| 3          | `*` `/` `%`                                         | Multiplication, Division, Modulus                                                   | Left-to-Right                                |               |               |
| 4          | `+` `-`                                             | Addition, Subtraction                                                               | Left-to-Right                                |               |               |
| 5          | `<<` `>>`                                           | Bitwise Shift Left/Right                                                            | Left-to-Right                                |               |               |
| 6          | `<` `<=` `>` `>=`                                   | Relational Operators (less/greater than)                                            | Left-to-Right                                |               |               |
| 7          | `==` `!=`                                           | Equality/Inequality                                                                 | Left-to-Right                                |               |               |
| 8          | `&`                                                 | Bitwise AND                                                                         | Left-to-Right                                |               |               |
| 9          | `^`                                                 | Bitwise XOR                                                                         | Left-to-Right                                |               |               |
| 10         | `                                                   | `                                                                                   | Bitwise OR                                   | Left-to-Right |               |
| 11         | `&&`                                                | Logical AND                                                                         | Left-to-Right                                |               |               |
| 12         | `                                                   |                                                                                     | `                                            | Logical OR    | Left-to-Right |
| 13         | `?:`                                                | Ternary Conditional                                                                 | Right-to-Left                                |               |               |
| 14         | `=` `+=` `-=` `*=` `/=` `%=` `&=` `^=` `            | =` `<<=` `>>=`                                                                      | Assignment and Compound Assignment Operators | Right-to-Left |               |
| 15         | `,`                                                 | Comma (Expression Separator)                                                        | Left-to-Right                                |               |               |



