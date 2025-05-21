## Usage of checking and requesting Special Access and Special Permissions

```c++
// On Android 8.0+, you need this permission to install unknown apps
if (!NativeJava::SpecialPermission::installUnknownApps::granted()) {
    NativeJava::SpecialPermission::installUnknownApps::open();
}

// Permission to modify system settings
if (!NativeJava::SpecialPermission::changeSystemSettings::granted()) {
    NativeJava::SpecialPermission::changeSystemSettings::open();
}
```

```c++
// On Android 11+, you all files access is introduced,
if (!NativeJava::SpecialPermission::allFilesAccess::granted()) {
    NativeJava::SpecialPermission::allFilesAccess::open();
}
```
Also, you should add this permission to your manifest file in order for all files access to work:
```xml
<uses-permission android:name="android.permission.MANAGE_EXTERNAL_STORAGE" android:minSdkVersion="30"/>
```

```c++
if (!NativeJava::SpecialPermission::usageDataAccess::granted()) {
    NativeJava::SpecialPermission::usageDataAccess::open();
}

if (!NativeJava::SpecialPermission::deviceAdmin::granted()) {
    NativeJava::SpecialPermission::deviceAdmin::open();
}

```

#### If you attempt to request Device Admin permission for your app, create a new XML file in this path,
###### res/xml/device_admin.xml
```xml
<device-admin xmlns:android="http://schemas.android.com/apk/res/android">
    <uses-policies>
        <limit-password />
        <watch-login />
    </uses-policies>
</device-admin>
```

#### Then bind this to your Android Manifest file:
```xml
<receiver android:name=".DeviceAdminReceiverStub"
          android:permission="android.permission.BIND_DEVICE_ADMIN">
    <meta-data android:name="android.app.device_admin"
               android:resource="@xml/device_admin" />
    <intent-filter>
        <action android:name="android.app.action.DEVICE_ADMIN_ENABLED" />
    </intent-filter>
</receiver>
```
