# Chapter 7: Object-Oriented Programming in Pascal

Object-oriented programming (OOP) is a paradigm that uses "objects" to design applications and programs. It allows for better data organization and modularity. In Pascal, OOP is implemented using classes and objects. This chapter will introduce the basic concepts of OOP in Pascal, including classes, objects, inheritance, polymorphism, and encapsulation.

## Classes and Objects

### Defining a Class

A class is a blueprint for creating objects. It defines properties (fields) and methods (procedures and functions) that the objects created from the class can use.

```pascal
type
  TPerson = class
    private
      FName: string;
      FAge: integer;
    public
      constructor Create(name: string; age: integer);
      procedure Display;
  end;
```

### Implementing the Class Methods

```pascal
constructor TPerson.Create(name: string; age: integer);
begin
  FName := name;
  FAge := age;
end;

procedure TPerson.Display;
begin
  writeln('Name: ', FName);
  writeln('Age: ', FAge);
end;
```

### Creating Objects

```pascal
var
  person: TPerson;

begin
  person := TPerson.Create('Alice', 30);
  person.Display;
  person.Free;
end.
```

## Inheritance

Inheritance allows a class to inherit properties and methods from another class. This helps in reusing code and creating a hierarchical relationship between classes.

### Defining a Base Class and a Derived Class

```pascal
type
  TPerson = class
    private
      FName: string;
      FAge: integer;
    public
      constructor Create(name: string; age: integer);
      procedure Display; virtual;
  end;

  TEmployee = class(TPerson)
    private
      FSalary: real;
    public
      constructor Create(name: string; age: integer; salary: real);
      procedure Display; override;
  end;
```

### Implementing the Methods

```pascal
constructor TPerson.Create(name: string; age: integer);
begin
  FName := name;
  FAge := age;
end;

procedure TPerson.Display;
begin
  writeln('Name: ', FName);
  writeln('Age: ', FAge);
end;

constructor TEmployee.Create(name: string; age: integer; salary: real);
begin
  inherited Create(name, age);
  FSalary := salary;
end;

procedure TEmployee.Display;
begin
  inherited Display;
  writeln('Salary: ', FSalary:0:2);
end;
```

### Creating Objects of Derived Class

```pascal
var
  employee: TEmployee;

begin
  employee := TEmployee.Create('Bob', 25, 55000.0);
  employee.Display;
  employee.Free;
end.
```

## Polymorphism

Polymorphism allows methods to be called based on the actual object type, even if the reference is of a base class type. This is achieved using virtual methods and method overriding.

### Example of Polymorphism

```pascal
var
  person: TPerson;
  employee: TEmployee;

begin
  person := TPerson.Create('Charlie', 40);
  employee := TEmployee.Create('Dave', 28, 62000.0);

  person.Display;     { Calls TPerson's Display }
  employee.Display;   { Calls TEmployee's Display }

  person := employee; { Assigning derived class object to base class reference }
  person.Display;     { Calls TEmployee's Display due to polymorphism }

  person.Free;
  employee.Free;
end.
```

## Encapsulation

Encapsulation is the concept of hiding the internal state and requiring all interaction to be performed through an object's methods. It promotes modularity and protects object integrity.

### Example of Encapsulation

```pascal
type
  TBankAccount = class
    private
      FBalance: real;
    public
      constructor Create(initialBalance: real);
      procedure Deposit(amount: real);
      procedure Withdraw(amount: real);
      procedure DisplayBalance;
  end;

constructor TBankAccount.Create(initialBalance: real);
begin
  FBalance := initialBalance;
end;

procedure TBankAccount.Deposit(amount: real);
begin
  if amount > 0 then
    FBalance := FBalance + amount;
end;

procedure TBankAccount.Withdraw(amount: real);
begin
  if (amount > 0) and (amount <= FBalance) then
    FBalance := FBalance - amount;
end;

procedure TBankAccount.DisplayBalance;
begin
  writeln('Balance: ', FBalance:0:2);
end;
```

### Using the Encapsulated Class

```pascal
var
  account: TBankAccount;

begin
  account := TBankAccount.Create(1000.0);
  account.Deposit(500.0);
  account.Withdraw(200.0);
  account.DisplayBalance;  { Output: Balance: 1300.00 }
  account.Free;
end.
```
