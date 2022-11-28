- [Operators](#operators)
- [Rule](#rule)
# Operators

This chart shows the operators that can be overloaded.

![1659958431415](../image/1659958431415.png)

4 operators cannot be overloaded:

- `::`(scope resolution),
- `.`(member access),
- `.*`(member access through pointer to member),
- `?:`(ternary conditional)

# Rule

Overloaded operators are **functions**, defined by the keyword `operator` followed by the symbol for the operator being defined `operator<symbol>`.

e.g. We need our `+` operator to return a new MyClass object with a member variable equal to the sum of the two objects' member variables.

```cpp
class MyClass {
public:
    int var;
    MyClass();
    MyClass(int a): var(a) {}
    MyClass operator+(MyClass &obj) {
        MyClass res;
        res.var= this->var + obj.var;
        return res;
    }
};
int main() {
    MyClass obj1(12), obj2(55);
    MyClass res = obj1 + obj2;
    cout << res.var;
    return 0;
}
```
