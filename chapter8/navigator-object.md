Navigator 对象包含了一些有关浏览器状态的信息。可以通过 `window.navigator` 属性得到 Navigator 对象。

## 常见属性

Navigator 对象提供一系列常用属性，获取当前浏览器的信息。具体内容如下:

| 属性名称 | 描述 |
| --- | --- |
| appCodeName | 浏览器的代码名 |
| appName | 浏览器的名称 |
| appVersion | 浏览器的平台和版本信息 |
| platform | 运行浏览器的操作系统平台 |

我们可以通过以下代码示例，测试上述 Navigator 对象的常见属性:

```javascript
console.log('浏览器的代码名: ' + navigator.appCodeName);
console.log('浏览器的名称: ' + navigator.appName);
console.log('浏览器的平台和版本信息: ' + navigator.appVersion);
console.log('运行浏览器的操作系统平台: ' + navigator.platform);
```

## userAgent 属性

Navigator 对象提供很多属性，可以来识别当前浏览器及操作系统信息。但绝大多数属性在目前浏览器中已经不再起作用了。

而 Navigator 对象的 userAgent 属性依旧可以实现识别浏览器的功能。userAgent 属性返回由客户机发送服务器的 user-agent 头部的值。userAgent 属性是一个只读的字符串，声明了浏览器用于 HTTP 请求的用户代理头的值。

以下列表罗列了不同浏览器的 userAgent 属性的值:

| 浏览器产品 | userAgent 属性值 |
| --- | --- |
| Firefox | Mozilla/5.0 (Windows NT 6.1; WOW64; rv:50.0) Gecko/20100101 Firefox/50.0 |
| Chrome | Mozilla/5.0 (Windows NT 6.1; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/52.0.2743.82 Safari/537.36 |
| IE 8 | Mozilla/4.0 (compatible; MSIE 8.0; Windows NT 6.1; WOW64; Trident/7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E) |
| IE 11 | Mozilla/5.0 (Windows NT 6.1; WOW64; Trident/7.0; SLCC2; .NET CLR 2.0.50727; .NET CLR 3.5.30729; .NET CLR 3.0.30729; Media Center PC 6.0; .NET4.0C; .NET4.0E; rv:11.0) like Gecko |
| Safari | Mozilla/5.0 (Macintosh; Intel Mac OS X 10124) AppleWebKit/603.1.30 (KHTML, like Gecko) Version/10.1 Safari/603.1.30 |

### 用户的浏览器产品

通过 userAgent 属性获取用户当前使用的浏览器产品，提供浏览器兼容解决方案。如下代码所示:

```javascript
var ua = navigator.userAgent;

if(/firefox/i.test(ua)){
	console.log('当前使用的是 Firefox 浏览器');
}else if(/chrome/i.test(ua)){
	console.log('当前使用的是 Chrome 浏览器');
}else if(/safari/i.test(ua)){
	console.log('当前使用的是 Safari 浏览器');
}else if(/msie/i.test(ua)){
	console.log('当前使用的是 IE 11 之前版本的浏览器');
}else if("ActiveXObject" in window){
	console.log('当前使用的是 IE 11 浏览器');
}
```

### 用户的操作系统信息

通过 userAgent 属性获取用户当前使用的操作系统信息，具体代码示例如下:

```javascript
if (/windows/i.test(ua)){
	console.log('当前使用的是 Windows 操作系统');
}else if (/mac/i.test(ua)){
	console.log('当前使用的是 Mac 操作系统');
}else if (/android/i.test(ua)){
	console.log('当前使用的是 Android 操作系统');
}else if (/iphone/i.test(ua)){
	console.log('当前使用的是 iPhone 操作系统');
}
```

