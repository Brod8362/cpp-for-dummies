04 - Input/Output
=================

The programs you use every day require input and output for them to be useful. Imagine a web browser where you can't interact with anything, 
or an e-reader but all the pages are blank. Learning to use basic input and output is incredibly important to writing useful programs.

For now, we're going to focus on the basic means of IO: `cin` and `cout`. `cin` represents stdin, and `cout` represents stdout. 
These are the standard streams of input and output for any program running on your computer. 
As our program is running in a terminal, we just type into the terminal to use `cin` and the program outputs to the terminal with `cout`.

cout
----
Let's try outputting something to the screen. You may remember from the [Hello, World]() lesson that we used cout and some weird operator that looked like this `<<`.
This operator is called the **insertion** operator. I'll cover it more in details in the streams lesson, but for now just know that its putting data *into* `cout`'s buffer.

```c++
#include <iostream> //you must include iostream to use cin/cout

using namespace std; //if you don't do this, you'll have to type std::cin and std::cout every time.

int main() {
  cout << "Hello, my name is bob.";
  cout << "Hello, my name is joe.";
  return 0;
}
```

Here's an example of a complete program that prints to stdout. If you run this code, you'll see that it does work as intended, however, it all prints to one line!
That's because we need to *also* insert `endl`, which is a special character that represents the end of the line. (It also flushes the buffer of the stream, but that is once again not relevant right now.)

Let's edit our program to include `endl`:

```c++
//from now on, everything outside of the main function will be truncated for brevity
int main() {
  cout << "Hello, my name is bob." << endl;
  cout << "Hello, my name is joe." << endl;
  return 0;
}
```
Compile and run this new code and you'll find that now it prints out on separate lines. Hooray!

`cout` isn't only limited to strings. It can print any primitive datatype, and also user-defined data types if you overload the correct function.
For example:
```c++
int year = 1999;
cout << "Party like it's " << year << endl;
```

cin
---
Now that we can output something from our program, let's ask the user for their name, and then print it out.
```c++
int main() {
  string name;
  cout << "Hello. What is your name?" << endl;
  cin >> name;
  cout << "Hello, " << name << endl;
  return 0;
}
```
Notice that when we use `cin`, the 'arrows' are pointing the other way (`>>`). 
This is called the **extraction** operator, and is extracting data from `cin` and putting it into the variable `name`.
More importantly, it will extract as much data as it can from `cin` until the variable it's writing into cannot take any more information.
For example, let's say we have this code snippet:
```c++
int myInt;
string myStr;
cin >> myInt;
cin >> myStr;
```
and you input "43hello", what will happen?

`cin >> myInt` will read as much of "43hello" that it can - in this case, 43. So, `myInt` is set to 43, and "hello" is still on the buffer of `cin`.
Then, when `cin >> myStr` executes, whatever is left on cin is put into `myStr`, as strings can hold anything that `cin` has on the buffer.

Practice Problem
----------------
Can you write a program that asks for information from the user, and outputs it in a specific format?

INPUT:
```
Joe
blue
35
```
OUTPUT:
```
Hi, What is your name?
What is your favorite color?
How old are you?
Hello, Joe. I see you like the color blue. You are 35 years old.
```

<details>
  <summary> Solution code </summary>
  
  ```c++
  #include <iostream>
  
  using namespace std;
  
  int main() {
    string name, color;
    int age;
    cout << "Hi. What is your name?" << endl;
    cin >> name;
    cout << "What is your favorite color?" << endl;
    cin >> color;
    cout << "How old are you?" << endl;
    cin >> age;
    cout << "Hello, " << name << ". I see you like the color " << color << ". You are " << age << " years old." << endl;
    return 0;
  }
  ```
  
</details>
