# Chapter 9: Pascal Standard Libraries

Pascal provides several standard libraries (also known as units) that offer a wide range of functionality, from basic input/output to mathematical computations and string manipulation. Understanding and utilizing these libraries can significantly enhance your productivity and the capabilities of your programs. This chapter will cover some of the most commonly used Pascal standard libraries: `crt`, `SysUtils`, and `Math`.

## The CRT Unit

The `crt` unit provides functions and procedures for handling console input and output, as well as managing the screen.

### Including the CRT Unit

To use the `crt` unit, include it in the `uses` clause of your program.

```pascal
uses crt;
```

### Clearing the Screen

```pascal
begin
  ClrScr;
  writeln('Screen cleared!');
end.
```

### Moving the Cursor

```pascal
begin
  GotoXY(10, 5);
  writeln('Cursor moved to position (10, 5)');
end.
```

### Changing Text Color

```pascal
begin
  TextColor(Red);
  writeln('This text is red.');
  TextColor(White);
end.
```

### Pausing the Program

```pascal
begin
  writeln('Press any key to continue...');
  ReadKey;
end.
```

## The SysUtils Unit

The `SysUtils` unit provides a variety of system-related utilities, including string manipulation, file handling, date and time operations, and error handling.

### Including the SysUtils Unit

To use the `SysUtils` unit, include it in the `uses` clause of your program.

```pascal
uses SysUtils;
```

### String Manipulation

#### Converting Strings to Numbers

```pascal
var
  str: string;
  num: integer;

begin
  str := '123';
  num := StrToInt(str);
  writeln('Converted string to integer: ', num);
end.
```

#### Converting Numbers to Strings

```pascal
var
  num: integer;
  str: string;

begin
  num := 456;
  str := IntToStr(num);
  writeln('Converted integer to string: ', str);
end.
```

### File Handling

#### Checking if a File Exists

```pascal
var
  fileName: string;

begin
  fileName := 'test.txt';
  if FileExists(fileName) then
    writeln('File exists.')
  else
    writeln('File does not exist.');
end.
```

#### Deleting a File

```pascal
var
  fileName: string;

begin
  fileName := 'test.txt';
  if DeleteFile(fileName) then
    writeln('File deleted.')
  else
    writeln('Failed to delete file.');
end.
```

### Date and Time Operations

#### Getting the Current Date and Time

```pascal
var
  now: TDateTime;

begin
  now := Now;
  writeln('Current date and time: ', DateTimeToStr(now));
end.
```

#### Formatting Date and Time

```pascal
var
  now: TDateTime;

begin
  now := Now;
  writeln('Formatted date: ', FormatDateTime('yyyy-mm-dd', now));
  writeln('Formatted time: ', FormatDateTime('hh:nn:ss', now));
end.
```

## The Math Unit

The `Math` unit provides mathematical functions and constants.

### Including the Math Unit

To use the `Math` unit, include it in the `uses` clause of your program.

```pascal
uses Math;
```

### Common Mathematical Functions

#### Calculating the Square Root

```pascal
var
  x, result: real;

begin
  x := 16.0;
  result := Sqrt(x);
  writeln('Square root of ', x:0:2, ' is ', result:0:2);
end.
```

#### Calculating the Power of a Number

```pascal
var
  base, exponent, result: real;

begin
  base := 2.0;
  exponent := 3.0;
  result := Power(base, exponent);
  writeln(base:0:2, ' raised to the power of ', exponent:0:2, ' is ', result:0:2);
end.
```

### Constants

#### Mathematical Constants

```pascal
begin
  writeln('Value of Pi: ', Pi:0:10);
end.
```
