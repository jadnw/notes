# Basic Ideas

## Modern C++

- The C++ programming language was originally developed in the early 1908s by
Danish computer scientist Bjarne Stroustrup.

- Programms written in C++ are still easily many times faster than those written
in other popular languages.

## Standard libraries

- The *Standard Libraries* is a huge collection of routines and definitions that
provide functionality that is required by many programs such as numerical
calculations, string processing, sorting and searching, organizinggg and 
managing data, and input and output.

## C++ Program Concepts

### Source files and header files

- Source files contain functions and thus all the executable code in a program.
The name of source files usually have the extension *.cpp* (or *.cc*, *.cxx*, 
*.c++*)

- Header files contain, among other things, function prototypes and definitions
for classes and templates that are used by the executable code in a source file.
The name of header files usually have the extension *.h* (or *.hpp*)

### Comments and Whitespaces

- You add comments that document your program code to make it easier to
understand how it works. The compiler ignores all comments in your code.

```cpp
// This is a single line comment

/* This comment is
    over two lines. */
```

- Whitespaces is any sequence of spaces, tabs, newlines, or form feed characters,
generally ignored by the compiler, except when it is neccessary for syntactic
reasons to distinguish on element from another.

> Caution: There are no spaces between the angle brackets (\< and \>) and the
standard header file name. With some compilers, your program may not compile.

### Functions

- Function is a named block of code that carries out a well-defined operation
such as "read the input data" or "calculate the average value" or "output the 
results."

- There must be one function with the name *main*, and execution always starts
automatically with this function.

```cpp
int main() {
    // Everything goes here
}
```

### Statements

- Statement is a basic unit in a C++ program. A statement always ends with a
semicolon, and it's the semicolon that marks the end of statement, not end of
the line. It defines something, such as a computation, or an action that is to
be performed.

```cpp
int answer {42}; // This is a statement
```

### Data Input and Output

- Input and output are performed using *streams* in C++. To output something,
you write it to an output stream, and to input data, you read it from an input
stream.

- A *stream* is an abstract representation of a source of data or a data sink.

### return Statements

- A *return* statement ends a function and returns control to where the function
was called. It may or may not return a value.

- Returning 0 to the OS indicates that the program ended normally. Returning
nonzero values such as 1, 2, etc., to indicate different abnormal end conditions.

> Note: `main()` is the only function for which omitting return is equivalent to
returning zero. Any other function with return type `int` always has to end with
an explicit `return` statement.

### Namspaces

- Namespace is a sort of family name that prefixes all the names declared within
the namespace.

- Two colons (`::`) have a fancy title: *the scope resolution operator*.

> Caution: Things that are not defined in a namespace exist in the *global*
namespace, which has no name (including the `main()` function).

### Names and Keywords

- A lot of things need names in a program, and there are precise rules for
defining names.

- Keywords are reserved words that have a specific meaning in C++, so you must
use theme for other purposes.

> Tip: Do not use names that starts with an underscore.

## Classes and Objects

- A *class* is a block of code that defines a data type. A class has a name that
is the name for the type. An item of data of a class type is referred to as an
*object*.

## Templates

- A *template* is a recipe that you create to be used by the compiler to
generate code automatically for a class or function customized for a particular
type or types.

## Representing Numbers

### Binary Numbers

- Your PC is rather less handy, being built mainly of switches that are neither
on or off. It is OK for counting in twos but not spectacular at counting in tens.

- A binary digit is more commonly known as a *bit*.

- If you have n bits available, you can represent 2^n intergers, wtih positive
values from 0 to 2^n - 1.

### Hexadecimal Numbers

- Hexadecimal numbers help us dealing with larger binary numbers.

### Negative Binary Numbers

- All modern computers use the so-called *2's complement representation* of
negative binary numbers. To represent a negative value of a binary number, you
can *flip* all bits then add 1.

### Octal Values

> Caution: Never write decimal integers in your source code with a leading zero.
You will get a value different from what you intended.

### Bi-Endian and Little-Endian Systems

- The most significant byte of the value are stored with the highest address
(last, in other words). This arrangement is described as *little-endian*.

- The most significant eight bits are stored in the lowest address. This
arrangement is described as *bi-endian*.
