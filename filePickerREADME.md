## Example usage:
```c++
#include <QDebug>
#include "nativejava/FilePicker.h"

NativeJava::FilePicker::onFilePicked([](const QString& filePath) {
    qDebug() << "File selected:" << filePath;
    // Process it here
});

NativeJava::FilePicker::open("image/*");

```
