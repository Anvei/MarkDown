## **UI Widget**

#### **TextView**

- xml语法

|Attribute|Usage|
|-|-|
|android:id|使用@+id/idName为控件注册ID，其中idName是自己给控件设置的名称|
|android:layout_width|控制控件的宽度，有三个选项，wrap_content按照实际占位分配空间，match_parent按照父布局的大小匹配空间,fill_parent和match_parent意义相同，现在官方已经不推荐使用。除此以外，还可以指定固定大小，但是在不同屏幕大小的设备上会出现适配性问题|
|android:layout_height|和android:layout_width相同|
|android:text|用来设置TextView的文本内容|
|android:textSize|设置文本内容的字体大小|
|android:layout_gravity|指定控件在父布局中的对齐方式|
|android:gravity|指定文本内容在TextView中的对齐方式|	       

- Java语法

|Method|Usage
|-|-|
|setText( )|设置TextView控件的文本内容|
|getText( )|获取TextView控件的文本内容
|getVisibility( )|获取控件的可见性，有三个值，View.VISIBLE、View.INVISIBLE、View.GONE|
|setVisibility( )|传入上述三个参数之一，设置控件的可见性|
#### **Button**

- xml语法

- Java语法
#### **EditText**
- `android:maxLines`:设置TextView的最大行数，否则会一直拉长
#### **ImageView**
- `android:src`:设置图片
#### **ProgressBar**

- `android:visibility`:设置可见性
  
**Determinate Progress**

Use determinate mode for the progress bar when you want to show that a specific quantity of progress has occurred. For example, the percent remaining of a file being retrieved, the amount records in a batch written to database, or the percent remaining of an audio file that is playing.

To indicate determinate progress, you set the style of the progress bar to `R.style.Widget_ProgressBar_Horizontal` and set the amount of progress. The following example shows a determinate progress bar that is 25% complete:

```xml
<ProgressBar
      android:id="@+id/determinateBar"
      style="@android:style/Widget.ProgressBar.Horizontal"
      android:layout_width="wrap_content"
      android:layout_height="wrap_content"
      android:progress="25"/>
```

You can update the percentage of progress displayed by using the `setProgress(int)` method, or by calling `incrementProgressBy(int)` to increase the current progress completed by a specified amount. By default, the progress bar is full when the progress value reaches 100. You can adjust this default by setting the `android:max attribute`.

Other progress bar styles provided by the system include:

- `Widget.ProgressBar.Horizontal`
- `Widget.ProgressBar.Small`
- `Widget.ProgressBar.Large`
- `Widget.ProgressBar.Inverse`
- `Widget.ProgressBar.Small.Inverse`
- `Widget.ProgressBar.Large.Inverse`
  
The "inverse" styles provide an inverse color scheme for the spinner, which may be necessary if your application uses a light colored theme (a white background).

#### **AlertDialog**

```java
AlertDialog.Builder alertDialog = new AlertDialog.Builder(this);
alertDialog.setTitle("This is an AlertDialog.");
alertDialog.setMessage("Something important.");
alertDialog.setCancelable(true);
alertDialog.setPositiveButton("Ok",new DialogInterface.OnClickListener(){
@Override
public void onClick(DialogInterface dialog, int which){
    Toast.makeText(MainActivity.this,"You click the Ok button",Toast.LENGTH_SHORT).show();
    }
});
alertDialog.setNegativeButton("No", new DialogInterface.OnClickListener(){
    @Override
    public void onClick(DialogInterface dialog, int which){
        Toast.makeText(MainActivity.this,"You click the No button",Toast.LENGTH_SHORT).show();
    }
});
alertDialog.show();
```
#### **ProgressDialog**

```java
@Override
    public void onClick(View v) {
        switch (v.getId()) {
            case R.id.button:
                ProgressDialog progressDialog = new ProgressDialog(MainActivity.this);
                progressDialog.setTitle("This is ProgressDialog");
                progressDialog.setMessage("Loading...");
                progressDialog.setCancelable(true);
                progressDialog.show();
                break;
            default:
                break;
        }
    }
```

#### **CheckBox**
- isChecked(): boolean

#### ActionBar

隐藏标题栏
```java
@Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        ActionBar actionbar = getSupportActionBar();
        if (actionbar != null) {
            actionbar.hide();
        }
    }
```

#### 自定义布局

```java
public class TitleLayout extends LinearLayout {

    public TitleLayout(Context context, AttributeSet attrs) {
        super(context, attrs);
        LayoutInflater.from(context).inflate(R.layout.title, this);
        Button titleBack = (Button) findViewById(R.id.title_back);
        Button titleEdit = (Button) findViewById(R.id.title_edit);
        titleBack.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick(View v) {
                ((Activity) getContext()).finish();
            }
        });
        titleEdit.setOnClickListener(new OnClickListener() {
            @Override
            public void onClick(View v) {
                Toast.makeText(getContext(), "You clicked Edit button",
                        Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```

#### Menu

```java
@Override
    public boolean onCreateOptionsMenu(Menu menu){
        getMenuInflater().inflate(R.menu.menu1,menu);
        return true;
    }
@Override
    public boolean onOptionsItemSelected(MenuItem item){
        switch(item.getItemId()){
            case R.id.item_continue:
                Toast.makeText(this,"You click the continue item",Toast.LENGTH_SHORT).show();
                break;
		...
```

#### ListView

- **ArrayAdapter\<T>适配器构造方法**

  |Index|Constructor|
  |-|-|
  |1|ArrayAdapter(Context context, int resource)|
  |2|ArrayAdapter(Context context, int resource, int textViewResourceId)|
  |3|**ArrayAdapter(Context context, int resource, T[] objects)**|
  |4|ArrayAdapter(Context context, int resource, int textViewResourceId, T[] objects)|
  |5|**ArrayAdapter(Context context, int resource, List\<T> objects)**|
  |6|ArrayAdapter(Context context, int resource, int textViewResourceId, List<T> objects)|
  |7|ArrayAdapter(Context context, int resource, int textViewResourceId, List<T> objects, boolean objsFromResources)|

  注意 : 第七个构造方法是private

- **自定义ArrayAdapter时需要重写getView()**
	```java
	public @NonNull View getView(int position, @Nullable View convertView,@NonNull ViewGroup parent)
	```
	
	**示例**
	```java
	@Override
	public View getView(int position, View CovertView, ViewGroup parent){
		
		Book book = getItem(position);

		View view = LayoutInflater.from(getContext()).inflate(mResource, parent, false);

		TextView author = (TextView) view.findViewByfId(R.id.author);

		author.setText(book.getAuthor());

		return view;
		}
	```
- **给ListView设置Adapter**

	```java
	BookAdapter adapter = new BookAdapter(this, R.layout.activity_sub,mBookList);

    ListView listView = (ListView) findViewById(R.id.listView);

    listView.setAdapter(adapter);
	```
- Listener

```java
listView.setOnItemClickListener(new AdapterView.OnItemClickListener() {

    @Override
    public void onItemClick(AdapterView<?> parent, View view, int position, long id) {
    Fruit fruit = fruitList.get(position);
    Toast.makeText(MainActivity.this, fruit.getName(), Toast.LENGTH_SHORT).show();
    }

});
```

#### **RecyclerView**
#### **Fragment**
## **UI Layout**

#### LayoutInflate对象

```java
....
super.onCreate(savedInstanceState);
setContentView(R.layout.activity_main);

LinearLayout main = (LinearLayout) findViewById(R.id.activity_main);
//inflate()第三个参数填了false代表并不把子视图加入到根视图
View view = LayoutInflater.from(this).inflate(R.layout.sub, main,false);
main.addView(view);
....
```

```java
....
LinearLayout main = (LinearLayout) findViewById(R.id.activity_main);
//这里填了true,所以既返回了inflate后的View对象，又完成了将子视图加载到根视图的操作
//和上面的代码是相同效果
View view = LayoutInflater.from(this).inflate(R.layout.sub, main,true);
```

#### **LinearLayout**
#### **RelativeLayout**
#### **GridLayout**
#### **FrameLayout**
#### **PercentLayout**
