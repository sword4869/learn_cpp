# definition

Friend function of a class can access its **all members(include private memebers)**. But the friend function is **not** a member function.

The function is defined as a regular function **outsid e class**.

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

PS: friend functions don't have a pointer `this`.
