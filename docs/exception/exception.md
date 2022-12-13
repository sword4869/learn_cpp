C++ exception handling is built upon three keywords: `try`, `catch`, and `throw`.

# throw

Any data type.

```cpp
if(true) throw "404";

throw 404;
```

# try-catch

> concrete data type


```cpp
try{
    throw 404;
}catch(int x){
    cout << x << endl;
}
```

> every data type

`...` is indeed the special syntax, not the pseudo code.
```cpp
try{
    throw 404;
}catch(...){
    cout << x << endl;
}
```
