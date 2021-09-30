00 - Hello, World!
----------------
Welcome to my beginner course/reference on C++!
I'm going to be covering the basics and foundations of C++, which you can use to learn new concepts or review old ones.
There will also be challenge problems with solutions that you can use for practice.

But first, let's look at everyone's first ever program: Hello, World!

```c++
#include <iostream>

using namespace std;

int main() {
  
  cout << "Hello, World!" << endl;
  
  return 0;
}
```

Now, if you compile and run this program, the output will be `Hello, World!`. 
Pretty cool, but clearly there's a lot of things missing here that make this program useful.

For example, how can we read input from a user? And how do we store that? And how can we store *multiple* values? And what about my own functions?
Luckily for you, all of this will be covered in due time. Check out Article [01 - Variables](https://github.com/Brod8362/cpp-for-dummies/blob/main/variables.md) to start.

Compiling manually
------------------
If you're running linux or just can't get your IDE to cooperate, then it's important to know how to compile and run your code manually.
In the event that your main function is in a file called `myProgram.cpp` (note that .cxx is also an acceptable file extension), then just run this in a terminal window:

> `g++ -Wall myProgram.cpp` 

Your code will be compiled and stored into a file. On Linux/macOS systems, this file will be called `a.out`. On windows, it will be called `a.exe`.
You can now execute it by running `./a.out` in your terminal (Linux/macOS), or `./a.exe` for Windows. You can also just double click on it in file explorer on windows.

What are these scary messages when I compile?
---------------------------------------------
The `-Wall` flag means "warn all", and will give you warnings for any potential issue it finds.
- If the text is highlighted in blue or pink, then it means it won't stop your program from compiling, but there's a solid chance it is a problem or may cause unintended behavior.
- If the text is highlted in red, that means it is an error, and your program will NOT compile. You will need to fix the error before being able to compile your code.

(If your terminal doesn't support color text, it does say `warning`, `info`, or `error` at the beginning of the lines.)

I don't have `g++`!
-------------------
That means you need to install a compiler. 

For Windows, your best bet is following [this guide](https://code.visualstudio.com/docs/cpp/config-mingw) by microsoft. (Sorry, I don't use windows, and have little experience developing on it.)

If you're running Linux, check your package manager. For Arch Linux, you need to install the `base-devel` group. On Ubuntu, you can just install the `g++` package.
If you're running another flavor of Linux, you should be able to search through your package manager and find something similar.

On macOS, it's incredibly easy. The first time you to try run `g++` (if you don't have it), a window will pop up asking you to install it. Just click OK and the hard work will be done for you.
