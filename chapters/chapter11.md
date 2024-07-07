# Chapter 11: Appendix

This appendix provides additional resources to help you with Pascal programming. It includes a list of Pascal reserved words, common compiler directives, and tips and best practices for writing efficient and maintainable Pascal code.

## Pascal Reserved Words

Reserved words are predefined and cannot be used as identifiers (e.g., variable names, procedure names). Here is a list of Pascal reserved words:

```text
and         array       begin       case        const
div         do          downto      else        end
file        for         function    goto        if
in          label       mod         nil         not
of          or          packed      procedure   program
record      repeat      set         then        to
type        until       var         while       with
```

## Common Compiler Directives

Compiler directives are special instructions to the compiler to modify its behavior. Here are some commonly used Pascal compiler directives:

### Syntax

Compiler directives are typically placed between `{$` and `}`.

### Examples

- **`$I`**: Include a file.
  ```pascal
  {$I filename.inc}
  ```

- **`$R`**: Enable or disable range checking.
  ```pascal
  {$R+}  { Enable range checking }
  {$R-}  { Disable range checking }
  ```

- **`$Q`**: Enable or disable overflow checking.
  ```pascal
  {$Q+}  { Enable overflow checking }
  {$Q-}  { Disable overflow checking }
  ```

- **`$M`**: Set stack and heap sizes.
  ```pascal
  {$M 16384,0,655360}
  ```

- **`$DEFINE`** and **`$UNDEF`**: Define and undefine symbols.
  ```pascal
  {$DEFINE DEBUG}
  {$UNDEF DEBUG}
  ```

## Tips and Best Practices

### Use Meaningful Variable Names

Use descriptive names for variables, procedures, functions, and other identifiers to make your code more readable and maintainable.

```pascal
var
  totalAmount: real;
  studentName: string;
```

### Comment Your Code

Use comments to explain the purpose of your code, especially for complex logic. This helps others (and yourself) understand your code.

```pascal
{ Calculate the total amount after applying the discount }
totalAmount := price - (price * discount / 100);
```

### Consistent Indentation

Use consistent indentation to make your code more readable. Typically, two or four spaces are used for each level of indentation.

```pascal
if condition then
begin
  statement1;
  statement2;
end;
```

### Avoid Magic Numbers

Avoid using hard-coded numbers (magic numbers) in your code. Instead, use constants with meaningful names.

```pascal
const
  MaxStudents = 50;

var
  studentCount: integer;

begin
  if studentCount > MaxStudents then
    writeln('Error: Exceeds maximum number of students');
end;
```

### Modularize Your Code

Break your code into smaller, reusable procedures and functions. This makes your code more modular and easier to test and maintain.

```pascal
procedure PrintGreeting(name: string);
begin
  writeln('Hello, ', name);
end;

begin
  PrintGreeting('Alice');
end.
```

### Handle Errors Gracefully

Use error handling mechanisms to manage exceptions and unexpected situations in your code.

```pascal
try
  result := StrToInt(input);
except
  on E: EConvertError do
    writeln('Invalid number format');
end;
```

### Optimize for Performance

Optimize your code for performance by avoiding unnecessary calculations and using efficient algorithms and data structures.

```pascal
for i := 1 to n do
  result := result + array[i];
```

### Test Your Code Thoroughly

Thoroughly test your code to ensure it works correctly in all scenarios. Use both normal and edge cases in your testing.

```pascal
procedure TestAddition;
begin
  Assert(Add(2, 2) = 4);
  Assert(Add(-1, 1) = 0);
  Assert(Add(0, 0) = 0);
end;
```
