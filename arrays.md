04 - Arrays
===========

So being able to store values is pretty nice, but it would be even better if we could bundle multiple of the same value together into a group.

Once again, C++ has our back, and there are a multitude of different ways available to us to do this.
For now, let's just worry about two - Arrays and vectors.

Arrays (static)
---------------
### Creating
Creating an array is incredibly easy. For example, let's say we want to create an array that can hold 5 values. then all we need to do is this:
```c++
int myArray[5];
```
Congratulations! You now have an array which can hold 5 items. Pretty cool, right? But what good is it if we don't know how to read and write values to it?

Let's put something into the first spot of the array. In programming in general, the "spots" in the array are called **indexes**. 
Another *VERY* important detail is that arrays in most programming languages start from 0. 
So in an array of size 5, the actual valid indexes are 0, 1, 2, 3, and 4. If you try to index 5, you'll get an error (most likely a segmentation fault)

### Inserting
Anyway, to put something into an array at a given index, this is the syntax:
```c++
  myArray[index] = myValue;
//  |       |         |
//  |       |         the value you want to put into the array. MUST be the same type as the array itself
//  |       |
//  |       the index you want to store it in. this MUST be an integer
//  |
//  the name of the array you created
```

For a real example, you can do this
```c++
int myArray[5];
myArray[0] = 25;
```

And now the value at the 0th position is `25`. 

### Reading
To read from an array, just index it but don't assign a new value. Piggybacking off the example from earlier
```c++
//note that in the previous code segment, we initialized the first value of the array to be 25.
int output = myArray[0];
cout << output << endl;
```

### Resizing
Imagine a scenario where you're using an array but then realize you're out of space, and you need to make it bigger.
Unfortunately for you, an array's size **CANNOT** be changed. However, you **can** create a new array that's bigger, and then copy the elements over.
I'll cover how to do this in the Dynamic Arrays section.

### Practice Assignment
Create a program which takes 3 inputs from the user, and outputs them in reverse order using an array.

(While this program can easily be done without an array, you should force yourself to use the array to help memorize the syntax.)

INPUT:
```
hello
orange
city
```
OUTPUT:
```
city
orange
hello
```

<details>
  
  <summary> Solution code </summary>
  
  ```c++
  #include <iostream>
  
  using namespace std;
  
  int main() {
    string inputs[3];
    cin >> inputs[0];
    cin >> inputs[1];
    cin >> inputs[2];
    cout << inputs[2];
    cout << inputs[1];
    cout << inputs[0];
    return 0;
  }
  ```
  
</details>


Arrays (dynamic)
----------------
One issue you might find with creating an array is that the compiler will not let you do something like this:
```c++
int userInput;
cin >> userInput;
int myArray[userInput];
```
This is because the size of `myArray` is not known at **compile time**. In layman's terms, when turning your C++ code into code that the computer can actually run,
it does not know how big your array will be. This means it cannot code the instruction in for memory allocation.
  
This is where dynamic arrays come in. Dynamic arrays are called so not because their size can be changed (it is still a fixed size),
but because the memory for them is allocated dynamically. These arrays, while the same in operation, need to be treated slightly differently.

### Creating
To create a dynamic array of size `size`, you use this syntax:
```c++
int size;
cin >> size;
//you do not need to use cin to get the size, this is simply for example.
int* myArray = new int[size];
```
Now you have an array of size `size` that you can use to store values in, exactly the same as you would with a static array.
However, you may notice that the type is different: it's `int*`. Why is that?

The `new` keyword allocates memory of a given size on the heap (a region of memory), and then returns a pointer to the first element of the array.
This pointer is what we use to access elements of the array. A pointer is *not* the value itself, rather, it points to where the value in memory can be found.
This will be covered in more detail in the pointers section.
  
### Indexing
Accessing the values of a dynamic array is exactly the same as a static array.
To write a value, you just do `array[index] = value;` and to read a value, just `array[index];`.
  
### Deleting
When you use dynamic arrays, you **MUST** delete them after you're done using them. Otherwise, the memory associated with them will not be freed until the program exits.
If your program is intended to run for long periods of time, this can cause a memory leak, which may eventually consume all of the memory on the system.

To delete an array, you use this syntax:
```c++
delete[] myArray;
myArray = nullptr;
```

To break down what's happening here:
  - On the first line, we're using the `delete[]` keyword to delete the array. You cannot just use `delete`, as that will not properly free the memory associated with the array.
  - On the second line, we're setting the pointer that was returned by `new` to `nullptr`, to ensure we don't accidentally try to use memory that is no longer allocated.
    (This will be covered in more detail in the pointers section.)
  
Always make sure to delete your arrays after you're done using them in your code, and also be sure not to pass deleted arrays into functions.
  
Vectors
-------
Vectors alleviate a lot of the grievances you may have with arrays: their size is not fixed, 
meaning you can add as many elements as you want and not have to worry about running out of space.
Vectors are a kind of **class** in C++, which means they have member functions that we can execute. This will be covered in more detail later.
For now, just know that vectors have functions associated with them that you can run to perform various operations.
  
**IMPORTANT:** When using vectors in your code, always make sure to `#include <vector>`.
  
### Creating
To create a vector, just define a variable for one. To create a vector that holds strings, you would do this:
```c++
vector<string> myVec;
```
  
Now we have a vector that we can use to store values in. Note that there is no need to define a size, as the size can be dynamically changed as you add or remove elements.

### Adding Values
There are many ways to add values into a vector, but we're going to focus on two right now: `.at(int)` and `.push_back(T)`. 

`.push_back(T)` adds a new value to the end of the vector, and increases the size of the vector by one.
For example:
```c++
vector<string> myVec;
//vector's size is currently 0
myVec.push_back("hello");
//vector's size is currently 1, and the 0th index is "hello". note that indexes greater than 0 do not exist at this point.
```
  
Speaking of size, to get a vector's size you run the `.size()` function. It returns the current size of the vector.
There is another function called `.capacity()`, but that function will return the capacity of the internal array of the vector, and is usually not what you want.
Be sure not to mix these up accidentally.
  
Once we have some values in a vector, we can change or access them using the `.at(int)` function. To access the 0th value of a vector, you do this:
```c++
string value = myVec.at(0);
```
The variable `value` now holds the value that was stored in the vector at position 0. 
  
If we wanted to *change* the value as position 0, we can do this:
```c++
myVec.at(0) = "qwerty";
```

### Removing Values
Similar to adding values, there's a function to remove the last value from the vector: `.pop_back()`.
This removes the last element and does NOT return it.
  
However, this only allows us to remove the value at the end of the vector. How can we remove one from somewhere in the middle?
For this we need to use `.erase(iterator)`. This function takes in an iterator that points at the value we want to remove.

This may sound scary, but it is actually quite simple to use. For example:
```c++
  vector<char> myVec;
  myVec.push_back('a');
  myVec.push_back('b');
  myVec.push_back('c');
  //we want to remove 'b', or the 1st element of the vector.
  myVec.erase(myVec.begin()+1);
  //and now 'b' is gone, the vector only contains 'a' and 'c'.
```
  
As a more general example:
```c++
vector<T> vec;
int index; //where index is the index of the value we want to remove. 
vec.remove(vec.begin()+index);
```
  
### Other functions
Vectors have a lot of other functions that are useful. You can find a complete list of them [here](https://www.cplusplus.com/reference/vector/vector/).
Below, I'll list a few of the most useful ones.
  
`bool empty()`
: Returns `true` is the vector's size is 0, `false` otherwise.
  
`reference at(int index)`
: Returns a reference to the value stored at index `index`.
 
`int size()`
: Returns the current size of the vector.
  
`void push_back(T value)`
: Stores the value `value` at the end of the vector, increasing the size by one.
  
`void pop_back(iterator iter)`
: Removes the value pointed at by the iterator `iter`.
  
`iterator begin()`
: Returns an iterator pointing at the first element.
  
`void clear()`
: Destroy all values in the vector.
