02 - Datatypes
=========
**Ok, so now I can make a variable. But what does `int` mean?!**

Well, looks like it's time to go over the *primitive types* that C/C++ have to offer.

| **typename** | **description**                                         | **size (bytes, x86-64)** | **range of values**                                               |
|--------------|---------------------------------------------------------|--------------------------|-------------------------------------------------------------------|
| `int`        | An integer number                                       | 4                        | -2147483648 to 2147483647 (signed) 0 to 4294967295 (unsigned)     |
| `long`       | A "larger"¹ int                                         | 4                        | -2147483648 to 2147483647 (signed) 0 to 4294967295 (unsigned)     |
| `long long`  | An actually larger int                                  | 8                        | (-2^63) to (2^63)-1 (signed) 0 to 18446744073709551615 (unsigned) |
| `short`      | A smaller in                                            | 2                        | -32767 to 32767 (signed) 0 to 65535 (unsigned)                    |
| `char`       | A single character. Interchangeable with `byte`.        | 1                        | -127 to 127 (signed) 0 to 255 (unsigned)                          |
| `bool`       | A true or false value.                                  | 1                        | true, false                                                       |
| `void`       | The concept of nothing.                                 | N/A                      | N/A                                                               |
| `float`      | A decimal number, called "floating point".              | 4                        | It's complicated                                                  |
| `double`     | A larger version of a float, capable of more precision. | 8                        | It's complicated                                                  |
| `byte`       | A single byte. Interchangeable with `char`.             | 1                        | -127 to 127 (signed) 0 to 255 (unsigned)                          |
The size for all types is repesented in bytes on a modern, x86 64 bit system using GCC. Sizes may differ when running a system of different architecture.


int vs long
-----------
`int` vs `long` is an interesting tidbit of history, as they're both the same size in bytes, and thus hold the same values.  So why does `long` exist?
It used to be that `int` was actually a 2-byte datatype (16 bits), and `long` was 4 bytes. 
As technology advanced, and we moved from 16 bit computing to 32 bit computing (and nowadays, 64bit computing),`int` was expanded to be 4 bytes in size, 
however `long` also remained 4 bytes. This is why `long long` and `short` were created - `short` filled the 2-byte type gap, and `long` represents something
actually longer than an `int`. (Typically 8 bytes.)

signed vs unsigned
------------------
Computers represent numbers in binary, a series of 1s and 0s. Most normal people count in base 10, which means we have 10 possible "numbers" to work with: 0-9.
However, computers work with base 2 (binary), and the only values that exist are 0 and 1. 
We count like `1, 2, 3, 4` but computers count like `1, 10, 11, 100`. 

This is important, as when we only have a set number of bits to work with (in the case of an `int`, 4 bytes * 8 bits ber byte = **32 bits**), there's inherently a limited range of values we can represent.
If we choose to represent our variables including negatives, we have to give up a single bit to represent sign. Because of how binary numbers work, this means we cut our maximum value in half, but gain the ability to represent negative numbers.

void
----
`void` is a special datatype in that it represents nothing. You can't have a `void` variable (with the exception of `void*` but we'll get to that when we cover pointers),
but you *can* have a function that returns `void`. All that means is that the function returns nothing 

