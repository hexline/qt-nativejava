### Register and start a background or foreground service:
## Examples:
1. ### Calling a function when internet is available:
*Add the service details in the android manifest file*
```xml
<service android:name="com.nativejava.InternetService"
         android:exported="false"
         android:process=":qt_service"
         android:permission="android.permission.BIND_JOB_SERVICE">
    <intent-filter>
        <action android:name="org.qtproject.qt.android.bindings.QtService" />
    </intent-filter>
</service>

<receiver android:name="com.nativejava.ConnectivityReceiver">
    <intent-filter>
        <action android:name="android.net.conn.CONNECTIVITY_CHANGE"/>
    </intent-filter>
</receiver>

<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
```
*Then start the service:*
```c++
// Call this to start the service
NativeJava::background::internetService::startService(
         [](bool up){
              if (up)  qDebug() << "Internet is back!";
              else     qDebug() << "Internet went away.";
          }
);
```

2. ### Acting when USSD response is received:
*First include the USSD service in the manifest file:*
```xml
<service
    android:name="com.nativejava.UssdInterceptorService"
    android:permission="android.permission.BIND_ACCESSIBILITY_SERVICE"
    android:exported="true">
    <intent-filter>
        <action android:name="android.accessibilityservice.AccessibilityService"/>
    </intent-filter>
    <meta-data
        android:name="android.accessibilityservice"
        android:resource="@xml/ussd_accessibility_config"/>
</service>
```

2. ### Calling a function when 
