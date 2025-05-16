# qt-nativejava
#### A high-level wrapper for use in Qt/C++ that can interact with Native Android. This library includes reliable headers that would save time. 

## How to install
* For Windows, download <a href="">THIS FILE</a> into your Qt Project's folder, where main.cpp is found.
* For Linux, download <a href="">THIS FILE</a> into your Qt Project's folder, where main.cpp is found.
Then run the downloaded file.
#### Installation is done!

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
    Q_INVOKABLE void pickFile(){
        NativeJava::FilePicker::open([](const QString &path){
            qDebug() << "Got file path:" << path;
        }, "image/*");
    }
}
```

## Supported native processes:

 * **Permission handling**: Requesting and checking runtime permissions.
   <a href="permissionREADME.md">How to request permission (example)</a>
 * **Special Permission handling**: Handles requesting special permissions like 'All files access', saving you time.
   <a href="specialPermissionREADME.md">How to request permission (example)</a>
 * **Notifications** reading and writing.
   <a href="notificationsREADME.md">How to post or read all notifications (example)</a>
 * **Hardware and Sensors**: This library includes a header that provides useful methods for common tasks regarding sensors, telephony, camera usage, live location access, biometrics etc.
   <a href="hardwareREADME.md">How to use (example)</a>
 * **Android content provider**: Useful wrappers for reading and writing of Contacts, SMS, and Call Logs.
 <a href="contentProviderREADME.md">How to use (example)</a>
