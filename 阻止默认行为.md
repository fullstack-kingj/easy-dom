## 什么是默认行为

所谓默认行为，就是指 HTML 元素不借助 JavaScript 逻辑原本具有的动态效果。例如以下 HTML 元素:


- `<a>` 元素的跳转功能
- `<form>` 元素中点击 `<input type=“submit”>` 提交按钮时，提交表单功能
- 输入框的输入文本内容功能
- 单选框或复选框的切换选项功能

## Event 事件对象的 preventDefault() 方法

Event 事件对象提供了 preventDefault() 方法，用于阻止 HTML 元素的默认行为。

```html
<a class="button" id="a" href="#">链接</a>
<script>
	var a = document.getElementById('a');
	a.onclick = function(event){
		event.preventDefault();
	}
</script>
```

## 浏览器的兼容性

IE 8 及之前版本的浏览器，并不支持 preventDefault() 方法，而是提供了 returnValue 属性实现相同功能。

```html
<a class="button" id="a" href="#">链接</a>
<script>
	var a = document.getElementById('a');
	a.onclick = function(event){
		if (event.preventDefault){
			event.preventDefault();
		}else{
			event.returnValue = false;
		}
	}
</script>
```

## return false 语句

事件的处理函数中，我们也可以使用 return false 语句阻止默认行为。
return false 语句除了具有阻止默认行为功能之外，编写在 return false 语句后面的 JavaScript 代码并不会被执行。

> **值得注意的是:** return false 语句只有在 DOM 规范标准的事件属性有效，而在事件监听器的处理函数中是无效的。

```javascript
var a = document.getElementById('a');
a.onclick = function(event){
	return false;
}
```


