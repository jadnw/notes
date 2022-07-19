# Arrays and Loops

...


## The for Loop

- `size_t` is used for instances, for sizes and counts of things

> Note: `size_t` is not the name of a built-in fundamental type such as `int`,
`long` or `double`; it is a type alias defined by the Standard Library. More
specifically, it is an alias for one of the unsigned integer types, sufficiently
large to contain the size of any type the compiler supports (including any array).

> Caution: Array index values are not checked to verify that they are valid.
It's up to you to make sure that you don't reference elements outside the bounds
of the array. If you store data using an index value that's outside the valid
range for an array, you'll either inadvertently overwrite something in memory or
cause a so-called `segmentation fault` or `access violation`. Either way, your
program will almost certainly come to a sticky end.

...

## Determining the Size of an Array

> Note: The `std::size()` function works not only for arrays. It can be used with
any collection of elements defined by the Standard Library.

...

### Controlling a for Loop with Floating-Point Values

> Caution: You need to be careful when using a floating-point variable to control
a for loop. Fractional values may not be representable exactly as a binary
floating-point number. This can lead to some unwanted side effects.

> Caution: Compare floating-point numbers can be tricky. You should always be
cautious when comparing the result of floating-point computations directly using
operator such as `==`, `>=` or `<=`. Rounding errors almost always prevent the
floating-point value from ever becoming exactly equal to the mathetical precise
value.

### Controlling a for Loop with Unsigned Integers

> Caution: Take care when substracting from unsigned integers. Any value that
mathematically speaking should be negative then wraps around to become a huge
positive numbers. These types of errors can have catastrophic results in loop
control expressions.
