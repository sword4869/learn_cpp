# Declare a variable

**Only once declaration**.

You have the option to assign a value to the variable at the time you declare the variable or to declare it and assign a value later.

```cpp
int a=10;

int b;
b=11;
```

Any variable declared with the auto keyword should **be initialized at the time of its declaration** or there will be an error.

```cpp
auto c=13;

// error
// auto d;
```

# constant

A constant is an expression with a fixed value. It cannot be changed while the program is running.
Use the `const` keyword to define a constant variable.

```cpp
const int X = 42;
```

All constant variables **must be initialized** at the time of their creation.
