# qt-nativejava
#### A high-level wrapper for use in Qt/C++ that can interact with Native Android. This library includes reliable headers that would save time. 

## How to install
* For Windows, download <a href="">THIS FILE</a> into your Qt Project's folder, where main.cpp is found.
* For Linux, download <a href="">THIS FILE</a> into your Qt Project's folder, where main.cpp is found.
Then run the downloaded file.
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
 * **Foreground and Background services**: This wrapper comes with a default background and foreground services like media playback foreground, general foreground, etc. Follow the full guide to learn more about background services too.
```c++
#include <nativejava/service.h>
// Simple string notification
NativeJava::foregroundService::start("none", "Qt app is running a process");

// Media player foreground
NativeJava::foregroundService::start("media", {"file1.mp3", "file2.mp3"});
// Read full guide to add the service to the Android Manifest file.
```
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
