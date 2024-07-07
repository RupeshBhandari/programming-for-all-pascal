# Chapter 8: Error Handling and Debugging

Error handling and debugging are crucial aspects of programming. Proper error handling ensures that your program can deal with unexpected situations gracefully, while debugging helps you identify and fix issues in your code. This chapter will cover techniques and tools for error handling and debugging in Pascal.

## Runtime Errors

Runtime errors occur while the program is running. Common runtime errors include division by zero, file not found, and invalid input. Pascal provides mechanisms to handle such errors gracefully.

### Using the `try...except` Block

The `try...except` block is used to handle exceptions (errors) that occur during program execution.

#### Example

```pascal
program TryExceptExample;

var
  x, y, z: integer;

begin
  x := 10;
  y := 0;

  try
    z := x div y;
    writeln('Result: ', z);
  except
    on E: EDivByZero do
      writeln('Error: Division by zero');
  end;
end.
```

In this example, the division by zero error is caught by the `try...except` block, and a custom error message is displayed.

### Using the `try...finally` Block

The `try...finally` block is used to ensure that certain code is executed regardless of whether an exception occurs or not. This is often used for resource cleanup.

#### Example

```pascal
program TryFinallyExample;

var
  fileVar: text;

begin
  assign(fileVar, 'output.txt');
  rewrite(fileVar);

  try
    writeln(fileVar, 'Hello, World!');
  finally
    close(fileVar);
  end;
end.
```

In this example, the file is closed regardless of whether an error occurs while writing to it.

## Compile-Time Errors

Compile-time errors are detected by the compiler before the program runs. These errors include syntax errors, type mismatches, and undeclared variables. To fix compile-time errors, carefully read the compiler error messages and correct the issues in your code.

### Common Compile-Time Errors

1. **Syntax Errors**: Incorrect use of the language's syntax.
   - Example: Missing semicolon (`;`) or incorrect spelling of keywords.
2. **Type Mismatches**: Using incompatible data types.
   - Example: Assigning a string value to an integer variable.
3. **Undeclared Variables**: Using variables that have not been declared.
   - Example: Using a variable without declaring it first.

## Debugging Techniques

Debugging is the process of identifying and fixing errors in your code. Pascal provides several techniques and tools to help you debug your programs effectively.

### Using Writeln for Debugging

The simplest way to debug your Pascal program is to use the `writeln` statement to print variable values and track the flow of execution.

#### Example

```pascal
program DebuggingExample;

var
  x, y, z: integer;

begin
  x := 10;
  y := 5;

  writeln('x = ', x);
  writeln('y = ', y);

  z := x + y;
  writeln('z = x + y = ', z);

  z := x div y;
  writeln('z = x div y = ', z);
end.
```

### Using the Debugger

Many Pascal IDEs, such as Lazarus, come with built-in debuggers that allow you to set breakpoints, step through code, and inspect variable values.

#### Setting Breakpoints

Breakpoints are markers that you can set in your code to pause execution at specific points. This allows you to examine the state of your program and understand its behavior.

1. Open your Pascal IDE (e.g., Lazarus).
2. Open your Pascal source file.
3. Click in the left margin next to the line where you want to set a breakpoint.
4. Run your program in debug mode.

#### Stepping Through Code

Stepping through code allows you to execute your program line by line. This helps you understand the flow of execution and identify the exact point where an error occurs.

1. Set a breakpoint as described above.
2. Run your program in debug mode.
3. Use the "Step Over" or "Step Into" commands to execute your code line by line.

### Inspecting Variables

While debugging, you can inspect the values of variables at different points in your program. This helps you verify that your variables are being updated correctly.

1. Pause your program at a breakpoint.
2. Hover over a variable to see its current value.
3. Use the "Watch" window to monitor specific variables.

## Handling Specific Exceptions

Pascal provides several predefined exception types that you can handle in your code. Some common exceptions include:

- `EConvertError`: Raised when a string-to-number conversion fails.
- `EInOutError`: Raised during input/output operations (e.g., file not found).
- `EOutOfMemory`: Raised when the system runs out of memory.

### Example: Handling Multiple Exceptions

```pascal
program MultipleExceptionsExample;

var
  x: integer;
  str: string;

begin
  str := 'abc';

  try
    x := StrToInt(str);
    writeln('Converted value: ', x);
  except
    on E: EConvertError do
      writeln('Error: Invalid number format');
    on E: EOutOfMemory do
      writeln('Error: Out of memory');
    else
      writeln('An unknown error occurred');
  end;
end.
```

In this example, the `EConvertError` is caught when trying to convert a non-numeric string to an integer.
