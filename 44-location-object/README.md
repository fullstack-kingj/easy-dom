# Location 对象

Location 对象包含了浏览器的地址栏中的信息，该对象主要用于获取和设置地址。

Location 对象很特别，因为该对象既是 Window 对象的属性，又是 Document 对象的属性。

```javascript
console.log(window.location == document.location);// true
```

## History 对象的属性

Location 对象不仅存储了地址栏中的信息，还提供了解析功能。可以通过不同的 Location 对象的属性访问不同的地址栏中的信息。

| 属性名称 | 描述 |
| --- | --- |
| host | 返回服务器名称和端口号 |
| hostname | 返回服务器名称 |
| href | 返回当前加载页面的完整 URL |
| pathname | 返回当前 URL 中的目录和文件名 |
| port | 返回当前 URL 中的端口号 |
| protocol | 返回页面使用的网络协议 |

### 获取和设置地址

通过可以获取和设置浏览器的地址栏中的地址信息。

```javascript
// 获取当前浏览器窗口的地址栏信息console.log('Location对象为: ' + window.location);// 设置当前浏览器窗口的地址栏信息window.location = 'http://www.baidu.com';
```

上述功能我们同样可以通过 Location 对象的 href 属性完成。

```javascript
// 获取当前浏览器窗口的地址栏信息console.log('Location对象的href属性为: ' + location.href);// 设置当前浏览器窗口的地址栏信息location.href = 'http://www.baidu.com';
```

### 查询字符串参数

Location 对象提供了 search 属性，用于返回 URL 包含的查询字符串。

```javascript
function getQueryStringArgs(){    var qs = location.search.length > 0 ? location.search.substring(1) : '';    var args = {};    var items = qs.length ? qs.split('&') : [];    var item = null, name = null, value = null, i = 0, len = items.length;    for (i=0; i<len; i++) {        item = items[i].split('=');        name = decodeURIComponent(item[0]);        value = decodeURIComponent(item[1]);        if (name.length) {            args[name] = value;        }    }    return args;}
```

## History 对象的方法

Location 对象提供了以下方法:

| 方法名称 | 描述 |
| --- | --- |
| assign() | 载入一个新的文档，作用和直接修改 location 相同 |
| reload() | 重新载入当前文档，作用和刷新按钮一样。参数为 true 时，则会强制清空缓存刷新页面 | replace() | 用新的文档替换当前文档（不会生成历史记录，不能使用回退按钮回退）|