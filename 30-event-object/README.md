# Event 事件对象

## 什么是事件对象

为 HTML 页面中的元素注册事件时，事件的处理函数具体一个参数，该参数就是 Event 事件对象。
Event 事件对象中包含了该事件的信息，以及该事件发生在哪个元素上。

```javascript
element.addEventListener(eventName, function(event){
	// event 就是事件对象
}, capture)
```

> **值得注意的是:**
> 
> - 当事件发生时， Event 事件对象会被创建并依次传递给事件监听器。
> - 由于 Event 事件对象是事件处理函数的参数，所以参数名允许自定义的。

## Event 事件对象的属性或方法

| 属性或方法 | 描述 |
| --- | --- |
| target | 表示触发当前事件的 HTML 元素 |
| currentTarget | 表示注册当前事件的 HTML 元素 |
| srcElement | IE 8 及之前版本浏览器支持，表示触发当前事件的 HTML 元素 |
| returnValue | IE 8 及之前版本浏览器支持，表示取消当前事件的默认行为 |
| cancelBubble | IE 8 及之前版本浏览器支持，表示阻止当前事件的冒泡行为 |
| preventDefault() | 表示取消当前事件的默认行为 |
| stopPropagation() | 表示阻止当前事件的冒泡行为 |

## IE 8及之前版本浏览器的 Event 事件对象

IE 8 及之前版本浏览器，HTML 页面元素注册事件时，Event 事件对象并不是作为事件的处理函数的参数，而是作为 window 对象的属性存在的。

我们可以通过以下示例代码进行测试:

```html
<div class="button-group">
	<button id="btn" class="button">按钮</button>
</div>
<script>
	var btn = document.getElementById('btn');
	btn.attachEvent('onclick',function(){
		console.log(window.event);
	});
</script>
```

## Event 事件对象的兼容解决方案

如果 HTML 页面元素注册事件是通过 HTML 页面元素的事件属性或者 DOM 提供的事件属性方式实现的话，Event 事件对象的兼容解决方案如下代码示例:

```javascript
event = event || window.event;
```

或者，也可以通过如下代码示例解决:

```javascript
if (!event){
	event = window.event;
}
```