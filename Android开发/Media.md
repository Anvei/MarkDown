## 调用摄像头和相册

#### 调用摄像头拍照

- **示例**

**MainActivity.class**

```java
...
ActivityResultLauncher<Intent> launcher = registerForActivityResult(new ActivityResultContracts.StartActivityForResult(),
        new ActivityResultCallback<ActivityResult>(){
            //回调，读取拍下的图片并显示出来
            @Override
            public void onActivityResult(ActivityResult result){
                if(result.getResultCode() == RESULT_OK){
                    try{
                        Bitmap bitmap = BitmapFactory.decodeStream(
                            getContentResolver().openInputStream(imageUri));
                    picture.setImageBitmap(bitmap);
                    }catch(FileNotFoundException e){
                    e.printStackTrace();
                    }
                }
            }
        });

@Override
public void onCreate(Bundle savedInstanceStage){
...
File outputImage = new File(getExternalCacheDir(), "output_image.jpg");
try{
    if(outputImage.exists()){
        outputImage.delete();
    }
    outputImage.createNewFile();
}catch(IOException e){
    e.printStackTrace();
}
//判断系统版本是否高于Android7.0
if(Build.VERSION.SDK_INT >= 24){
    imageUri = FileProvider.getUriForFile(MainActivity.this, 
            "com.example.app.fileprovider", outputImage);
}else{
    imageUri = Uri.fromFile(outputImage);
}
//启动相机程序
Intent intent = new Intent("android.media.action.IMAGE_CAPTURE");
/** 指定相机拍摄的图片存储的地址 */
intent.putExtra(MediaStore.EXTRA_OUTPUT, imageUri);
launcher.launch(intent);
}
...
```

**FileProvider配置**

- AndroidManifest.xml
    
```xml
<provider
    android:name="androidx.core.content.FileProvider"
    android:authorities="com.example.app.fileprovider"
    android:exported="false"
    android:grantUriPermissions="true">
    <meta-data
        android:resource="@xml/file_paths"
        android:name="android.support.FILE_PROVIDER_PATHS"/>
```

- res/xml/file_paths.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<paths xmlns:android="http://schemas.android.com/apk/res/android">  
    <!--external-path代表的是getExternalStorageDirectory()的结果-->
    <external-path name="my_images" path="" />
</paths>
```

- **获取关联缓存目录**

    - `geExternalCacheDir()`
     
        获取关联缓存目录的位置,具体位置是/sdcard/Android/data/<package name>/cache
 
- **File对象**

    - `File(String path, String fileName)`

        创建File对象

    - `exists()`

        判断File对象对应的文件是否存在

    - `delete()`
     
        删除File对象对应的文件

    - `createNewFile()`

        从File对象创建文件

- **从File对象获取Uri**

    - Build.VERSION.SDK_INT >= 24
    
    ```java
    /** # Class FileProvider @path: android.support.v4.content.FileProvider
     * ContentProvider的子类
     * 
     * @param context A {@link Context} for the current component.
     * @param authority The authority of a {@link FileProvider} defined in a
     *            {@code &lt;provider&gt;} element in your app's manifest.
     * @param file A {@link File} pointing to the filename for which you want a
     * <code>content</code> {@link Uri}.
     * @return A content URI for the file.
    */
    public static Uri getUriForFile(Context context, String authority, File file)
    ```

    - Build.VERSION.SDK_INT < 24
     
    ```java
    /** #Class Uri
     * 
     * Creates a Uri from a file. The URI has the form "file://<absolute path>".
     *  Encodes path characters with the exception of '/'. 
     * <p>Example: "file:///tmp/android.txt"
     *
     * @throws NullPointerException if file is null
     * @return a Uri for the given file
     * 
     * 这个imageUri标识着本地真实路径,被认为不安全，在Android7.0以上的系统会抛出异常
     */
    public static Uri fromFile(File file)
    ```

- **显示图片**

```java
/** #Class ContentResolver
 * 
 * Open a stream on to the content associated with a content URI.  If there
 * is no data associated with the URI, FileNotFoundException is thrown.
 */
public final InputStream openInputStream(Uri uri)

/** #Class BitmapFactory 
 * 
 * Decode an input stream into a bitmap.
 */
public static Bitmap decodeStream(InputStream is)
```

#### 从相册选择照片

