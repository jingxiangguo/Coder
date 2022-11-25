---
title: 'map'
date: 2022-11-22
permalink: /learning/map/
toc: true
---
## Background 
---


After working with C++ in large software projects and reading numerous threads on the Stack Overflow, I realize how distant I am from completely mastering C++. As a novice, I often googled my guesses first, and then rushed to apply what I just learnt to get the work done without thinking about potentially costy trade-offs under the hood. As my experience grew, I no longer fantasied about a quick and dirty solution that solves once for all. Instead, I learn to assess the merit of a solution based on how well the overall design objectives are served. Such assessment will be deeply rooted in the understandings of C++ foundamentals, which, to me, are not trivial tasks to accomplish.    

The purpose of writing this note is not to introduce all the nuts and bolts of C++ again as there are so many books out there that have done much better job. Rather, I want to write something practical, providing valuable and relevant information to a developer so that he/she can make the judious choice in the development. I wish this note to be of immediate help for those who just embark on their journeys of using c++.    

[vector](vector/vector.md)
[vector]({{ site.baseurl }}/vector/vector.md)

## ```std::vector```
* It is a sequential container
* The container itself can be allocated on the ```stack``` as a local variable in a function, but it owns and manages memories on the ```heap```. Also, the container can be dynamically allocated on the ```heap``` with its managed memory also on the ```heap```. The code snippet below shows two different memory locations.  


```c++
#include <iostream>
#include <vector>

void func()
{ 
    std::vector<int> viVal;
    std::vector<int>* pviVal; 
    viVal.push_back(1);
    // &viVal -> the memory address on the stack
    std::cout << &viVal << std::endl; 
    // viVal.data() -> the memory address on the heap
    std::cout << viVal.data() << std::endl;
   // The 'viVal' and its resources on the heap will be automatically free after exiting func. 
    pviVal = new std::vector<int>; 
    // pviVal.data() -> the memory address on the heap
    std::cout << pviVal << std::endl;
    pviVal->push_back(1); 
    // viVal.data() -> the memory address on the heap
    std::cout << pviVal->data() << std::endl;
}

int main()
{ 
   func(); 
   return 0;  
}

```



#### ```size()```

#### ```push_back()```
#### ```capacity()```
#### ```shrink_to_fit()```
#### ```resize()```
#### ```data()```
#### ```empty()```
#### ```clear()```
#### ```emplace()```
#### ```emplace_back()```





## Applications 

#### Case1: Iterate two ```std::vector``` simulatenously


## References:


## ```std::stack``` 
it is a container adapator

## ```std::map```

## ```std::set```

When $a \ne 0$, there are two solutions to $(ax^2 + bx + c = 0)$ and they are 
$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$



# C++ Basics

# C++ Move 

