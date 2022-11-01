- [1. Normal](#1-normal)
- [2. Specialization](#2-specialization)

# 1. Normal

To create objects of the template class for different types, specify the data type in angle brackets, as we did when defining the function outside of the class.

```cpp
#include <iostream>
using namespace std;

template <class T>
class MyClass {
public:
    T first;
    MyClass(T x):first(x){}
    void print1();
    void print2(T y);
};

template <class T>
void MyClass<T>::print1(){
    cout << first << endl;
}

template <class T>
void MyClass<T>::print2(T y){
    cout << y << endl;
}

int main() {
    MyClass<int> m(10);
    m.print1();
    // m.print2("str"); 只能写同样的T
    m.print2(100);
    MyClass<string> n("hello");
    n.print1();
}
```
模板类中的函数的语法，就是函数模板的语法多了个`MyClass<T>::`.

# 2. Specialization

Template specialization allows for the definition of a different implementation of a template when a specific type is passed as a template argument.

First of all, notice that we precede the class name with `template<>`, including an empty parameter list. This is because all types are known and no template arguments are required for this specialization. More important than this prefix, is the `<string>` specialization parameter after the class template name and the inner part of the class also uses a specific `string` type.

Keep in mind that there is no member "inheritance" from the generic template to the specialization, so all members of the template class specializations must be defined on their own.

```cpp
#include <iostream>
using namespace std;

template <class T>
class MyClass {
public:
    T first;
    MyClass(T x):first(x){
        cout << x << " is not string" << endl;
    }
};

template <>
class MyClass<string> {
public:
    string first;
    MyClass(string x):first(x){
        cout << x << " is string" << endl;
    }
};

int main() {
    MyClass<int> m(10);
    MyClass<double> n(3.14);
    MyClass<string> p("hello");
}
```
# 代码分离
如果需要代码分离，即 template class 的声明、定义，以及 main 函数分属不同文件。例如：
```
src_dir
|____MyStack.h
|____MyStack.cpp
|____main.cpp
```
则 main.cpp 文件中需要同时包含 .h 文件和 .cpp 文件，不然会出现链接错误。
```cpp
// main.cpp
#include "MyStack.h"
#include "MyStack.cpp"

// 其他include
// main函数主体 
```
