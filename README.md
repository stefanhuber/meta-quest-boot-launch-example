# Start Android App on Boot

## Add receiver to Android manifest

```xml
<receiver
    android:exported="true"
    android:enabled="true"
    android:name=".VrReceiver">
    <intent-filter>
        <action android:name="android.intent.action.BOOT_COMPLETED"/>
    </intent-filter>
</receiver>
```

## Start MainActivity on receiving boot event

```java
public class VrReceiver extends BroadcastReceiver {
    @Override
    public void onReceive(Context context, Intent intent) {
        Log.i("VR MANAGER", "The action was given to the BR: " + intent.getAction());
        Intent i = new Intent(context, MainActivity.class);
        i.setFlags(Intent.FLAG_ACTIVITY_NEW_TASK | Intent.FLAG_ACTIVITY_CLEAR_TASK);
        context.startActivity(i);
    }
}
```