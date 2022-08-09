The `<string>` library is included in the `<iostream>` library, so you don't need to include `<string>` separately, if you already use `<iostream>`

Alternatively, you can use the `<string>` library if you don't use `<iostream>`.

PS: `<iostream>` and `<string>` library both need to be in namespace std.

```cpp
#include <iostream>
using namespace std;

int main(){
    string a ="ff";
    return 0;
}
```

```cpp
#include<string>
using namespace std;

int main(){
    string a ="ff";
    return 0;
}
```
