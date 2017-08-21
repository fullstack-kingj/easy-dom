Element 对象提供了一系列的属性和方法用来利用 DOM 元素树结构中元素的关系实现遍历其中的元素。

> **关于元素之间的关系**，可以参考《DOM 元素树》一节有关元素之间关系的内容。

## 获取子元素

通过 HTML 页面中指定元素查找其子元素，我们可以通过以下 Element 对象的属性实现:

| 属性名 | 描述 |
| --- | --- |
| children | 获取指定元素的所有子元素 |
| firstElementChild | 获取指定元素的第一个子元素 |
| lastElementChild | 获取指定元素的最后一个子元素 |

> **值得注意的是:** HTML 页面中某个元素的子元素不一定是唯一的。

### 获取所有子元素

Element 对象提供了 children 属性用于获取 HTML 页面中指定节点的所有子元素:

```javascript
var elList = element.children;
```

在上述语法结构中，children 属性的返回值 elList 是一个 HTMLCollection 对象，并且为只读。该属性获取一个包含指定元素的所有子元素的集合。

以下代码示例，就是通过指定元素获取其所有子元素，再实现其他操作的:

```javascript
var parentElem = document.getElementById('parent');var children = parentElem.children;console.log(children);
```

### 获取所有子元素的个数

Element 对象提供了 childElementCount 属性用于获取指定元素的所有子元素的个数:

```javascript
var count = element.childElementCount;
```

在上述语法结构中，childElementCount 属性返回的 count 表示指定元素的所有子元素的个数。

以下代码示例，就是通过指定元素获取其所有子元素的个数，再实现其他操作的:

```javascript
var parentElem = document.getElementById('parent');var count = parentElem.childElementCount;console.log(count);
```

### 获取第一个子元素

Element 对象提供了 firstElementChild 属性用于获取指定元素的第一个子元素:

```javascript
var first_child = element.firstElementChild;
```

在上述语法结构中，firstElementChild 属性返回的 first_child 表示当前元素的第一个子元素的引用。

> **值得注意的是:** 如果当前元素无子节点，则 firstElementChild 属性返回 null。

以下代码示例，就是通过指定元素获取其第一个子元素，再实现其他操作的:

```javascript
var parentElem = document.getElementById('parent');var firstChild = parentElem.firstElementChild;console.log(firstChild);
```

### 获取最后一个元素

Element 对象提供了 lastElementChild 属性用于获取指定元素的最后一个子元素:

```javascript
var last_child = node.lastElementChild;
```

在上述语法结构中，lastElementChild 属性返回的 last_child 表示当前元素的最后一个子元素的引用。

> **值得注意的是:** 如果当前节点无子元素，则 lastElementChild 属性返回 null。

以下代码示例，就是通过指定元素获取其最后一个子元素，再实现其他操作的:

```javascript
var parentElem = document.getElementById('parent');var lastChild = parentElem.lastElementChild;console.log(lastChild);
```

## 获取相邻兄弟元素

通过 HTML 页面中指定元素查找其相邻兄弟元素，我们可以通过以下 Element 对象的属性实现:

| 属性名 | 描述 |
| --- | --- |
| previousElementSibling | 获取指定元素的前面相邻兄弟元素 |
| nextElementSibling | 获取指定元素的后面相邻兄弟元素 |

### 获取相邻前面兄弟元素

Element 对象提供了 previousElementSibling 属性用于获取指定元素的前面相邻兄弟元素:

```javascript
previousElem = element.previousElementSibling;
```

在上述语法结构中，previousElementSibling 属性返回的 previousElem 表示当前元素的前一个兄弟元素。

> **值得注意的是:** 如果当前节点无前一个兄弟元素，则 previousElementSibling 属性返回 null。

以下代码示例，就是通过指定元素获取其前面相邻兄弟元素，再实现其他操作的:

```javascript
var btn = document.getElementById('btn');var previousElem = btn.previousElementSibling;console.log(previousElem);
```

### 获取相邻后面兄弟元素

Element 对象提供了 nextElementSibling 属性用于获取指定元素的后面相邻兄弟元素:

```javascript
nextElem = element.nextElementSibling;
```

在上述语法结构中，nextElementSibling 属性返回的 nextElem 表示当前元素的后一个兄弟元素。

> **值得注意的是:** 如果当前节点无后一个兄弟元素，则 nextElementSibling 属性返回 null。

以下代码示例，就是通过指定元素获取其后面相邻兄弟元素，再实现其他操作的:

```javascript
var btn = document.getElementById('btn');var nextElem = btn.nextElementSibling;console.log(nextElem);
```

## 浏览器兼容问题

上述 Element 对象的遍历元素属性中，除 children 外，其他属性均不支持 IE 8 及之前版本的浏览器:
- childElementCount- firstElementChild- lastElementChild- previousElementSibling- nextElementSbling### 浏览器兼容问题解决方案我们可以通过自定义 JavaScript 文件方式，实现浏览器兼容问题。如以下代码示例:

```javascript
/**
 * Adds support to IE8 for the following properties:
 *
 *     Element.childElementCount
 *     Element.firstElementChild
 *     Element.lastElementChild
 *     Element.nextElementSibling
 *     Element.previousElementSibling
 */
(function(){
	"use strict";
	
	
	var patches = {
		
		firstElementChild: function(){
			for(var nodes = this.children, n, i = 0, l = nodes.length; i < l; ++i)
				if(n = nodes[i], 1 === n.nodeType) return n;
			return null;
		},
		
		lastElementChild: function(){
			for(var nodes = this.children, n, i = nodes.length - 1; i >= 0; --i)
				if(n = nodes[i], 1 === n.nodeType) return n;
			return null;
		},
		
		nextElementSibling: function(){
			var e = this.nextSibling;
			while(e && 1 !== e.nodeType)
				e = e.nextSibling;
			return e;
		},
		
		previousElementSibling: function(){
			var e = this.previousSibling;
			while(e && 1 !== e.nodeType)
				e = e.previousSibling;
			return e;
		},
		
		childElementCount: function(){
			for(var c = 0, nodes = this.children, n, i = 0, l = nodes.length; i < l; ++i)
				(n = nodes[i], 1 === n.nodeType) && ++c;
			return c;
		}
	};
	
	for(var i in patches)
		i in document.documentElement ||
		Object.defineProperty(Element.prototype, i, {get: patches[i]});
}());
```

> **需要说明的是:** 上述浏览器兼容问题的解决方案是由 [Snippets 开源项目提供的](https://github.com/Alhadis/Snippets/blob/master/js/polyfills/IE8-child-elements.js)。