# Pointers and References

## What is a Pointer?

- A *pointer* is a variable that can store an address of another variable, of 
some piece of data elsewhere in memory.

- Each pointer points to *a particular type of data item at that address*.

> Tip: You should always initialize a pointer when you define it. If you cannot
give it its intended value yet, initialize the pointer to `nullptr`.

- No matter the type or size of the data a pointer refers to, though, the size
of the pointer variable itself will *always the same*.

## The Address-Of Operator

- The *address-of* operator, &, is a unary operator that obtains the address of
a variable.

## The Indirection Operator

- Applying the *indirection operator* (*dereference operator*), *, to a pointer 
accesses the contents of the memory location to which it points.

...

## Constant Pointers and Pointers to Constants

- *A pointer to a constant*: You can't modify what's pointed to, but you can set
the pointer to point to something else.

```cpp
const char* pstring {"Some text that cannot be changed"};
const int value {20};
const int* pvalue {&value};
```

- *A constant pointer*: The address stored in the pointer can't be changed.
A constant pointer can only ever point to the address that it's initialized with.

```cpp
int data {20};
int* const pdata {&data};
```

> Tip: You can read all type names right to left

```cpp
float const * const pvalue {&value};
const float * const pvalue {&value}; // equivalent
```

...

## Pointers and Arrays

- Because an array name can be interpreted as an adress, you can use one to
initialize a pointer as well.

```cpp
double values[10];
double* pvalues {values}; // instead of &values
```

## The Difference Between Pointers

- The difference between two pointers is again measured in terms of elements,
not in terms of bytes.

## Dynamic Memory Allocation

- *Dynamic memory allocation* is allocating the memory you need to store the
data you're working with at runtime, rather than having amount of memory predefined
when the program is compiled. You can change the amount of memory your program
has dedicated to it as execution progresses.

## The Stack and the Free Store

- *The stack* is the space for an automatic variable is allocated in memory.
It has a fixed size that is determined by your compiler. At the end of the block
in which an automatic variable is defined, the memory allocated for the variable
on the stack is released and is thur free to be reused. When you call a funciton,
the arguments you pass to the function will be stored on the stack along with the
address of the location to return to when execution of the function ends.

- *The free store* (the heap) is the memory that is not occupied by the operating
system or other programs that are currently loaded.

- The `new` operator to request the space be allocated within the free store at
runtime for a new variable of any type. The `delete` operator releases memory
that you previously allocated with `new`.

- You can allocate space in the free store for variables in one part of a program
and then release the space and return it to the freestore in another part of 
the program when you no longer need it.

- If the memory isn't released by the `delete` operator, it will be released
automatically when program execution ends.

## Dynamic Allocation of Arrays

- To remove the array from a free store when you are done with it, use `delete[]`:

```cpp
delete[] data;
```

## Member Selection Through a Pointer

- The `->` operator is refered to as the *arrow operator* or *indirection member
selection operator*.

```cpp
auto* pdata {new std::vector<int>{}};
(*pdata).push_back(66);
pdata->push_back(66); // equivalent
```

## Hazard of Dynamic Memory Allocation

### Dangling pointers and Multiple Deallocations

- A *dangling pointer* is a pointer variable that still contains the address to
free store memory that has already been deallocated by either `delete` or
`delete[]`.

- *Multiple deallocations* occur when you deallocate an already deallocated
(and hence dangling) pointer for a second time using either `delete` or `delete[]`.

> Caution: Every `new` must be paired with a single `delete`; every `new[]` must
be paired with a single `delete[]`. Any other sequence of events leads to either
undefined behavior or memory leaks.

## Golden Rule of Dynamic Memory Allocation

> Tip: Never use the operator `new`, `new[]`, `delete` and `delete[]` directly
in day-to-day coding. These operators have no place in modern C++ code. Always
use either the `std::vector<>` container (to replace dynamic arrays) or a smart
pointer (to dynamically allocate objects and manage their lifetimes). These
high-level alternatives are much, much safer than the low-level memory
management primitives and will help you tremendously by instantly eradicating
all dangling pointers, multiple allocations, allocation/deallocation mismatches,
and memory leaks from your programs.

## Raw Pointers vs Smart Pointers

Smart pointer types are defined by templates inside the `memory` header of the
Standard Library, so you must include this in your source file to use them.
There are three types of smart pointers, all defined in `std` namespace:

- A `unique_ptr<T>` object behaves as a pointer to type `T` and is "unique" in
the sense that there can only one single `unique_ptr<T>` object containing the
same address.

- A `shared_ptr<T>` object behaves as a pointer to type `T`, but in contrast with
`unique_ptr<T>`, there can be any number of `shared_ptr<T>` objects that contain
the same address. Thus, `shared_ptr<>` objects allow *shared ownership* of an
object in the free store. At any given moment, the number of `share_ptr<>` objects
that contain a given address in time is known by the runtime. This is called 
*reference counting*.

- A `weak_ptr<T>` is linked to a `shared_ptr<T>` and contains the same address.
Creating a `weak_ptr<>` does not increment the reference count associated to the
linked `shared_ptr<>` object, though, so a `weak_ptr<>` does not prevent the
object pointed to from being destroyed. Its memory will be released when the last
`shared_ptr<>` referencing it is destroyed or reassigned to point to a different
address, even when associated `weak_ptr<>` objects still exist. If this happens,
the `weak_ptr<>` will nevertheless not contain a dangling pointer, at least not
one that you could inadvertently access.

### Using `unique_ptr<T>` Pointers

> Tip: To create a `std::unique_ptr<T>` object that points to a newly allocated
`T` value, always use the `std::make_unique<T>` function. This function is safer
as well against some more subtle memory leaks.

> Tip: It is mostly recommended to use a `vector<T>` container instead of an
`unique_ptr<T[]>`. A `vector<T>` is far more powerful and flexible than the smart
pointer.

> Caution: Never call `release()` without capturing the raw pointer that comes
out. This introduces a whopping memory leak, can not applied `delete` or `delete[]`.

...

## Understanding References

- A *reference* is a name that you can use as an alias for another variable.
Unlike a pointer, you cannot declare a reference and not initialize it. Because
a reference is an alias, the variable for which it is an alias must be provided
when reference is initialized.

- A reference cannot be modified to be an alias for something
else. Once it is initialized as an alias for some variable, it keeps referring
to that same variable for the remainder of its lifetime.

- You can use a reference as an alternative to the original variable name.

- A reference variable is thus much like `const` pointer variable
