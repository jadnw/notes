# Introducing Fundamental Types of Data

## Variables, Data, and Data Types

### Define Integer Variables

- To define a variable

```cpp
int apple_count {15}; // brace initializer
int orange_count(5); // functional notation
int total_fruit = apple_count + orange_count; // assignment notation
```

- A *narrowing conversion* is a conversion to a type with a more limited range
of values.

- Brace initializer will cause at least a compiler warning, often an error when
its definition contains a narrowing conversion.

### Signed & Unsigned Integer Types

> Tip: Only use variables of the unmodified `char` type to store characters. For
`char` variables that store other data such as plain integer numbers, you should
always add the appropriate sign modifier.

> Note: `signed` is short for `signed int`, `unsigned` is short for `unsigned int`

### Zero Initialization

- Zero initialization works for any fundamental types.

```cpp
int counter {}; // counter starts at zero
```

...

## Mixed Expressions and Type Conversions

> Note: The phenomenon where the result of a subtraction of unsigned integers
wraps around a very large numbers is sometimes called *underflow*. Naturally,
the converse phenomenon exists as well is called *overflow*. The outcome of
overflow and underflow with signed integers is undefined, depends on the compiler
and computer architecture you are using.

...

### Working with Characters

- To define an ASCII character.

```cpp
char yes {'Y'};
```

- To define a *wide-character* 

```cpp
wchar_t wch {L'Z'}; // Character Z, prefix with L
wchar_t wch {L'\x0438'}; // Cyrillic
```

- Better way to handle international characters

```cpp
char16_t ch {u'Z'}; // Store character encoded as UTF-16, prefix with u
char32_t ch {U'Z'}; // Store character encoded as UTF-32, prefix with U
```
