## ContentProvider

#### 权限机制

1. **权限必须要在AndroidManifest.xml文件内声明**

```xml
<manifest xmlns:android="http://schemas.android.com/apk/res/android"
    ...>
    <users-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
    <users-permission android:name="android.permission.RECEIVE_BOOT_COMPLETED"/>
    ...
</manifest>
```

2. **Android6.0以后的系统对于危险权限还需要用户授权**

- **运行时权限**申请

    - **检查权限**
    ```java
    /**
    * #ContextCompat类, @return PERMISSION_GRANTED if you have the permission,
    * or PERMISSION_DENIED if not.
    */ 
    public static int checkSelfPermission(Context context, String permission)
    ```

    - **申请权限**
    ```java
    //#ActivityCompat类
    public static void requestPermissions(Activity activity, String[] permissions, int requestCode)
    ```
    <table>
        <tr>
            <th colspan=2>Parameters</th>
        </tr>
        <tr>
            <td>@NonNull Activity activity</td>
            <td>The target activity.</td>
        </tr>
        <tr>
            <td>@NonNull String[] permissions</td>
            <td>The requested permissions. Must be non-null and not empty.</td>
        </tr>
        <tr>
            <td>@IntRange(from = 0) int requestCode</td>
            <td>Application specific request code to match with a result reported to onRequestPermissionsResult. Should be >= 0.</td>
        </tr>
    </table>

    - **处理权限申请结果**
    ```java
    //interface ActivityCompat.OnRequestPermissionsResultCallback
    //AppCompatActivity实现了该接口，我们只需在Activity中重写该方法即可
    abstract void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults)
    ```

    <table>
        <tr>
            <th colspan=2>parameters</th>
        </tr>
        <tr>
            <td>int requestCode</td>
            <td>The request code passed in requestPermissions</td>
        </tr>
        <tr>
            <td>@NonNull String[] permissions</td>
            <td>The requested permissions. Never null.</td>
        </tr>
        <tr>
            <td>@NonNull int[] grantResults</td>
            <td>The grant results for the corresponding permissions which is either PERMISSION_GRANTED or PERMISSION_DENIED. Never null.</td>
        </tr>
    </table>

    - **示例**
    ```java
    public void onCreate(Bundle savedInstanceStage){
        ...
        Button makeCall = (Button) findViewById(R.id.make_calll);
        makeCall.setOnClickListener(new View.OnClickListener(){
            @Override
            public void onClick(View view){
                //先检查权限，如果没有权限就申请权限
                if(ContextCompat.checkSelfPermission(MainActivity.this, Manifest.
                permission.CALL_PHONE) != PackageManager.PERMISSION_GRANTED){
                    ActivityCompat.requestPermissions(MainActivity.this, 
                    new String[]{Manifest.permission.CALL_PHONE}, 1)
                }else{
                    ...     //如果有权限就继续执行其他操作
                }
            }
        });
        ...
    }

    @Override
    public void onRequestPermissionsResult(int requestCode, String[] permissions, int[] grantResults){
        switch(requestCode){
            case 1:
            if (grantResults.length > 0 && grantResults[0] == PackageManager.PERMISSION_GRANTED){
                ...     //已经获得权限，继续执行其他操作
            }else{
                //被拒绝了权限
                Toast.makeText(this, "You denied the permission", Toast.LENGTH_SHORT).show();
            }
        }
    }
    ```
3. **危险权限清单**

>一共9组24个危险权限

<table>
    <tr>
        <th>权限组名</th>
        <th>权限名</th>
        <th>作用</th>
    </tr>
    <tr>
        <th rowspan=2>CALENDAR</th>
        <td>READ_CALENDER</td>
    </tr>
    <tr>
        <td>WRITE_CALENDER</td>
    </tr>
    <tr>
        <th>CAMERA</th>
        <td>CAMERA</td>
    </tr>
    <tr>
        <th rowspan=3>CONTACTS</th>
        <td>READ_CONTACTS</td>
    </tr>
    <tr>
        <td>WRITE_CONTACTS</td>
    </tr>
    <tr>
        <td>GET_ACCOUNTS</td>
    </tr>
    <tr>
        <th rowspan=2>LOCATION</th>
        <td>ACCESS_FINE_LOCATION</td>
    </tr>
    <tr>
        <td>ACCESS_COARSE_LOCATION</td>
    </tr>
    <tr>
        <th>MICROPHONE</th>
        <td>RECORD_AUDIO</td>
    </tr>
    <tr>
        <th rowspan=7>PHONE</th>
        <td>READ_PHONE_STATE</td>
    </tr>
    <tr>
        <td>CALL_PHONE</td>
    </tr>
    <tr>
        <td>READ_CALL_LOG</td>
    </tr>
    <tr>
        <td>WRITE_CALL_LOG</td>
    </tr>
    <tr>
        <td>ADD_VOICEMALL</td>
    </tr>
    <tr>
        <td>USE_SIP</td>
    </tr>
    <tr>
        <td>PROCESS_OUTGOING_CALLS</td>
    </tr>
    <tr>
        <th>SENSORS</th>
        <td>BOOY_SENSORS</td>
    </tr>
    <tr>
        <th rowspan=5>SMS</th>
        <td>SEND_SMS</td>
    </tr>
    <tr>
        <td>RECEIVE_SMS</td>
    </tr>
    <tr>
        <td>READ_SMS</td>
    </tr>
    <tr>
        <td>RECEIVE_WAP_PUSH</td>
    </tr>
    <tr>
        <td>RECEIVE_MMS</td>
    </tr>
    <tr>
        <th rowspan=2>STORAGE</th>
        <td>READ_EXTERNAL_STORAGE</td>
    </tr>
    <tr>
        <td>WRITE_EXTERNAL_STORAGE</td>
    </tr>
</table>

#### ContentResolver--访问其他程序中的数据

```java
getContentResolver()
```

1. **内容URI**

- 头部协议声明
 
    `content://`

- authority

    >authority用于对不同程序做区分，为了避免冲突，一般都会采取程序包名来进行命名
    >对于包名com.example.app，对应的authority为com.example.app.provider

- path

    >path用于程序内不同表做区分的,通常会添加到authority后面,/table或者/table/1

- 示例

    >content://com.example.app.provider/table1
    >content://com.example.app.provider/table2/1

2. **查询数据**

```java
/** @return A Cursor object, which is positioned before the first entry. May return
 * <code>null</code> if the underlying content provider returns <code>null</code>,
 * or if it crashes.
*/
public final Cursor query(Uri uri, String[] projection, 
                String selection, String[] selectionArgs, String sortOrder)
```

|Parameters|对应的SQL部分|Usage|
|-|-|-|
|uri|from tableName|指定查询的某个应用程序下的某张表|
|projection|select column1, column2|指定查询的列名|
|selection|where column = value|指定where约束条件|
|selectionArgs|---|为where的占位符提供具体的值|
|sortOrder|order by column1, column2|指定查询结果的排序方式|

3. **增加数据**

```java
/**
 * @return the URL of the newly created row. May return <code>null</code> if the underlying
 * content provider returns <code>null</code>, or if it crashes.
*/
public final Uri insert(Uri url, ContentValues values)
```

4. **更新数据**

```java
//@return the number of rows updated.
public final int update(Uri uri, ContentValues values, String where, String[] selectionArgs)
```

5. **删除数据**

```java
//@return The number of rows deleted.
public final int delete(Uri url, String where, String[] selectionArgs)
```