# Chapter 2: Basic Pascal Syntax

## Program Structure

A Pascal program typically consists of the following parts:

1. **Program Heading**: This is optional but recommended. It specifies the name of the program.
2. **Uses Clause**: This is also optional. It specifies the libraries or units used in the program.
3. **Declaration Part**: This includes variable, constant, type, and procedure/function declarations.
4. **Begin-End Block**: This is the main block where the executable statements reside.

### Example

```pascal
program ExampleProgram;

uses crt;

var
  a, b, sum: integer;

begin
  a := 10;
  b := 20;
  sum := a + b;
  writeln('Sum is: ', sum);
end.
```

## Variables and Data Types

### Declaring Variables

Variables are declared in the `var` section and must have a specified data type.

```pascal
var
  x: integer;
  y: real;
  z: char;
  s: string;
```

### Common Data Types

- **Integer**: Whole numbers.
- **Real**: Floating-point numbers.
- **Char**: Single characters.
- **String**: Sequences of characters.
- **Boolean**: True or False values.

### Example

```pascal
program VariableExample;

var
  age: integer;
  price: real;
  initial: char;
  name: string;
  isStudent: boolean;

begin
  age := 25;
  price := 19.99;
  initial := 'A';
  name := 'Alice';
  isStudent := true;

  writeln('Age: ', age);
  writeln('Price: ', price:0:2);
  writeln('Initial: ', initial);
  writeln('Name: ', name);
  writeln('Is Student: ', isStudent);
end.
```

## Constants and Operators

### Declaring Constants

Constants are declared in the `const` section and must have a fixed value.

```pascal
const
  PI = 3.14159;
  MAX_SIZE = 100;
```

### Operators

Pascal supports various operators for arithmetic, relational, and logical operations.

- **Arithmetic Operators**: `+`, `-`, `*`, `/`, `div`, `mod`
- **Relational Operators**: `=`, `<>`, `<`, `<=`, `>`, `>=`
- **Logical Operators**: `and`, `or`, `not`

### Example

```pascal
program OperatorExample;

var
  a, b, c: integer;
  x, y: boolean;

begin
  a := 10;
  b := 20;

  { Arithmetic Operations }
  c := a + b;
  writeln('a + b = ', c);
  c := b - a;
  writeln('b - a = ', c);
  c := a * b;
  writeln('a * b = ', c);
  c := b div a;
  writeln('b div a = ', c);
  c := b mod a;
  writeln('b mod a = ', c);

  { Relational Operations }
  if a < b then
    writeln('a is less than b');
  if a <> b then
    writeln('a is not equal to b');

  { Logical Operations }
  x := true;
  y := false;
  writeln('x and y = ', x and y);
  writeln('x or y = ', x or y);
  writeln('not x = ', not x);
end.
```
