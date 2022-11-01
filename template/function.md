# one template type

`sum1()` is the normal function which is limited in integer numbers.

`sum2()` is template function which is automatically matched with different type numbers.

```cpp
#include <iostream>
using namespace std;

int sum1(int a, int b){
    return a+b;
}

template <typename T>
T sum2(T a, T b){
    return a+b;
}

int main() {
    cout << sum1(1,2) << endl;
    cout << sum2(1,2) << endl;
    cout << sum2(1.1, 2.2) << endl;
}
```

# multiple template type

```cpp
#include <iostream>
using namespace std;

template <typename T, typename U>
T smaller(T a, U b){
    return a>b?a:b;
}

int main() {
    // (double, int) -> double
    cout << smaller(1.2, 0) << endl;
    // (int, double) -> int
    cout << smaller(3, 4.4) << endl;
}
```

`typename`和`class`在模板类和模板函数中都可以混用，不过习惯上模板函数`typename`，模板类`class`
