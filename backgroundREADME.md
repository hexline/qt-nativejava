## Usage
<b>In your Qt app,</b>
```c++
#include <QGuiApplication>
#include <QQmlApplicationEngine>
#include "background.h"

void doTask() {
    qDebug() << "[Background] Executing background ritual.";
}

int main(int argc, char *argv[])
{
    QGuiApplication app(argc, argv);

    // Register background task
    Background::startService("MyTask", doTask);

    QQmlApplicationEngine engine;
    const QUrl url(QStringLiteral("qrc:/main.qml"));
    engine.load(url);

    return app.exec();
}
```

#### Don't forget to update the android AndroidManifest.xml in <project_root>/android/AndroidManifest.xml
  <b>Inside &lt;application&gt; tag</b>
  ```xml
  <service
    android:name="com.nativejava.BackgroundService"
    android:enabled="true"
    android:exported="true"
    android:foregroundServiceType="dataSync"
    android:permission="android.permission.BIND_JOB_SERVICE" />
// If you want to start it after boot,
<receiver
    android:enabled="true"
    android:exported="true"
    android:permission="android.permission.RECEIVE_BOOT_COMPLETED"
    android:name="com.nativejava.BootReceiver">
    <intent-filter>
        <action android:name="android.intent.action.BOOT_COMPLETED"/>
    </intent-filter>
</receiver>

  ```
<b>Then add neccessary permissions</b>
```xml
<uses-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED"/>
<uses-permission android:name="android.permission.FOREGROUND_SERVICE"/>
<uses-permission android:name="android.permission.WAKE_LOCK"/>
<uses-permission android:name="android.permission.REQUEST_IGNORE_BATTERY_OPTIMIZATIONS"/>
```

