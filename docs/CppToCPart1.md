layout: page
title: "C++ To C Part 1"
permalink: /cpp2cp1

# C++ to C <p style="font-size: 14px;">Part 1</p>

> [!WARNING]
> This is a work in progress page!

Welcome to my C++ to C guide. This is part 1 of the series. You do not need to know C++ to use this guide. It is helpful that you already have at least a basic understanding of C and the standard library.

## C++ std::vector
In C++ a common array type is a vector. A vector is a resizable array that **uses the heap**. In C++, you create a vector as: <br/>
```C++
std::vector<type> MyVector;
```
and if you want to define an initial amount of items: <br/>
```C++
std::vector<type> MyVector(length);
```
A vector is a resizable array and a common way to resize it is by pushing an object onto it and popping an object out of it. This is done by 2 functions: <br/>
```C++
MyVector.push_back(Item_To_Insert);
```
and to take something out: <br/>
```C++
MyVector.pop_back(); 
```
How I tend to write this in C is using a heap allocated array. This can be done with: <br/>
```C
type* MyArray = (type*)malloc(sizeof(type) * length);
```
In C++, a vector automatically gets freed. In C, you must free the array yourself. This can be done with: <br/>
```C
free(MyArray);
```
When using a heap allocated array, I usually have a variable (like an int) to keep track of how many items are currently in the array. This is not needed but can be helpful. In C to add something onto a heap allocated array you can do: <br/>
```C
MyArray = realloc(MyArray, ((length + 1) * sizeof(type)));
MyArray[length++] = item;
```
and if you want it more compact:
```C
MyArray = realloc(MyArray, sizeof(type) * (length + 1)), MyArray[length++] = item;
// Note: If realloc fails, it returns NULL, the original memory is not freed, and a memory leak will happen.
```
To preform a `pop_back` in C, you can preform the same operation for adding an item but subtract the length. This can be preformed with:
```C
MyArray = realloc(MyArray, ((length - 1) * sizeof(type)));
```

> [!NOTE]
> More content coming soon.