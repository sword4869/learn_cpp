- [1. two types of polymorphism](#1-two-types-of-polymorphism)
  - [1.1. 相同的函数功能](#11-相同的函数功能)
  - [1.2. 不同的函数功能](#12-不同的函数功能)

Polymorphism occurs when there is a hierarchy of classes and they are related by inheritance.

```cpp
Base B;
Derived D;

// 方式1:指针
Base *p1 = &D;
p1->function();

// 方式2:引用
Base &p2 = D;
p2.function();
```
`Base p3 = D;`这个不是. 此乃类型转化, D的对象被转化为Base类的对象, 之后`p3`都看作Base类的对象.
# 1. two types of polymorphism

C++ polymorphism means **one function with different implementions**. Concrete polymorphism is a controversial topic, so there are 2 types of function implementions.

What they have in common is to call a derived class's member functions via a base class pointer.

- base class pointer: ` Enemy *e1 = &n;` 
  
  The pointer is the base class pointer type and points to the object of the derived class.

- 如果只有一种多态的话，那么认为是后者:
  - 相同的函数功能：调用父类的函数。
    
  - 不同的函数功能：调用子类不同的函数.
    
## 1.1. 相同的函数功能

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
很明显, 父类定义函数而子类没重新定义, 自然这个例子中调用的都是父类的函数.

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
父类和子类都队函数作了定义.

可以看到虽然`a`,`b`的值变换了，但是`show()`都是`Base.show()`，调用都是父类的函数。

## 1.2. 不同的函数功能

It is used when the different derived classes need different behaviors of the same function.

keyword `virtual`, and the function is called **virtual function**.

```cpp
#include <iostream>
using namespace std;

class Enemy {
public:
    virtual void attack(){}
};

class Ninja: public Enemy {
public:
    virtual void attack() {
        cout << "Ninja!" << endl;
    }
};

class Monster: public Enemy {
public:
    void attack() {
        cout << "Monster!" << endl;
    }
};

int main() {
    Ninja n;
    Monster m;
    Enemy *e1 = &n;
    Enemy *e2 = &m;
    e1->attack();   // Ninja!
    e2->attack();   // Monster!
}
```
父类定义`virtual`虚函数, 子类可以定义`virtual`也可以普通函数. 一般, 子类的函数再`virtual`都是出现在子类又被子子类继承的情况.