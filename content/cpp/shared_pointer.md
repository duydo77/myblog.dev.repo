https://www.geeksforgeeks.org/smart-pointers-cpp/

Pointers are used for accessing the resources which are external to the program - kike heap memory. So, for accessing the heap memory, pointers are used. If we just use the copy of the resources, we just change the copy version when making change to it. But, f we use a pointer to the resource, we'll be able to change the original resource.

## 1. Problems with Normal pointer
if we create a pointer in a function, this pointer will be delete after this function is complete but the memory is point to is not. So it will make memory leak that we dont want.

``` Cpp
#include <iostream>
using namespace std;
 
class Rectangle {
private:
    int length;
    int breadth;
};
 
void fun()
{
    // By taking a pointer p and
    // dynamically creating object
    // of class rectangle
    Rectangle* p = new Rectangle();
}
 
int main()
{
    // Infinite Loop
    while (1) {
        fun();
    }
}
```

## 2. Smart pointer
smart pointer is a class that will manage the pointer and deallocate the memory when the pointer is deleted. Java, C# has a Garbage Collection Mechanisms to smartly deallocate unused memory. When the object is destroyed it frees the memory as well. So, we dont need to worry about any memory leak.  

## 3. Types of smart pointer
