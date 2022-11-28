- [1. two types of polymorphism](#1-two-types-of-polymorphism)
  - [1.1. identical behaviors](#11-identical-behaviors)
  - [1.2. different behaviors](#12-different-behaviors)
- [2. 2 type of virtual function](#2-2-type-of-virtual-function)
  - [2.1. have body](#21-have-body)
  - [2.2. no body](#22-no-body)

Polymorphism occurs when there is a hierarchy of classes and they are related by inheritance.

# 1. two types of polymorphism

C++ polymorphism means **one function with different implementions**. Concrete polymorphism is a controversial topic, so there are 2 types of function implementions.

What they have in common is to call a derived class's member functions via a base class pointer.

- base class pointer: 
  ` Enemy *e1 = &n;` The pointer is the base class pointer type and points to the object of the derived class.
- call a derived class's member functions:
  - In the way of identical behavior, `e1->setAttackPower(20)`, the function is inherited from base class.
  - In the way of different behavior, ``, the function's concrete implement is in derived class.

## 1.1. identical behaviors

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

## 1.2. different behaviors

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

## 2.1. have body

The function in the base class have the body content. So the base class can create a object.

PS: `virtual void attack(){}` belongs to this type.

- `e1` which points to the derived class object with function implemention calls the function in derived function.
- `e2` which points to the derived class object without function implemention calls the function in base function.
- `e3` which points to the base class object calls the function in base function.

```cpp
#include <iostream>
using namespace std;

class Enemy {
protected: 
    int attackPower = 0;
public:
    virtual void attack(){
        cout << "Enemy! - "<<attackPower<<endl;
    }
};

class Ninja: public Enemy {
public:
    void attack() {
        cout << "Ninja! - "<<attackPower<<endl;
    }
};

class Monster: public Enemy {};

int main() {
    Ninja n;
    Monster m;
    Enemy q;
    Enemy *e1 = &n;
    Enemy *e2 = &m;
    Enemy *e3 = &q;
    e1->attack();
    e2->attack();
    e3->attack();
}
```

## 2.2. no body

This function is called **pure virtual function** and has the special syntax `virtual void attack() = 0;` (this statement is a declaration which ends with semicolon).

The base class with pure virtual function is called **abstract class**.

Every derived class inheriting from a class with a pure virtual function **must override** that function. (or compiler error)

You cannot create objects of the base class with a pure virtual function. (or compiler error)

```cpp
virtual void attack()=0;

Enemy q;	// error
```
