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

## How to Use:

 * **Permission handling**: Requesting and checking runtime permissions.
```c++
    #include <nativejava/permission.h>

```
   <a href="permissionREADME.md">Full guide on How to check and request permissions</a>
 * **Special Permission handling**: Handles requesting special permissions like 'All files access', saving you time.
```c++
    //Example
    #include <nativejava/specialPermission.h>
    if (!NativeJava::SpecialPermission::allFilesAccess::granted()) {
        NativeJava::SpecialPermission::allFilesAccess::open();
    }
   ```
   <a href="specialPermissionREADME.md">Full guide on How to check and request other special permissions</a>
 * **Notifications** reading and writing.
```c++
    //Example
    #include <nativejava/notification.h>
    void postNotification() {
        NativeJava::notification::write("Greetings", "You've just summoned a toast of chaos!", 101);
    }
```
   <a href="notificationREADME.md"> FUll guide on How to post or read all notifications (example)</a>
 * **Android content provider**: Useful wrappers for reading and writing of Contacts, SMS, and Call Logs.
```c++
   //Example
   #include <nativejava/content.h>
   NativeJava::content::Content::onContactsReceived([](const QString& json) {
        qDebug() << "[Contacts JSON] => " << json;
    });
   NativeJava::content::Content::fetchContacts();
```
 <a href="contentProviderREADME.md">Full guide on How to use read and write contacts, sms, call logs</a>
