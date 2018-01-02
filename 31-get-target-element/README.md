# 获取目标元素

## Event 事件对象的 target 属性

Event 事件对象提供了 target 属性，用于获取触发当前事件的 HTML 元素。

```html
<ul id="li" class="list-group">
	<li class="list-group-item"><a href="#">链接</a></li>
</ul>
<script type="text/javascript">
	var li = document.getElementById('li');
	li.addEventListener('click',function(event){
		console.log(event.target)
	});
</script>
```

上述示例代码运行效果如右图所示:

![](img/02.png)

- 如果点击 `<a>` 元素，则 `<a>` 元素触发事件，target 属性表示 `<a>` 元素。

```html
<a href="#">链接</a>
```

- 如果点击 `<li>` 元素，则 `<li>` 元素触发事件，target 属性表示 `<li>` 元素。

```html
<li class="list-group-item"><a href="#">链接</a></li>
```

- 如果点击 `<ul>` 元素，则 `<ul>` 元素触发事件，target 属性表示 `<ul>` 元素。

```html
<ul id="li" class="list-group">
	<li class="list-group-item"><a href="#">链接</a></li>
</ul>
```

### target 属性的浏览器的兼容性

IE 8 及之前版本浏览器并不支持 target 属性，而是提供了与 target 属性作用相同的 srcElement 属性。

```html
<ul id="li" class="list-group">
	<li class="list-group-item"><a href="#">链接</a></li>
</ul>
<script type="text/javascript">
	var li = document.getElementById('li');
	li.attachEvent('onclick',function(event){
		event = event || window.event;
		console.log(event.srcElement)
	});
</script>
```

## Event 事件对象的 currentTarget 属性

Event 事件对象提供了 currentTarget 属性，用于获取注册当前事件的 HTML 元素。

```html
<ul id="li" class="list-group">
	<li class="list-group-item"><a href="#">链接</a></li>
</ul>
<script type="text/javascript">
	var li = document.getElementById('li');
	li.addEventListener('click',function(event){
		console.log(event.currentTarget)
	});
</script>
```

上述示例代码，无论点击 `<a>`、`<li>` 或者 `<ul>` 元素，currentTarget 属性得到都是注册事件的 `<ul>` 元素。

### 事件处理函数中的 this

事件处理函数中的 this，作用与事件对象的 currentTarget 属性相同，可以获取注册当前事件的 HTML 元素。

```html
<ul id="li" class="list-group">
	<li class="list-group-item"><a href="#">链接</a></li>
</ul>
<script type="text/javascript">
	var li = document.getElementById('li');
	li.addEventListener('click',function(event){
		console.log(this)
	});
</script>
```

### currentTarget 属性的浏览器兼容性

IE 8 及之前版本的浏览器并不支持 Event 事件对象的 currentTarget 属性，并且也没有提供相应的属性或方法。监听器 attachEvent() 方法中的 this 表示 window 对象，也不是注册事件的 HTML 元素。

```javascript
function bind(elem, event, callback){
	if (elem.addEventListener){
		elem.addEventListener(event, callback, false);
	}else{
		elem.attachEvent('on' + event, function(){
			callback.call(elem);
		});
	}
}
```

