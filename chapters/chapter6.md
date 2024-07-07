# Chapter 6: Advanced Pascal Programming

In this chapter, we will explore some advanced programming concepts in Pascal, including file handling, dynamic memory allocation, and pointers. These topics will help you manage more complex data and interactions in your Pascal programs.

## File Handling

Pascal provides several built-in procedures and functions for file handling. Files can be used to store data permanently and retrieve it when needed.

### Types of Files

Pascal supports different types of files, including:
- **Text Files**: Used to store readable characters.
- **Binary Files**: Used to store data in binary format.

### Text Files

#### Declaring Text Files

```pascal
var
  fileName: text;
```

#### Writing to a Text File

```pascal
program WriteTextFile;

var
  fileName: text;
  i: integer;

begin
  assign(fileName, 'output.txt');
  rewrite(fileName);

  for i := 1 to 10 do
    writeln(fileName, 'Line number ', i);

  close(fileName);
end.
```

#### Reading from a Text File

```pascal
program ReadTextFile;

var
  fileName: text;
  line: string;

begin
  assign(fileName, 'output.txt');
  reset(fileName);

  while not eof(fileName) do
  begin
    readln(fileName, line);
    writeln(line);
  end;

  close(fileName);
end.
```

### Binary Files

#### Declaring Binary Files

```pascal
var
  binFile: file of dataType;
```

#### Writing to a Binary File

```pascal
program WriteBinaryFile;

type
  Student = record
    name: string[20];
    age: integer;
  end;

var
  binFile: file of Student;
  s: Student;

begin
  assign(binFile, 'students.dat');
  rewrite(binFile);

  s.name := 'Alice';
  s.age := 22;
  write(binFile, s);

  s.name := 'Bob';
  s.age := 24;
  write(binFile, s);

  close(binFile);
end.
```

#### Reading from a Binary File

```pascal
program ReadBinaryFile;

type
  Student = record
    name: string[20];
    age: integer;
  end;

var
  binFile: file of Student;
  s: Student;

begin
  assign(binFile, 'students.dat');
  reset(binFile);

  while not eof(binFile) do
  begin
    read(binFile, s);
    writeln('Name: ', s.name, ', Age: ', s.age);
  end;

  close(binFile);
end.
```

## Dynamic Memory Allocation

Dynamic memory allocation allows you to allocate memory at runtime. This is useful when you don't know the exact amount of memory needed during compile time.

### Using the `new` and `dispose` Procedures

```pascal
program DynamicMemory;

var
  p: ^integer;

begin
  new(p);  { Allocate memory }
  p^ := 10;
  writeln('Value: ', p^);
  dispose(p);  { Free memory }
end.
```

In this example, `p` is a pointer to an integer. The `new` procedure allocates memory for an integer, and `dispose` frees the allocated memory.

### Dynamic Arrays

Dynamic arrays allow you to allocate and manage arrays at runtime.

```pascal
program DynamicArray;

var
  arr: array of integer;
  i, n: integer;

begin
  writeln('Enter the size of the array: ');
  readln(n);

  setlength(arr, n);

  for i := 0 to n - 1 do
    arr[i] := i * 2;

  for i := 0 to n - 1 do
    writeln('arr[', i, '] = ', arr[i]);
end.
```

## Pointers

Pointers are variables that store the memory address of another variable. They are useful for dynamic memory allocation and accessing variables indirectly.

### Declaring Pointers

```pascal
var
  p: ^integer;
```

### Using Pointers

```pascal
program PointerExample;

var
  p, q: ^integer;
  x: integer;

begin
  new(p);
  p^ := 10;
  writeln('Value at p: ', p^);  { Output: 10 }

  x := 20;
  q := @x;
  writeln('Value at q: ', q^);  { Output: 20 }

  dispose(p);
end.
```

In this example, `p` and `q` are pointers to integers. The `new` procedure allocates memory for an integer, and the `@` operator is used to get the address of a variable.

### Pointer Arithmetic

Pascal does not support pointer arithmetic directly, but you can use it through arrays.

```pascal
program PointerArithmetic;

type
  IntArray = array[1..10] of integer;
  PIntArray = ^IntArray;

var
  arr: PIntArray;
  i: integer;

begin
  new(arr);

  for i := 1 to 10 do
    arr^[i] := i * 3;

  for i := 1 to 10 do
    writeln('arr[', i, '] = ', arr^[i]);

  dispose(arr);
end.
```
