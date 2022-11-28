# definition

一个类的友元函数能够访问类的**所有成员**(包括私有)。一个类的友元函数对类成员的访问能力等同于类的成员函数 ，即能访问类的所有成员。 

But the friend function is **not** a member function.

The function is defined as a regular function **outside class**.

It takes an object of type the class as its parameter and is able to access the private data members of that object.

```cpp
class MyClass {
public:
    MyClass() {
        regVar = 0;
    }
private:
    int regVar;
    friend void someFunc(MyClass &obj);
};

void someFunc(MyClass &obj) {
    obj.regVar = 42; 
    cout << obj.regVar;
}
```

friend functions don't have a pointer `this`.
