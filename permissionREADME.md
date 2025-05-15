## How to request and check runtime permissions

```c++
#include <nativejava/permission.h>

PermissionManager pm;
// Request permisison
pm.requestPermission("android.permission.READ_SMS");

// Check permisison
bool granted = pm.checkPermission("android.permisison.READ_SMS);
```
