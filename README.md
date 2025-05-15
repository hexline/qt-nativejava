# qt-nativejava
#### A high-level wrapper for use in Qt/C++ that can interact with Native Android. This library includes reliable headers that would save time. 

#### How to install
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
Then open your CMakeLists.txt and add this after <b>qt_add_executable</b> like this:
```cmake
qt_add_executable(appMyApplication
    main.cpp
)
add_subdirectory(nativejava/)
set_property(TARGET appMyApplication APPEND PROPERTY QT_ANDROID_PACKAGE_SOURCE_DIR ${CMAKE_SOURCE_DIR}/android)
```
## Supported native processes:
1. Interacting with app's Activity.
2. Permission handling: Requesting and checking runtime permissions.
3. Special Permission handling: Handles requesting special permissions like 'All files access', saving you time.
4. Local Stream: A header that lays clear path for native file handling, voice capturing and processing, camera usage, etc.
5. Hardware and Sensors: This library includes a header that provides useful methods for common tasks regarding sensors, telephony, etc.
6. Notifications reading and writing.
7. Android content provider: Useful wrappers for reading and writing of Contacts, SMS, and Call Logs.
8. 
