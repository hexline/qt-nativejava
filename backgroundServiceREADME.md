### Register and start a background or foreground service:
## Examples:
1. ### Calling a function when internet is available:
*Add the service details in the android manifest file*
```xml
<uses-permission android:name="android.permission.ACCESS_NETWORK_STATE" />
<uses-permission android:name="android.permission.FOREGROUND_SERVICE" />

<application>
    <service android:name=".ConnectivityChangeService" android:exported="false" />
    
    <receiver android:name=".ConnectivityReceiver">
        <intent-filter>
            <action android:name="android.net.conn.CONNECTIVITY_CHANGE" />
        </intent-filter>
    </receiver>
</application>
```
*Then create your header file to handle it:*
```h
//internet_service.h

```

*You can register the service when a button is clicked, like:*
```c++

```

2. ### Calling a function when 
