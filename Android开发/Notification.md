## Notification

#### **获取NotificationManager**用来管理通知

1. **getSystemService()**
```java
/** #Class Context
 * @param name The name of the desired service.
 * @return The service or {@code null} if the name does not exist.
 */ 
public abstract Object getSystemService(String name)
```

2. **显示通知notify()**
```java
/** #Class NotificationManager
 * Post a notification to be shown in the status bar. If a notification with
 * the same id has already been posted by your application and has not yet 
 * been canceled, it will be replaced by the updated information.
 *
 * @param id An identifier for this notification unique within your
 *        application.
 * @param notification A {@link Notification} object describing 
 *        what to show the user. Must not be null.
 */
public void notify(int id, Notification notification)
```

3. **获取NotificationManager**

```java
NotificationManager manager = (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);
```

#### **创建Notification对象**

1. **获取Builder实例**
```java
/** #class NotificationCompat.Builder
 * @param context A Context that will be used to construct the RemoteViews. 
 * The Context will not be held past the lifetime of this Builder object.
 * 
 * @param channelId The constructed Notification will be posted 
 * on this NotificationChannel.
 */ 
public Builder(Context context, String channelId)
```

2. **获取Notification实例**
```java
/** #class NotificationCompat.Builder
 * @return Combine all of the options that have been set and 
 * return a new Notification object.
 */ 
public Notification build()
```

#### **连缀设置**

##### 1. **setContentTitle(CharSequence title)**

```java
/** #class NotificationCompat.Builder
 * Set the title (first row) of the notification, in a standard notification.
 */ 
```

##### 2. **setContentText(CharSequence text)**

```java
/**#class NotificationCompat.Builder
 * Set the text (second row) of the notification, in a standard notification.
 */ 
```

##### 3. **setWhen(long when)**

```java
/** #class NotificationCompat.Builder
 * Set the time that the event occurred. Notifications in the panel are sorted 
 * by this time.For apps targeting N and above, this time is not shown anymore 
 * by default and must be opted into using setShowWhe
 */ 
```

##### 4. **setSmallIcon(int icon)**

```java
/** #class NotificationCompat.Builder
 * Set the small icon to use in the notification layouts. 
 * 
 * @param icon A resource ID in the application's package of 
 * the drawable to use
 */ 
```

##### 5. **setLargeIcon(Bitmap icon)**

```java
/** #class NotificationCompat.Builder
 * Set the large icon that is shown in the notification.
 */ 
```

##### 6. **setAutoCancel(boolean autoCancel)**

```java
/** #class NotificationCompat.Builder
 * Setting this flag will make it so the notification is automatically canceled 
 * when the user clicks it in the panel.
 */ 
```

- 显式取消
```java
NotificationManager manager = (NotificationManager) getSystemService(NOTIFICATION+SERVICE);
manager.cancel(1);      //1是notify()传入的id
```

##### 7. **setContentIntent(PendingIntent intent)**

```java
/** #class NotificationCompat.Builder
 * Supply a PendingIntent to send when the notification is clicked.
 */ 
```

>获取PendingIntent实例

```java
/** Class PendingIntent
 * @param context The Context in which this PendingIntent should start
 * the activity.
 * @param requestCode Private request code for the sender
 * @param intent Intent of the activity to be launched.
 * @param flags May be {@link #FLAG_ONE_SHOT}, {@link #FLAG_NO_CREATE},
 * {@link #FLAG_CANCEL_CURRENT}, {@link #FLAG_UPDATE_CURRENT},
 * or any of the flags as supported by
 * {@link Intent#fillIn Intent.fillIn()} to control which unspecified parts
 * of the intent that can be supplied when the actual send happens.
 *
 * @return Returns an existing or new PendingIntent matching the given
 * parameters.  May return null only if {@link #FLAG_NO_CREATE} has been
 * supplied.
 * 一般来说,requestcode和flags传入0即可
 */ 
public static PendingIntent getActivity(Context context, int requestCode,
            Intent intent, int flags)
public static PendingIntent getService(Context context, int requestCode,
            Intent intent, int flags)
public static PendingIntent getBroadcast(Context context, int requestCode,
            Intent intent, int flags)
```

##### 8. **setPriority(int pri)**

```java
/**#class NotificationCompat.Builder
 * @param pri Relative priority for this notification. Must be 
 * one of the priority constants defined by NotificationCompat. 
 * Acceptable values range from PRIORITY_MIN (-2) to PRIORITY_MAX (2).
 */ 
```

#### 设置铃声、振动、LED闪烁

##### 1. **setSound(Uri sound)**

```java
/**#class NotificationCompat.Builder
 * Set the sound to play. It will play on the default stream.
 */
```

>示例: setSound(Uri.fromFile(new File("/system/media/audio/ringtones/Luna.ogg")))

##### 2. **setVibrate(long[] pattern)**

```java
/**#class NotificationCompat.Builder
 * Set the vibration pattern to use.
 * 
 * @param pattern 下标0的表示手机静止的时长，下标1的表示手机振动的时长，
 * 下标2的又表示静止的时长，下标3的又表示振动的时长，单位都是毫秒
 */
```

>示例：setVibrate(new long[]{0, 1000, 1000, 1000})

振动需要权限声明
```xml
<users-permission android:name="android.permission.VIBRATE">
```

##### 3. **setLights(@ColorInt int argb, int onMs, int offMs)**

```java
/**#class NotificationCompat.Builder
 * Set the argb value that you would like the LED on the device to blink, 
 * as well as the rate. The rate is specified in terms of the number 
 * of milliseconds to be on and then the number of milliseconds to be off.
 */
```

>示例: setLights(Color.GREEN, 1000, 1000)

##### 4. **setDefaults(int defaults)**

```java
/**#class NotificationCompat.Builder
 * Set the default notification options that will be used.
 * 
 * The value should be one or more of the following fields combined with 
 * bitwise-or: DEFAULT_SOUND, DEFAULT_VIBRATE, DEFAULT_LIGHTS.
 * For all default values, use DEFAULT_ALL.
 */
```

>示例： setDefaults(NotificationCompat.DEFAULT_ALL)

#### **示例**

```java
/** 创建Notification实例 */
Notification notification = new NotificationCompat.Builder(context)
        .setContentTitle("This is content title")
        .setContentText("This is content text")
        .setWhen(System.currentTimeMillis())
        .setSmallIcon(R.drawable.small_icon)
        .setLargeIcon(BitmapFactory.decodeResource(getResources(), 
                R.drawable.large_icon))
        .build();
/** 将Notification显示出来 */
manager.notify(1, notification);
```