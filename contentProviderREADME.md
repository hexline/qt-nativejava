### How to read and write contacts and SMS

Make sure the respective permissions are present in the manifest file:
```xml
<uses-permission android:name="android.permission.WRITE_SMS"/>
<uses-permission android:name="android.permission.READ_SMS"/>
<uses-permission android:name="android.permission.READ_CALL_LOG"/>
<uses-permission android:name="android.permission.READ_CONTACTS"/>
<uses-permission android:name="android.permission.WRITE_CONTACTS"/>
```

```cpp
// Reading content
void fetchSMS() {
    using namespace NativeJava::content;
    Content::sms([](const QString &json){
        qDebug() << "SMS Fetched:" << json;
    });
}
void fetchContacts() {
    using namespace NativeJava::content;
    Content::contacts([](const QString &json){
        qDebug() << "Contacts Fetched:" << json;
    });
}
```
