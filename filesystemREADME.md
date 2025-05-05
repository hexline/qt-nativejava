## Usage of the filesystem header

```c++
// Write or create a file
// NativeJava::filesystem::write("filepath", onSuccessFunc(), onErrorFunc());
NativeJava::filesystem::write(
    "/sdcard/MyApp/data.txt",
    "Hello from Qt!",
    [](const QString& result) {
        qDebug() << "Write Success:" << result;
    },
    [](const QString& error) {
        qDebug() << "Write Error:" << error;
    }
);

// Check if a file exists
NativeJava::filesystem::exists("/sdcard/test.txt", [](const QString& msg, bool error) {
    if (!error)
        qDebug() << "Exists:" << msg;
    else
        qDebug() << "Missing:" << msg;
});


// Read a file
NativeJava::filesystem::read(
    "/sdcard/MyApp/data.txt",
    [](const QString& content) {
        qDebug() << "File Content:" << content;
    },
    [](const QString& error) {
        qDebug() << "Read Error:" << error;
    }
);

// Delete a file or folder
NativeJava::filesystem::deletePath(
    "/sdcard/MyApp/data.txt",
    [](const QString& result) {
        qDebug() << "Delete Success:" << result;
    },
    [](const QString& error) {
        qDebug() << "Delete Error:" << error;
    }
);

// Create a folder
NativeJava::filesystem::createFolder(
    "/sdcard/MyApp/newfolder",
    [](const QString& result) {
        qDebug() << "Folder Created:" << result;
    },
    [](const QString& error) {
        qDebug() << "Folder Creation Failed:" << error;
    }
);



```
