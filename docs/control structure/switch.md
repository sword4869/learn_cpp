# switch

The switch statement doesn't have to contain a default case.

```cpp
switch(x){
case 1:
case 2:
}
```

When the first case is default case without break statement, it can still have fall-through problem.

```cpp
switch(x){
default: 
cout << "default" << endl;
break;
case 1:
cout << "1" << endl;
break;
}
```
