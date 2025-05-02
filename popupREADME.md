## Usage of toasts, etc.

```c++
#include <nativejava/popup.h>

void popupSomething() {
    NativeJava::Popup::showToast("Hello from Qt!");
    NativeJava::Popup::showSnackbar("Here's a Snackbar!", NativeJava::Popup::Duration::Long);
    NativeJava::Popup::showAlertDialog("Greetings", "This is an AlertDialog.");
}

```
