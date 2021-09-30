03 - Operators
==============
Now that we've covered how to declare and use variables, it's time to learn how to actually use them.
After all, what good is a variable if we can't do anything with it?

C++ uses the **operator precedence** to determine what order operators are executed in. Think of it like PEMDAS for computers.
You can see the full list of operators and their precedence [here,](https://en.cppreference.com/w/cpp/language/operator_precedence)
however I'm going to focus on the most important operators for now: `+`, `-`, `*`, `/`, and `%`.

Addition/Subtraction
--------
Adding two variables is incredibly simple. All you need to do is this:
```c++
int myVar1 = 3;
int myVar2 = 7;
int result = myVar1 + myVar2;
```
`result` is now equal to `myVar1` + `myVar2`, which is 10.

Or, say for example, if we want to increase the value of a variable by 1, we can do this:
```c++
int myVar = 10;
myVar = myVar + 1;
//myVar is now equal to 11
```
We can also increase or decrease it by more than one.
```c++
int myVar = 17;
myVar = myVar - 4;
//myVar is now equal to 13
```

Multiplication/Division/Modulo
------------------------------
Much like addition and subtraction, you can multiply or divide by using `*` and `/`.
```c++
int myVar = 3;
int product = myVar * 4;
//product is now equal to 12

int quotient = product / 2;
//quotient is now equal to 6. note that the value of myVar is unchanged
```
Beware of divison in particular. If you divide 5 by 2, for example, you'd expect to get the result 2.5.
However, this is not the case. The result is actually `2`, as the decimal is truncated as a result of integer divison.
If you had two int variables, and you want to divide them using floating point divison, you just need to cast one of them into a double or float.
```c++
int num1, num2;
num1 = 5;
num2 = 2;
double myQuotient = num1/(double)num2;
//result is 2.5
```
Make sure to store the result in a datatype that can handle decimals (so, floats or doubles.)

> Okay, but what's "modulo"?
Modulo is effectively the *remainder* of integer division. Take the example from earlier, 5 / 2.
The result is 2 (when using integer divison), and the remainder is 1. Thus, 5 % 2 is equal to 1.

Shortcuts
---------
Instead of writing something like `myVar = myVar + 4;`, you can actually use a shorthand operator.
Just type `myVar += 4;`. This works for all of the main operators, and thus `+=`, `-=`, `*=`, `/=`, and `%=` all exist and work as you'd expect.

Shortcuts of shortcuts
----------------------
You'll often find yourself needing to add one or subtract one from variables. You can of course do `+= 1` or `-= 1`, however there's once again an easier way.
`myVar++` is equal to `myVar += 1`, and `myVar--` is equal to `myVar-=1`.
