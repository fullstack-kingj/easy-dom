Element 对象提供了 innerHTML 属性用于实现获取或设置 HTML 页面指定元素的 HTML 代码。

## 获取 HTML 代码

innerHTML 属性表示 HTML 页面指定元素后代的 HTML 代码，其语法结构如下:

```javascript
var content = element.innerHTML;
```

在上述语法结构中，作为返回值 content 表示描述元素后代的 HTML 语句。

需要说明的是，在上述语法结构中，调用 innerHTML 属性的 element 表示元素节点。元素节点本身也是一个元素。

我们可以通过以下示例代码，学习如何通过 innerHTML 属性获取指定元素的 HTML 语句:

```javascript
var parent = document.getElementById('parent');var content = parent.innerHTML;console.log(content);
```

## 设置 HTML 代码

innerHTML 属性不仅提供了获取 HTML 页面中指定元素的后代 HTML 语句，还提供了设置 HTML 页面中指定元素的后代 HTML 语句。其语法结构如下:

```javascript
element.innerHTML = markup;
```

在上述语法结构中，markup 表示设置描述元素后代的 HTML 语句。

我们可以通过以下示例代码，学习如何通过 innerHTML 属性设置指定元素的 HTML 语句:

```javascript
var parent = document.getElementById('parent');parent.innerHTML = '<button name="btn" class="button animate">A Button</button>';
```

## 不是 W3C 规范

尽管 innerHTML 属性不属于 W3C DOM 规范，但是它为完全替换元素内容提供了一个更加便捷的方式。
举个例子，可以通过如下代码完全删除文档内body的内容:

```javascript
document.body.innerHTML = "";
```

> **值得注意的是:** 因为 innerHTML 属性没有统一的标准，各浏览器厂商对它实现差别很大。