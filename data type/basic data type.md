# Booleans: bool

The keyword of boolean is `bool`, not itself.

If a Boolean value is assigned to an integer, true becomes 1 and false becomes 0.

```cpp
int a = true;   // 1
int b = false;  // 0
```

If an integer value is assigned to a Boolean, 0 becomes false and any value that has a **non-zero** value becomes true.

```cpp
bool c = -1;    // true
bool d = 0;     // false
```

# modifier

## integer

Several of the basic types, including integers, can be modified using one or more of these
type modifiers:

- `signed`: A signed integer can hold both negative and positive numbers.
- `unsigned`: An unsigned integer can hold only positive values.
- `short`: Half of the default size.
- `long`: Twice the default size.

```cpp
signed long int a;

// is equivalent to
long a;
```

## floating

Floating point data types are always `signed`, which means that they have the capability to hold both positive and negative values.
