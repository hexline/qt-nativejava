## Example usage:
```c++
// No permission required for File Picker to read files
#include <QDebug>
#include <QFile>
#include <nativejava/filePicker.h>

void pickFileAndRead() {
    NativeJava::FilePicker::onFilePicked([](const QString& path) {
        qDebug() << "File picked:" << path;

        QFile file(path);
        if (file.open(QIODevice::ReadOnly)) {
            QByteArray data = file.readAll();
            qDebug() << "File content:" << data.left(100); // Preview first 100 bytes
            file.close();
        } else {
            qWarning() << "Failed to open file:" << path;
        }
    });

    // Launch file picker for any file
    NativeJava::FilePicker::open("*/*");
}
```
