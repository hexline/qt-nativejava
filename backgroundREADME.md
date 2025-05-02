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

  ```
