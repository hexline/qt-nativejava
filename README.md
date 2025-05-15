# qt-nativejava
#### A high-level wrapper for use in Qt/C++ that can interact with Native Android. This library includes reliable headers that would save time. 

## How to install
Clone or download this repo into your project root folder
```bash
git clone https://github.com/hexline/qt-nativejava
mv qt-nativejava nativejava # Rename the folder
# Move android/ folder to the root folder
mv nativejava/android android
```
The folder would look like:
```
my_project
--  nativejava/
--  android/
--  main.cpp
--  Main.qml
--  CMakeLists.txt
```
Then open your CMakeLists.txt and add this after <b>qt_add_executable()</b>, for example:
```cmake
qt_add_executable(appMyApplication
    main.cpp
)
add_subdirectory(nativejava/)
set_property(TARGET appMyApplication APPEND PROPERTY QT_ANDROID_PACKAGE_SOURCE_DIR ${CMAKE_SOURCE_DIR}/android)
```
The last thing to do id to open <b>nativejava/CMakeLists.txt</b> and change your target source to match the target of the previous CMakeLists.txt, for example

```cmake
target_sources(appMyApplication
    PRIVATE
        background.h bluetooth.h camera. filePicker.h interface.h hardware.h hotspot.h launchActivity.h permission.h popup.h microphone.h notification.h specialPermission.h wifi.h
)
```
#### Installation is done! 

Example of how to use:
```c++
// MyHandler.h
#include <QObject>
#include <nativejava/filePicker.h>

class MyHandler: public QObject{
    Q_OBJECT
public:
    Q_INVOKABLE void pickFile(QString permString){
        NativeJava::filePicker::onFilePicked([](const QString &path) {
            qDebug() << "[FilePicker] File picked:" << path;
            //QCoreApplication::quit();  // Exit after picking
        });
        NativeJava::filePicker::open("image/*");
    }
}
```

## Supported native processes:

 * **Permission handling**: Requesting and checking runtime permissions.
    **Special Permission handling**: Handles requesting special permissions like 'All files access', saving you time.
 * **Local Stream**: A header that lays clear path for native file handling, voice capturing and processing, camera usage, etc.
 * **Notifications** reading and writing.
 * **Hardware and Sensors**: This library includes a header that provides useful methods for common tasks regarding sensors, telephony, etc.
 * **Android content provider**: Useful wrappers for reading and writing of Contacts, SMS, and Call Logs.
 <a href="">How to use (example)</a>
