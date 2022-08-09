We can also use a pointer to access the object's members.
The following pointer points to the obj object:

```cpp
MyClass obj;
MyClass *ptr = &obj;
```

# access memeber

The arrow member selection operator (->) is used to access an object's members with a pointer.

```cpp
ptr->myPrint();
```

When working with an object, use the dot member selection operator (`.`).
When working with a pointer to the object, use the arrow member selection
operator (`->`).

# this

**Inside a member function**, `this` may be used to refer to the invoking obj.

Friend functions do not have a `this` pointer, because friends are not members of a class.

e.g.The `printInfo()` method offers three alternatives for printing the member variable of the class.

```cpp
class MyClass {
public: 
    MyClass(int a): var(a){}
    void printInfo() { 
        cout << var << end;
        cout << this->var << end;
        cout << (*this).var << end;
    }
private:
    int var;
};
```

The `this` keyword has an important role in operator overloading.
