06 - Scope
==========

Scope is one of the most important concepts to understand, not only for writing code but also for reading code, and debugging it. 
As any programmer can tell you, new or experienced alike, debugging code can be one of the most time consuming things you'll do while programming.

One of the most common problems I've seen is newer programmers wondering why they're getting errors when trying to use a variable they made. "I declared it, so why can't I use it?"
99% of the time, the problem is that they're not considering scope, and how it plays into your code, both for you (e.g, using variables, or changing them) and for the computer (memory management)


How it works
------------
Let's take the following code snippet:
```c++
int i;
for (i = 0; i < 5; i++) {
  cout << i << " ";
}

```
This code's function is pretty obvious: it's a for loop which prints the numbers 0-4 inclusive. However, there's one vital flaw with this code which may cause unintended errors.
That problem is the scope of the variable `i` - it's never used after the loop, and there's a solid chance it isn't meant to be used agian. 
However, because of *where* it's defined, that variable will still exist and be usable after the loop. 
Compare this to the other way of using a for loop:
```c++
for (int i = 0; i < 5; i++) {
  cout << i << " ";
}
```
While this code may work in exactly the same way, there's one very significant difference: **`i` will not be accessible after the loop.**
This can prevent you from accidentally using it again later when you didn't intend to. 

As a general rule of thumb: any time you use curly braces (`{}`), you're entering a new "layer" of scope. 
Inner layers of scope can access the layers further outside, however outside layers cannot reach in. For example:
```c++
int var;
cin >> var; //only var exists, and is accessible at this point
if (var == 3) {
  string var2; //both var and var2 exist, and both are accessible
  cin >> var2;
  if (var2 == "hello") {
    double var3; //var, var2, and var3 all exist and are accessible.
  }
  //var3 ceases to exist, and is no longer accessible.
}
//var2 ceases to exist, and is no longer accessible.
```
The above example is also true for for loops, while loops, functions, and more. There is one notable exception which can really catch you off if you're not ready for it.
That case is when using **switch** cases. Let's take an example of a typical switch case:
```c++
int input;
cin >> input;
switch (input) {
  case 1:
    int i = 5;
    break;
  case 2:
    int i = 6;
    break;
  case 3:
    int i = 8;
    break;
  default:
    int i = 9;
    break;
}
```
The above code will not compile, and will cite a lot of errors: the most common one you'll see is `redeclaration of : 'int i'`.
The reason for this is because a switch case is treated as **labels**, which the code will jump to directly.
If you're familiar with assembly and how processors work at a lower level, you'll understand what that means. But in layman's terms, you **cannot define variables within a switch statement**.
Here's some examples of other errors you'll get if you try to define variables within a switch statement:
- **error**: jump to case label
- **error**: redeclaration of (identifier)
- **note**: crosses initialization of (identifier)
- **note**: (identifier) previously declared here 

Best practices
--------------
Let's take a look at some poor use of scope, and how it can be improved.

Bad:
```c++
const int SIZE = 10;
string arr[SIZE];
string myInput;
for (int i = 0; i < SIZE; i++) {
  cin >> myInput;
  arr[i] = myInput;
}
//more code after...
```
**The Problem:** the variable `myInput` will continue to exist after the for loop, which is likely not intended. In this case, it will be assigned to the last value that was entered.
It is not a good idea to allow variables like to exist if you don't plan on using it later, as it may lead to unintended uses.
Good:
```c++
const int SIZE = 10;
string arr[SIZE];
for (int i = 0; i < SIZE; i++) {
  string myInput;
  cin >> myInput;
  arr[i] = myInput;
}
//more code after...
```
This code ensures that `myInput` will no longer exist after the loop. Note that in this particular example, there is no need for the variable at all, and you could just write into the array directly.
However, it's just a common error that is made by newer programmers.

Scope with classes
------------------
While classes have not yet been covered if you're following these in order, classes are an important thing to mention when talking about the scope of variables.
Let's say we have a class like this:
```c++
class Person {
  public:
    Person(int a,string n, double w)
    int GetAge();
    string GetName();
    double getWeight();
    
  private:
    int age;
    string name;
    double weight;
}
```
And later we have an implementation of say, `GetAge()`.
```c++
int Person::GetAge() {
  return age;
}
```
Where is it pulling the value `age` from? Well, because this function is a member of the class `Person`, it is able to access it's private members such as `age`, `name`, and `weight`.
You must be mindful of this when naming variables in your function, as trying to name a variable with the same name may cause weird errors.
