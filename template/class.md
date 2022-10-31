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
    void printInfo();
};

template <class T>
void MyClass<T>::printInfo(){
    cout << first << endl;
}

int main() {
    MyClass<int> m(10);
    m.printInfo();
    MyClass<string> n("hello");
    n.printInfo();
}
```

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
