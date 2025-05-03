## Usage of how you can read and write notifications

```c++

// Reading notifications
NativeJava::Notification::read([](const QList<NotificationData>& notifications) {
    for (const auto& note : notifications) {
        qDebug() << note.title << note.message;
    }
});

// Writing notifications
NativeJava::Notification::write("Title", "Message");
```

## Your should have the Notification Permissions on Android 12+ (API Level 31)
// For reading notifications, add this to your manifest file, then remind the user to enable Notification access for your app.

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


