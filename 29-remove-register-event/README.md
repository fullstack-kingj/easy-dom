# 移除注册事件

## 事件监听器的内存问题

我们先来看一个示例代码:

```javascript
var els = document.getElementsByTagName('*');

for(var i=0 ; i<els.length ; i++){
    els[i].addEventListener("click", function(e){
        /*do something*/
    }, false);
}
```

上述示例代码中，每次循环都会创建一个新的匿名函数。这样的结果会导致占用的存储空间很大。

我们再来看一个示例代码:

```javascript
var els = document.getElementsByTagName('*');

function processEvent(e){
	/*do something*/
}

for(var i=0 ; i<els.length ; i++){
	els[i].addEventListener("click", processEvent, false);
}
```

上述示例代码中，每次循环使用之前定义的函数。这样的结果是占用的存储空间更小。

## 移除注册事件

在上述两段示例代码中，除了占用存储空间大小的区别以外，第一个示例代码由于使用了匿名函数，是无法调用 removeEventListener() 方法移除注册的事件的。相反，第二个示例代码是允许的。

removeEventListener() 方法的语法格式如下:

```javascript
element.removeEventListener(eventName, functionName, capture)
```

上述语法结构中，参数的具体说明如下:

| 参数名称 | 描述 |
| --- | --- |
| eventName | 表示移除的事件名称（例如单击事件是 click 等）|
| functionName | 移除注册事件的句柄（之前使用 addEventListener() 方法定义的）|
| capture | 设置事件是捕获阶段还是冒泡阶段。false 为默认值，表示冒泡阶段 |

我们可以通过以下示例代码，学习如何使用 removeEventListener() 方法:

```html
<div class="button-group">
	<button id="btn" class="button">按钮</button>
</div>
<script>
	var btn = document.getElementById('btn');
	function listener(){
		console.log('你终于点中了我...');
	}
	btn.addEventListener('click',listener);
	btn.removeEventListener('click',listener);
</script>
```

## detachEvent() 方法

移除注册事件在 IE 8 及之前版本的浏览器都不支持 removeEventListener() 方法，而是单独提供了 detachEvent() 方法。其语法结构如下:

```javascript
element.detachEvent(eventName, functionName)
```

上述语法结构中，参数的具体说明如下:

| 参数名称 | 描述 |
| --- | --- |
| eventName | 表示移除的事件名称（例如单击事件是 click 等）|
| functionName | 移除注册事件的句柄（之前使用 attachEvent() 方法定义的）|

我们可以通过以下示例代码，学习如何使用 detachEvent() 方法:

```html
<div class="button-group">
	<button id="btn" class="button">按钮</button>
</div>
<script>
	var btn = document.getElementById('btn');
	function listener(){
		console.log('你终于点中了我...');
	}
	btn.attachEvent('click',listener);
	btn.detachEvent('click',listener);
</script>
```

## 移除注册事件的浏览器兼容解决方案

与注册事件相似，移除注册事件在实际开发中，同样需要兼容各大浏览器，具体解决方案如下:

```javascript
function unbind(elem, eventName, functionName){
	if (elem.removeEventListener){
		elem.removeEventListener(eventName, functionName);
	} else {
		elem.detachEvent('on'+eventName, functionName);
	}
}
```