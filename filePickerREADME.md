## Example usage:
```c++
#include "FilePicker.h"

NativeJava::FilePicker::onFilePicked([](const QString& filePath) {
    qDebug() << "File selected:" << filePath;
    // Process it here
});

NativeJava::FilePicker::open("image/*");

```
