# Chapter 5: Data Structures

Data structures are fundamental for organizing and managing data in a program. Pascal provides several built-in data structures that help you store, manage, and manipulate data efficiently. This chapter covers arrays, records, and sets.

## Arrays

An array is a collection of elements of the same type, stored in contiguous memory locations. Arrays allow you to store multiple values in a single variable and access them using an index.

### Declaring Arrays

```pascal
var
  arrayName: array[indexRange] of dataType;
```

### Example

```pascal
program ArrayExample;

var
  numbers: array[1..5] of integer;
  i: integer;

begin
  { Initializing array elements }
  for i := 1 to 5 do
    numbers[i] := i * 2;

  { Accessing array elements }
  for i := 1 to 5 do
    writeln('numbers[', i, '] = ', numbers[i]);
end.
```

In this example, `numbers` is an array of integers with indices ranging from 1 to 5. The array elements are initialized and accessed using a loop.

### Multidimensional Arrays

Pascal also supports multidimensional arrays. A common use case is a two-dimensional array, which can be visualized as a table with rows and columns.

#### Example

```pascal
program MultiArrayExample;

var
  matrix: array[1..3, 1..3] of integer;
  i, j: integer;

begin
  { Initializing matrix elements }
  for i := 1 to 3 do
    for j := 1 to 3 do
      matrix[i, j] := i * j;

  { Accessing matrix elements }
  for i := 1 to 3 do
  begin
    for j := 1 to 3 do
      write(matrix[i, j]:4);
    writeln;
  end;
end.
```

In this example, `matrix` is a two-dimensional array with 3 rows and 3 columns. The elements are initialized and accessed using nested loops.

## Records

A record is a composite data type that allows you to group different types of data together. Records are useful for representing complex data structures.

### Declaring Records

```pascal
type
  RecordName = record
    field1: dataType1;
    field2: dataType2;
    ...
  end;
```

### Example

```pascal
program RecordExample;

type
  Person = record
    name: string;
    age: integer;
    salary: real;
  end;

var
  employee: Person;

begin
  { Initializing record fields }
  employee.name := 'Alice';
  employee.age := 30;
  employee.salary := 50000.0;

  { Accessing record fields }
  writeln('Name: ', employee.name);
  writeln('Age: ', employee.age);
  writeln('Salary: ', employee.salary:0:2);
end.
```

In this example, `Person` is a record type with three fields: `name`, `age`, and `salary`. The `employee` variable is an instance of the `Person` record type.

## Sets

A set is a collection of elements of the same type, without duplicates. Sets are useful for operations involving membership, union, intersection, and difference.

### Declaring Sets

```pascal
var
  setName: set of baseType;
```

### Example

```pascal
program SetExample;

type
  Day = (Mon, Tue, Wed, Thu, Fri, Sat, Sun);

var
  weekdays, weekend: set of Day;

begin
  weekdays := [Mon, Tue, Wed, Thu, Fri];
  weekend := [Sat, Sun];

  { Set operations }
  if Tue in weekdays then
    writeln('Tuesday is a weekday');

  writeln('Weekend days: ');
  for var d in weekend do
    write(d, ' ');
end.
```

In this example, `Day` is an enumerated type representing days of the week. `weekdays` and `weekend` are sets of type `Day`. The program demonstrates membership checking and iterating over set elements.

### Set Operations

Pascal supports several set operations, including:

- **Union**: `+` or `include`
- **Intersection**: `*`
- **Difference**: `-`
- **Symmetric Difference**: `><`

#### Example

```pascal
program SetOperationsExample;

type
  Day = (Mon, Tue, Wed, Thu, Fri, Sat, Sun);

var
  setA, setB, resultSet: set of Day;

begin
  setA := [Mon, Wed, Fri];
  setB := [Wed, Thu, Fri, Sat];

  resultSet := setA + setB;  { Union }
  writeln('Union: ', resultSet);

  resultSet := setA * setB;  { Intersection }
  writeln('Intersection: ', resultSet);

  resultSet := setA - setB;  { Difference }
  writeln('Difference: ', resultSet);

  resultSet := setA >< setB;  { Symmetric Difference }
  writeln('Symmetric Difference: ', resultSet);
end.
```
