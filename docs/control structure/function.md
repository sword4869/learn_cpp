# Default value

This is the difference between CPP and C.

When defining a function, you can specify a default value for **each of the last parameters**.

```cpp
int sum(int a, int b=10){
    return a + b;
}
```

# Overloading

This is the difference between CPP and C.

Function overloading allows to create multiple functions with **the same function name**, so long as they have different **argument list** (the types and/or the number of arguments).

```cpp
int sum(int a, int b=10){
    return a + b;
}
float sum(float a, float b=10){
    return a + b;
}

```

You can not overload function declarations that differ only by return type. The following declaration results in an error.

```cpp
int printName(int a) {}
float printName(int b) {}
```
