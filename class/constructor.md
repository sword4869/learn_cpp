系统会自动生成一个默认的**无参的构造函数**，如果你声明了**有参构的造函数**，那么无参构造就会不主动创建。


当类为空时，编译器会为这个类合成默认的构造函数、析构函数、拷贝构造函数、赋值重载函数。
编译器合成的默认函数都是**public**的，不是private。因为如果类中构造函数是私有的，就不能在类的外部创建对象。
```cpp
class Demo
{

};
void func()
{
    Demo d1,d2,d5;//默认构造函数
    Demo d3(d1);//默认拷贝构造函数
    Demo d4 = d2;//默认拷贝构造函数
    d5 = d4;//默认赋值重载

    //局部对象自动销毁，调用默认析构函数
}
int main()
{
    func();
    return 0;
}
```
# 触发

```cpp
class A
{
public:
    A()
    {
        cout << "A";
    }
};
```

```cpp
A a;        // A
A a2[2];    // A A
A *a3;      // 无
```
# 构造函数与继承

派生类的构造函数会隐含调用基类的构造函数.

如果基类中没有缺省构造函数，那么派生类必须定义构造函数.

在建立派生类对象时，先调用基类的构造函数，再调用派生类的构造函数

在销毁派生类对象时，先调用子类的析构函数，再调用基类的析构函数
```cpp
class A
{
public:
    A()
    {
        cout << "A::A" << endl;
    }
    ~A()
    {
        cout << "A::~A" << endl;
    }
};
class B : public A
{
public:
    B()
    {
        cout << "B::B" << endl;
    }
    ~B()
    {
        cout << "B::~B" << endl;
    }
};
```

```cpp
B b; 
/**
A::A
B::B
B::~B
A::~A
*/
```
```cpp
A* p = NULL;    // 没有
p = new B;      // A::A, B::B
delete p;       // A::~A
```
指针声明没有, 赋值才有；没有B的析构.

因为B的构造会先去调用A的构造, 然后B的对象被转化为A的类型(`A*`), 这就是为什么最后析构的是A对象.


# member initializer list

- 初始化私有变量必须用这种格式
```cpp
class MyClass {
public:
    MyClass(int a, int b): regVar(a), constVar(b){}

private:
    int regVar;
    const int constVar;
};
```
- 继承
```cpp
// 仅有继承的变量
Derived（int x,int y）:Base（x,y）{}

// 继承的变量+子类独有的
Derived（int x,int y,int z,int m）:Base（x,y）{c=z; d=m;}
```