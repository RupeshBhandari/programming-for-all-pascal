# Chapter 3: Control Structures

Control structures are fundamental in programming, allowing you to control the flow of your program based on conditions and loops. Pascal provides several types of control structures, including conditional statements and loops.

## Conditional Statements

### If-Then Statement

The `if-then` statement is used to execute a block of code only if a specified condition is true.

```pascal
if condition then
  statement;
```

#### Example

```pascal
program IfThenExample;

var
  num: integer;

begin
  num := 10;
  
  if num > 5 then
    writeln('num is greater than 5');
end.
```

### If-Then-Else Statement

The `if-then-else` statement allows you to choose between two blocks of code to execute based on a condition.

```pascal
if condition then
  statement1
else
  statement2;
```

#### Example

```pascal
program IfThenElseExample;

var
  num: integer;

begin
  num := 10;
  
  if num > 15 then
    writeln('num is greater than 15')
  else
    writeln('num is not greater than 15');
end.
```

### Case Statement

The `case` statement is used to execute one block of code out of many based on the value of a variable.

```pascal
case variable of
  value1: statement1;
  value2: statement2;
  ...
  else statementN;
end;
```

#### Example

```pascal
program CaseExample;

var
  grade: char;

begin
  grade := 'B';
  
  case grade of
    'A': writeln('Excellent');
    'B': writeln('Good');
    'C': writeln('Fair');
    'D': writeln('Poor');
    'F': writeln('Fail');
  else
    writeln('Invalid grade');
  end;
end.
```

## Loops

Loops are used to execute a block of code repeatedly.

### For Loop

The `for` loop is used to execute a block of code a fixed number of times.

```pascal
for variable := start_value to end_value do
  statement;
```

#### Example

```pascal
program ForLoopExample;

var
  i: integer;

begin
  for i := 1 to 10 do
    writeln(i);
end.
```

### While Loop

The `while` loop is used to execute a block of code as long as a condition is true.

```pascal
while condition do
  statement;
```

#### Example

```pascal
program WhileLoopExample;

var
  i: integer;

begin
  i := 1;
  
  while i <= 10 do
  begin
    writeln(i);
    i := i + 1;
  end;
end.
```

### Repeat-Until Loop

The `repeat-until` loop is used to execute a block of code until a condition becomes true.

```pascal
repeat
  statement;
until condition;
```

#### Example

```pascal
program RepeatUntilExample;

var
  i: integer;

begin
  i := 1;
  
  repeat
    writeln(i);
    i := i + 1;
  until i > 10;
end.
```

## Nested Loops

You can also nest loops, meaning you can place one loop inside another.

#### Example

```pascal
program NestedLoopExample;

var
  i, j: integer;

begin
  for i := 1 to 3 do
  begin
    for j := 1 to 3 do
    begin
      writeln('i = ', i, ', j = ', j);
    end;
  end;
end.
```

## Breaking Out of Loops

Pascal provides the `break` statement to exit a loop prematurely and the `continue` statement to skip the remaining code in the current iteration and proceed to the next iteration of the loop.

#### Example: Using Break

```pascal
program BreakExample;

var
  i: integer;

begin
  for i := 1 to 10 do
  begin
    if i = 5 then
      break;
    writeln(i);
  end;
end.
```

#### Example: Using Continue

```pascal
program ContinueExample;

var
  i: integer;

begin
  for i := 1 to 10 do
  begin
    if i = 5 then
      continue;
    writeln(i);
  end;
end.
```
