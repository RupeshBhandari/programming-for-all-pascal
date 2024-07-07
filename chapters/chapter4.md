# Chapter 4: Procedures and Functions

Procedures and functions are blocks of code that perform specific tasks. They help in organizing and structuring code, making it more readable and maintainable. In Pascal, procedures and functions are declared and used in a straightforward manner.

## Procedures

A procedure is a block of code that performs a specific task but does not return a value.

### Declaring Procedures

```pascal
procedure ProcedureName(parameter_list);
begin
  { procedure body }
end;
```

### Example

```pascal
program ProcedureExample;

procedure Greet(name: string);
begin
  writeln('Hello, ', name);
end;

begin
  Greet('Alice');
end.
```

In this example, the `Greet` procedure takes a string parameter `name` and prints a greeting message.

## Functions

A function is similar to a procedure, but it returns a value.

### Declaring Functions

```pascal
function FunctionName(parameter_list): return_type;
begin
  { function body }
  FunctionName := return_value;
end;
```

### Example

```pascal
program FunctionExample;

function Add(a, b: integer): integer;
begin
  Add := a + b;
end;

begin
  writeln('Sum is: ', Add(5, 10));
end.
```

In this example, the `Add` function takes two integer parameters `a` and `b`, and returns their sum.

## Parameter Passing

Pascal supports different ways of passing parameters to procedures and functions.

### By Value

When a parameter is passed by value, a copy of the actual parameter is passed to the procedure or function. Changes made to the parameter inside the procedure or function do not affect the actual parameter.

```pascal
procedure ByValueExample(x: integer);
begin
  x := x + 1;
end;

var
  a: integer;
begin
  a := 5;
  ByValueExample(a);
  writeln('a = ', a);  { Output: a = 5 }
end.
```

### By Reference

When a parameter is passed by reference, the procedure or function operates on the actual parameter. Changes made to the parameter inside the procedure or function affect the actual parameter.

```pascal
procedure ByReferenceExample(var x: integer);
begin
  x := x + 1;
end;

var
  a: integer;
begin
  a := 5;
  ByReferenceExample(a);
  writeln('a = ', a);  { Output: a = 6 }
end.
```

### Example: By Value and By Reference

```pascal
program ParameterPassingExample;

procedure IncrementByValue(x: integer);
begin
  x := x + 1;
end;

procedure IncrementByReference(var x: integer);
begin
  x := x + 1;
end;

var
  a, b: integer;
begin
  a := 5;
  b := 5;
  
  IncrementByValue(a);
  IncrementByReference(b);
  
  writeln('a (by value) = ', a);  { Output: a = 5 }
  writeln('b (by reference) = ', b);  { Output: b = 6 }
end.
```

## Recursive Procedures and Functions

Recursion is a technique where a procedure or function calls itself.

### Example: Factorial Calculation

```pascal
program FactorialExample;

function Factorial(n: integer): integer;
begin
  if n = 0 then
    Factorial := 1
  else
    Factorial := n * Factorial(n - 1);
end;

begin
  writeln('Factorial of 5 is: ', Factorial(5));  { Output: 120 }
end.
```

In this example, the `Factorial` function calls itself to calculate the factorial of a number.

## Local and Global Variables

### Local Variables

Local variables are declared within a procedure or function and can only be accessed within that procedure or function.

```pascal
program LocalVariableExample;

procedure PrintLocalVariable;
var
  localVar: integer;
begin
  localVar := 10;
  writeln('Local Variable: ', localVar);
end;

begin
  PrintLocalVariable;
end.
```

### Global Variables

Global variables are declared outside any procedure or function and can be accessed by any procedure or function in the program.

```pascal
program GlobalVariableExample;

var
  globalVar: integer;

procedure PrintGlobalVariable;
begin
  globalVar := 10;
  writeln('Global Variable: ', globalVar);
end;

begin
  PrintGlobalVariable;
end.
```
