Variables
==========

A variable simply represents something that we can use to hold data. To declare a variable, (in this case an integer), simply type the following:
```c++
int myVar;
```
Congratulations, you have now created your first variable! Let's break down what we just did.
```c++
 int myVar;
//|    |
//|    |
//|    this is the name of your variable. you can call it whatever you want,
//|    though there are a few restrictions (I'll get back to this later).
//|
//the type of the variable. there are many types available.
//some common ones you'll be using are int, string, bool, and double.
```

So now that we have a variable, what can we do with it? Well, the purpose of variables is to hold data for us, so about we assign some data. 
You do that using the `=` operator.

```c++
myVar = 3;
```

Now, our variable is representing the number 3. Note that because our variable is of type `int`, we can only assign integers to it.
Variables are one of the many fundamental parts of programming. 

Ok, but what if I need more variables?
--------------------------------------
Conveniently, the designers of the C/C++ programming langauges thought of everything, and it's possible to declare multiple variables in the same line,
so long as they're the same type. For example:
```c++
int firstVar, secondVar, thirdVar;

//now, we can use these variables individually.
firstVar = 23;
secondVar = -4;
thirdVar = 0;
```
Conveniently, you can also assign a variable inline (as long as you only have one.)
```c++
int myVar = 7;
```
Let's try assigning some variables of other types.
```c++
int myInt = 3;
double myDouble = -9.6; //note that doubles are "decimals", and thus can hold decimal values. floats are also decimals, but they're a little different
float myfloat = 10.4f;
long myLong = 103L; //a long literal requires a capital L at the end, to signify it is a long.
string myString = "hello"; //string literals use double quotes...
char myChar = 'h'; //while char literals use single quotes
bool myBoolean = false; //bool only represnets true or false
```
There are many other datatypes, but these are the main ones you'll be using.

Initial values of variables
---------------------------
When you declare a variable, but don't immediately assign it to something, it's value will be whatever was stored in that address of memory last, due to how memory  management works in most operating systems.
If you're using a variable and find that you're getting very large numbers or garbage data, it's most likely because you never actually assigned the variable to any particular value.

Help, my variable is pointy!
----------------------------
If you see a variable with a type similar to `int*`, then that means you're dealing with a pointer. Check out the page on pointers [here (if you're reading this, it probably doesn't exist yet.)](https://www.github.com/brod8362)
