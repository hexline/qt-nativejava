## Usage of how you can read and write notifications

```c++

#include <nativejava/notification.h>

// Reading notifications
void readAllNotifications() {
    NativeJava::notification::read([](const QString& package, const QString& title, const QString& text) {
        qDebug() << "Notification from:" << package;
        qDebug() << "Title:" << title;
        qDebug() << "Text:" << text;
    });
}
// The above actions would be performed for each notification accessed

// Writing notifications
void postNotification() {
    NativeJava::notification::write("Greetings", "You've just summoned a toast of chaos!", 101);
}

```

## Your should have the Notification Permissions on Android 13+ (API Level 33)
 For posting notifications, add the POST_NOTIFICATION permission to your manifest file
```xml
<uses-permission android:name="android.permission.POST_NOTIFICATIONS" />
```

For reading notifications, add this to your manifest file, then remind the user to enable Notification access for your app, (API 18+)
```xml
<service
    android:name=".NotificationReaderService"
    android:label="Notification Reader"
    android:permission="android.permission.BIND_NOTIFICATION_LISTENER_SERVICE">
    <intent-filter>
        <action android:name="android.service.notification.NotificationListenerService" />
    </intent-filter>
</service>
```


