## Usage of toasts, etc.

```c++
#include <nativejava/popup.h>

void notifyUser() {
    NativeJava::Popup::showToast("This is a native toast!");
    NativeJava::Popup::showToast("Long one...", NativeJava::Popup::Duration::Long);
}
```
