```cpp
const MyClass obj;
```

# constructor

When you've used const to declare an object, you can't change its data members during the object's lifetime. But all const member variables must be initialized.

So the const object(include member varialbes)'s initialization is done via **a parameterized and public constructor**. If no public default constructor is provided, a compiler error will occur.

## member initializer list

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
MyClass:MyClass(int a, int b): regVar(a), constVar(b){
    cout << regVar << end;
    cout << constVar << end;
}
```

PS: Even in cases in which member variables are not constant, it makes good sense to use the member initializer syntax.

# forbid changes

Once a const class object has been initialized via the constructor, you cannot modify the object's member variables. **This includes both directly making changes to public member variables and calling member functions that set the value of member variables.**

# const object call const function

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
