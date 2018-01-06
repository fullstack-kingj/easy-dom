所谓注册事件，就是将 JavaScript 函数与指定的事件相关联，被绑定的函数成为该事件的句柄。当该事件被触发时，绑定的函数会被调用。
注册事件具有以下三种方式实现:- HTML 页面元素提供的事件属性
- DOM 标准规范中 HTML 相关对象提供的事件属性- 通过向 HTML 页面中指定元素添加事件监听器## HTML 元素的事件属性HTML 页面的元素提供了一系列的标准事件属性，通过这些事件属性可以实现注册事件的功能。例如以下代码示例，演示了如何通过 HTML 元素的事件属性完成注册事件:

```html
<div class="button-group">    <button id="btn" class="button" onclick="clickBtn()">按钮</button></div><script>    function clickBtn(){        console.log('你终于点中了我...');    }</script>
```

> **值得注意的是:** 这种方式并没有将 HTML 结构与行为有效地分离。

## DOM 对象的事件属性

通过 DOM 标准规范中的 Document 对象定位 HTML 页面的元素，所返回的 DOM 对象提供了一系列的事件属性，通过这些事件属性可以实现注册事件的功能。

例如以下代码示例，演示了如何通过 DOM 对象的事件属性完成注册事件:

```html
<div class="button-group">    <button id="btn" class="button">按钮</button></div><script>    var btn = document.getElementById('btn');
    btn.onclick = function(){
        console.log('你终于点中了我...');
    }</script>
```

通过 DOM 对象的事件属性方式注册事件，是不允许重复注册的。如果以这种方式为某个元素注册相同事件多次的话，只有最后一次注册的函数有效。

例如以下代码示例:

```javascript
var btn = document.getElementById('btn');
btn.onclick = function(){
    console.log('你终于点中了我...');
}
btn.onclick = function(){
    console.log('你又点中了我...');
}
```

## 事件监听器

DOM 标准规范提供的 addEventListener() 方法，调用该方法表示向指定元素添加事件监听器。

addEventListener() 方法的语法格式如下:

```javascript
element.addEventListener(eventName, functionName, capture)
```

上述语法结构中，参数的具体说明如下:

| 参数名称 | 描述 |
| --- | --- |
| eventName | 为元素指定具体的事件名称（例如单击事件是 click 等）|
| functionName | 注册事件的句柄 |
| capture | 设置事件是捕获阶段还是冒泡阶段。false 为默认值，表示冒泡阶段 |

如下示例代码，是 DOM 对象的事件属性的实现方式:

```html
<div class="button-group">    <button id="btn" class="button">按钮</button></div><script>    var btn = document.getElementById('btn');
    btn.onclick = function(){
        console.log('你终于点中了我...');
    }</script>
```

使用 addEventListener() 方法可以将上述代码进行改写:

```html
<div class="button-group">    <button id="btn" class="button">按钮</button></div><script>    var btn = document.getElementById('btn');
    btn.addEventListener('click',function(){
    	console.log('你终于点中了我...');
    });</script>
```

### 事件监听器的优点

addEventListener() 方法是 DOM 的标准规范所提供的注册事件监听器的方法，它的优点包括以下几点:

- 它允许某个 HTML 页面的元素在绑定一个事件的同时，注册多个事件的句柄（事件处理函数）。
- 它提供了一种更精细的手段控制事件的触发阶段（是捕获阶段还是冒泡阶段）。

### IE 8及之前版本浏览器的事件监听器

在 IE 8 及之前版本的浏览器，并不支持 addEventListenter() 方法添加事件监听器。而是使用 attachEvent() 方法进行添加。

attachEvent() 方法的语法格式如下:

```javascript
element.attachEvent(eventName, functionName)
```

| 参数名称 | 描述 |
| --- | --- |
| eventName | 为元素指定具体的事件名称（例如单击事件是 click 等）|
| functionName | 注册事件的句柄 |

我们可以通过以下示例代码，学习如何使用 attachEvent() 方法:

```html
<div class="button-group">
    <button id="btn" class="button">按钮</button>
</div><script>
    var btn = document.getElementById('btn');
    btn.attachEvent('onclick',function(){
        console.log('你终于点中了我...');
    });
</script>
```

### 监听器的浏览器兼容方案

在实际开发中，我们既要兼容 IE 8及之前版本的浏览器，也要兼容其他浏览器。所以，我们可以自定义事件注册方法实现:

```javascript
function bind(elem, event, callback){
	// 判断是否存在 addEventListener
	if (elem.addEventListener){
		elem.addEventListener(event, callback, false);
	}else{
		elem.attachEvent('on' + event, callback);
	}
}
```

### 事件监听器中的 this

当使用 addEventListener() 方法为某个 HTML 页面元素注册事件的时候，this 就指代注册事件的元素。

例如以下示例代码:

```javascript
btn.addEventListener('click',function(){
    console.log(btn.textContent);
});
```

上述代码可以使用 this 改写如下方式:

```javascript
btn.addEventListener('click',function(){
    console.log(this.textContent);
});
```

当使用 attachEvent() 方法为某个 HTML 页面元素注册事件的时候，this 指代的是 window 对象，而不是注册事件的元素。

例如以下示例代码:

```javascript
var btn = document.getElementById('btn');
btn.attachEvent('onclick',function(){
    console.log(this);
});
```

上述代码输出的结果如下:

```
[Object window]
```

### 监听器的浏览器兼容优化方案

由于 addEventListener() 方法中的 this 与 attachEvent() 方法中的 this 的含义不同，我们需要将监听器的浏览器兼容方案进行优化:

```javascript
function bind(elem, event, callback){
    // 判断是否存在 addEventListener
    if (elem.addEventListener){
        elem.addEventListener(event, callback, false);
    }else{
        elem.attachEvent('on' + event, function(){
            // 将 this 的指向修改为注册事件的元素
            callback.call(elem);
        });
    }
}
```

