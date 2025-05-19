### How to start foreground and background services
```c++
// Simple string notification
NativeJava::foregroundService::start("none", "Running a process");

// Media player foreground
NativeJava::foregroundService::start("media", {"file1.mp3", "file2.mp3"});
```
Then add this to your manifest:
Inside the <application> tag:
```xml
<service
    android:name="com.nativejava.MediaForeground"
    android:exported="false"
    android:foregroundServiceType="mediaPlayback" />

<!-- Optional: default fallback -->
<service
    android:name="com.nativejava.DefaultForeground"
    android:exported="false"
    android:foregroundServiceType="dataSync" />

<!-- Add more if needed -->
```
