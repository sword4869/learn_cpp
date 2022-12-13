# Definition

A pointer is **a variable**, with the **address** of another variable as its value. It is a data type that contains an address.

# Allocate

You can allocate memory at run time within the heap for the variable of a given type using the `new` operator, which **returns the address of the space allocated**.

```cpp
int *p = new int;

int *q = NULL;
q = new int;
```

# Dangling pointers

```cpp
delete p;
```

The `delete` operator frees up the memory allocated for the variable, but does not delete the pointer itself, as the pointer is stored on the stack.
Pointers that are left pointing to non-existent memory locations are called **dangling pointers**.

The solution is to assign NULL to the pointer, which make it to become a **null pointer**.

```cpp
p = NULL;
```

# Pointer to array

```cpp
int *p = new int[20];
p[0] = 10;
delete []p;
```

# sizeof

The argument can be data type of variable or variable.

```cpp
int a = 10;
cout << sizeof(int) << " " << sizeof(a);
```
