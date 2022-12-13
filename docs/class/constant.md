- [const functino in general class](#const-functino-in-general-class)
- [1. const object](#1-const-object)
  - [1.1. constructor](#11-constructor)
  - [1.2. member initializer list](#12-member-initializer-list)
  - [1.3. forbid changes](#13-forbid-changes)
  - [1.4. const object call const function](#14-const-object-call-const-function)



# const functino in general class

```cpp
class Aclass{
    bool operator<(const Aclass &b) const;
    void operator=(const Aclass &b);
};
```
什么时候是`const`函数，什么不是呢？

不需要修改时，就设计为const函数，比如小于运算符重载；需要修改时就不，比如赋值运算符重载。
# 1. const object
```cpp
const MyClass obj;
```

## 1.1. constructor

When you've declare **a const object**, you can't change its data members during the object's lifetime. But all const member variables must be initialized.

So the const object(include member varialbes)'s initialization is done via **a parameterized and public constructor**. If no public default constructor is provided, a compiler error will occur.

## 1.2. member initializer list

C++ provides a handy syntax for initializing members of the class called the member initializer list (also called a constructor initializer).

Why need this special syntax? Because the normal constructor is wrong.

```cpp
class MyClass {
public:
    MyClass(int a, int b) {
        regVar = a;
        constVar = b;
    }
private:
    int regVar;
    const int constVar;
};
//error
```

The initialization list eliminates the need to place explicit assignments in the constructor body.

```cpp
class MyClass {
public:
    MyClass(int a, int b): regVar(a), constVar(b){}
private:
    int regVar;
    const int constVar;
};
```

In the declaration of constructor, it is as same as normal class.

```cpp
class MyClass {
public:
    MyClass(int a, int b);
private:
    int regVar;
    const int constVar;
};
MyClass::MyClass(int a, int b): regVar(a), constVar(b){
    cout << regVar << end;
    cout << constVar << end;
}
```

PS: Even in cases in which member variables are not constant, it makes good sense to use the member initializer syntax.

## 1.3. forbid changes

Once **a const class** object has been initialized via the constructor, you cannot modify the object's member variables. **This includes both directly making changes to public member variables and calling member functions that set the value of member variables.**

## 1.4. const object call const function

A constant object can't call regular functions.
Hence, for a constant object to work you need a constant function.

For const member functions that are defined outside of the class definition, the const keyword must be used on both the function prototype and definition.

MyClass.h

```cpp
class MyClass{ 
public: 
    void myPrint() const; 
};
```

MyClass.cpp

```cpp
#include "MyClass.h" 
#include  <iostream>
using namespace std;
void MyClas:myPrint() const {
    cout <<"Hello" <<endl;
}
```

main.h

```cpp
#include "MyClass.h" 
#include  <iostream>
using namespace std;
int main(){
    const MyClass obj;
    obj.myPrint();
    return 0;
}
```
