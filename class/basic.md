- [1. constructor and destructor](#1-constructor-and-destructor)
  - [1.1. constructor](#11-constructor)
  - [1.2. destructor](#12-destructor)
- [2. encapsulation](#2-encapsulation)
- [3. header, source and main](#3-header-source-and-main)
  - [3.1. Scope Resolution Operator](#31-scope-resolution-operator)
  - [3.2. directive](#32-directive)
- [hh](#hh)


# 1. constructor and destructor

## 1.1. constructor

The constructor's name is identical to that of the class. It has no return type, not even void.

```cpp
class MyClass{
public:
    MyClass(argument list);
};

MyClass::MyClass(argument list){
    cout<<"Constructor"<<endl;
}
```

## 1.2. destructor

The destructor's name is identical to that of the class, only prefixed with a tilde (~). A destructor don't return a value or take any parameters.

```cpp
class MyClass{
public:
    ~MyClass();
};

MyClass::~MyClass(){
    cout<<"Destructor"<<endl;
}
```

Since destructor can't take parameters, destructor also can't be overloaded. Each class will have just one destructor.

Defining a destructor is not mandatory. If you don't need one, you don't have to define one.

# 2. encapsulation

We used encapsulation to hide the name attribute from the outside code. Then we provided access to it using public methods. Our class data can be read and modified only through those methods.

This allows for changes to the implementation of the methods and attributes, without affecting the outside code.

```cpp
#include <iostream>
#include <string>
using namespace std;
class myClass {
public:
    string name;
};
int main() {
    myClass myObj;
    my0bj.name = "John";
    cout << myObj.name;
    return 0; 
}
```

```cpp
#include <iostream>
#include <string>
using namespace std;

class myClass {
public:
    void setName(string x) {
        name = x;
    }
    string getName() {
        return name;
    }
private:
    string name;
};
int main() {
    myClass myObj;
    myObj.setName("John");
    cout << my0bj.getName();
    return 0;
}
```

# 3. header, source and main

The header file (**MyClass.h**) holds the function declarations (prototypes) and variable declarations.

```CPP
#ifndef MYCLASS H
#define MYCLASS H
class MyClass{
public:
    MyClass();
};
#endif I1 MYCLASS H
```

The source file (**MyClass.cpp**) holds the implementation of the class and its methods.

```cpp
#include "MyClass.h"
MyClass::MyClass(){
    cout << "constructor\n";
}
```

To use our classes in our main(**main.cpp**), we need to include the **header file**. For example, to use our newly created MyClass in main:

```cpp
#include <iostream>
#include "MyClass.h"
using namespace std;
int main() {
    MyClass obj;
}
```

## 3.1. Scope Resolution Operator

The double colon(`::`) in the source file (.cpp) is called the scope resolution operator, and it's used for the constructor definition.

## 3.2. directive

- `ifndef` stands for "if not defined". The first pair of statements tells the program to define the MyClass header file if it has not been defined already.
- `endif` ends the condition.

This prevents a header file from being included more than once within one file.


# hh

成员函数分为静态成员函数和非静态成员函数. ""