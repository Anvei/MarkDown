## 网络技术

### WebView

1. **getSettings()**
2. **setJavaScriptEnabled()**
3. **setWebViewClient()**
4. **loadUrl()**

```java
/** 设置支持JavaScript脚本 */
webView.getSettings().setJavaScriptEnabled(true);

webView.setWebViewClient(new WebViewClient());

/** 设置要加载的网页 */
webView.loadUrl("https://www.baidu.com");
```

### HttpURLConnection

##### 获取HttpURLConnection实例

```java
URL url = new URL("http://www.baidu.com");
HttpURLConnection connection = (HttpURLConnection) url.openConnection();
```

##### 设置

```java
/** 设置请求方式是GET还是POST */
connection.setRequestMethod("GET");
/** 设置连接超时时间 */
connection.setConnectTimeout(8000);
/** 设置读取超时时间 */
connection.setReadTimeout(8000);

/** 获取服务器返回的输入流 */
InputStreaam in = connection.getInputStream();
/** 关闭连接 */
connection.disconnect();
```

