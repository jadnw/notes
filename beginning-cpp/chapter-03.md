# Working with Fundamental Data Types

...

## Bitwise Operators

### Bitwise Shift Operators

> Caution: The result value of a bitwise shift operator is of type `int`.
Without `static_cast<>`, your compiler would issue at least a compiler warning
to signal the narrowing conversion, or it might even refuse to compile the
assignment altogether.

...

### Enumerated Data Types

- To define an enumeration

```cpp
enum class Day { Mon, Tue, Wed, Thur, Fri, Sat, Sun }; // default type int
enum class Punctuation : char { Comma = ',', Exclamation = '!', Question = '?' }; // type char
```

> Note: The more strongly typed `enum class`es are alway better choice over 
old-style `enum` types. Old-style enumerators convert value of integral or even
floating-point types without a cast.

## Aliases for Data Types

- To define a type as being equivalent to a standard type

```cpp
using BigOnes = unsigned long long
typedef unsigned long long BigOnes; // old-style
```

> Tip: Always use `using` to define a type alias in new code.

...

## Global Variables

> Tip: Using the scope resolution operator `::` to access or modify a global variable

```cpp
#include <iostream>

int count = 0;

int main() {
    int count = 1;
    std::cout << count << std::endl; // 1
    std::cout << ::count << std::endl; // 0
}
```


