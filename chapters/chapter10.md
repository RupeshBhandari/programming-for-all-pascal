# Chapter 10: Practical Applications

In this chapter, we will explore practical applications of Pascal. We will build a calculator, develop a simple game, and create a basic database application. These examples will demonstrate how to apply the concepts you have learned so far in real-world scenarios.

## Building a Calculator

We will create a simple calculator that can perform basic arithmetic operations: addition, subtraction, multiplication, and division.

### Calculator Program

```pascal
program Calculator;

uses
  crt, SysUtils;

var
  num1, num2, result: real;
  operation: char;

begin
  ClrScr;

  writeln('Simple Calculator');
  writeln('-----------------');

  writeln('Enter first number: ');
  readln(num1);

  writeln('Enter an operation (+, -, *, /): ');
  readln(operation);

  writeln('Enter second number: ');
  readln(num2);

  case operation of
    '+': result := num1 + num2;
    '-': result := num1 - num2;
    '*': result := num1 * num2;
    '/': if num2 <> 0 then
           result := num1 / num2
         else
         begin
           writeln('Error: Division by zero');
           exit;
         end;
  else
    writeln('Error: Invalid operation');
    exit;
  end;

  writeln('Result: ', result:0:2);
end.
```

### Explanation

1. The program prompts the user to enter two numbers and an operation.
2. It uses a `case` statement to perform the appropriate arithmetic operation based on the user's input.
3. The result is displayed to the user.

## Simple Game Development

We will create a simple guessing game where the user has to guess a randomly generated number.

### Guessing Game Program

```pascal
program GuessingGame;

uses
  crt, SysUtils;

var
  secretNumber, guess: integer;
  attempts: integer;

begin
  ClrScr;

  Randomize;
  secretNumber := Random(100) + 1;  { Generate a random number between 1 and 100 }
  attempts := 0;

  writeln('Guess the Number Game');
  writeln('---------------------');

  repeat
    writeln('Enter your guess (1-100): ');
    readln(guess);
    attempts := attempts + 1;

    if guess < secretNumber then
      writeln('Too low!')
    else if guess > secretNumber then
      writeln('Too high!')
    else
      writeln('Congratulations! You guessed the number in ', attempts, ' attempts.');
  until guess = secretNumber;
end.
```

### Explanation

1. The program generates a random number between 1 and 100.
2. It prompts the user to guess the number and provides feedback on whether the guess is too low, too high, or correct.
3. The game continues until the user guesses the correct number.

## Database Applications

We will create a simple database application to store and manage student records. Each student record will include a name and an age.

### Student Record Program

```pascal
program StudentDatabase;

uses
  crt, SysUtils;

type
  Student = record
    name: string[50];
    age: integer;
  end;

var
  students: array[1..100] of Student;
  studentCount: integer;

procedure AddStudent(name: string; age: integer);
begin
  if studentCount < 100 then
  begin
    studentCount := studentCount + 1;
    students[studentCount].name := name;
    students[studentCount].age := age;
  end
  else
    writeln('Error: Student database is full.');
end;

procedure ListStudents;
var
  i: integer;
begin
  writeln('Student List:');
  writeln('-------------');
  for i := 1 to studentCount do
    writeln(i, ': ', students[i].name, ', Age: ', students[i].age);
end;

var
  choice: char;
  name: string;
  age: integer;

begin
  ClrScr;
  studentCount := 0;

  repeat
    writeln('Student Database');
    writeln('----------------');
    writeln('1. Add Student');
    writeln('2. List Students');
    writeln('3. Exit');
    writeln('Enter your choice: ');
    readln(choice);

    case choice of
      '1':
        begin
          writeln('Enter student name: ');
          readln(name);
          writeln('Enter student age: ');
          readln(age);
          AddStudent(name, age);
        end;
      '2': ListStudents;
      '3': writeln('Exiting...');
    else
      writeln('Invalid choice.');
    end;

    writeln;
  until choice = '3';
end.
```

### Explanation

1. The program uses a record type to define a student with a name and an age.
2. It maintains an array of student records and a count of the number of students.
3. The `AddStudent` procedure adds a new student to the array.
4. The `ListStudents` procedure lists all the students in the database.
5. The main program provides a menu for the user to add students, list students, or exit the program.
