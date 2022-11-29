- [1. two types of polymorphism](#1-two-types-of-polymorphism)
  - [1.1. 相同的函数功能](#11-相同的函数功能)
  - [1.2. 不同的函数功能](#12-不同的函数功能)
- [2. 2 type of virtual function](#2-2-type-of-virtual-function)

Polymorphism occurs when there is a hierarchy of classes and they are related by inheritance.

# 1. two types of polymorphism

C++ polymorphism means **one function with different implementions**. Concrete polymorphism is a controversial topic, so there are 2 types of function implementions.

What they have in common is to call a derived class's member functions via a base class pointer.

- base class pointer: ` Enemy *e1 = &n;` 
  
  The pointer is the base class pointer type and points to the object of the derived class.

- 如果只有一种多态的话，那么认为是后者:
  - 相同的函数功能：调用父类的函数。
    
  - 不同的函数功能：调用子类不同的函数：
    
## 1.1. 相同的函数功能

It is used when we design the different derived classes have identical behavior implemention.

We write the function in base class.

```cpp
#include <iostream>
using namespace std;

class Enemy {
protected: 
    int attackPower;
public:
    void setAttackPower(int a){
        attackPower = a;
    }
};

class Ninja: public Enemy {};

class Monster: public Enemy {};

int main() {
    Ninja n;
    Monster m;
    Enemy *e1 = &n;
    Enemy *e2 = &m;
    e1->setAttackPower(20);
    e2->setAttackPower(80);
}

```

```cpp
class Base
{
public:
    int a, b;

    Base(int x, int y) : a(x), b(y) {}

    void show() { cout << "Base.show " << a << ',' << b << endl; }
};
class Derived : public Base
{
public:
    Derived(int x, int y) : Base(x, y) {}
    void show() { cout << "Derived.show " << a << ',' << b << endl; }
};
int main()
{
    Base B1(50, 50);
    Derived D1(10, 20);
    Base *pb = &B1;
    pb->show(); // Base.show 50,50
    Base *pd = &D1;
    pd->show(); // Base.show 10,20
    return 0;
}
```
可以看到虽然`a`,`b`的值变换了，但是`show()`都是`Base.show()`，调用都是父类的函数。

## 1.2. 不同的函数功能

It is used when the different derived classes need different behaviors of the same function.

keyword `virtual`, and the function is called **virtual function**.

```cpp
#include <iostream>
using namespace std;

class Enemy {
protected: 
    int attackPower = 0;
public:
    virtual void attack(){}
};

class Ninja: public Enemy {
public:
    void attack() {
        cout << "Ninja! - "<<attackPower<<endl;
    }
};

class Monster: public Enemy {
public:
    void attack() {
        cout << "Monster! - "<<attackPower<<endl;
    }
};

int main() {
    Ninja n;
    Monster m;
    Enemy *e1 = &n;
    Enemy *e2 = &m;
    e1->attack();
    e2->attack();
}
```

# 2. 2 type of virtual function

The virtual function is in the idea that the polymorphism is about different behaviors.

Defining a virtual function in the base class, with a corresponding version in a derived class, allows polymorphism to use base class pointers to call the derived classes' functions. Every derived class will override the `attack()` function and have a separate implementation.