## CSS 样式的优先级别为 HTML 页面中的元素通过多种方式定义 CSS 样式。这些定义 CSS 样式方式的优先级别各不相同：- 内联样式的优先级别最高- ID 选择器和伪类- 类选择器和属性选择器- 元素选择器和伪元素- 通配符选择器和组合选择器- !important 将当前选择器的优先级别设置为最高

通过 DOM 操作 HTML 页面中指定元素的样式时，只需要获取其运行时的有效样式即可。

## getComputedStyle() 方法Window 对象中提供了 getComputedStyle() 方法，用于获取指定元素的当前有效样式，得到 CSSStyleDeclaration 对象。

其语法结构如下:

```javascript
var style = window.getComputedStyle(element, [pseudoElt]);
```

上述语法结构中，向 getComputedStyle() 方法传递的 element 参数表示获取有效样式的指定元素。而 pseudoElt 参数是个可选项，指定一个要匹配的伪元素的字符串。

> **值得注意的是:** pseudoElt 参数必须对普通元素省略（或 null）。

getComputedStyle() 方法的返回值是 CSSStyleDeclaration 对象，表示指定元素的有效样式。

我们可以通过以下示例代码，学习 getComputedStyle() 方法的使用方式:

```javascript
var btn = document.getElementById('btn');var style = window.getComputedStyle(btn, null);console.log(style.backgroundColor);
```

## currentStyle 属性由于 getComputedStyle() 方法在 IE 8 及之前版本的浏览器中并不支持。所以，如果想要在 IE 8 及之前版本的浏览器中实现相同功能的话，需要使用 currentStyle 属性。```javascript
var btn = document.getElementById('btn');var style = btn.currentStyle;console.log(style.backgroundColor);
```

通过 element.currentStyle 属性得到 currentStyle 对象，该对象提供了有关 CSS 样式表的所有样式属性。## 浏览器兼容问题解决方案在实际开发中，我们需要既支持 IE 8 及之前版本的浏览器，也需要支持其他浏览器。所以，我们可以编写如下代码，解决浏览器的兼容问题:

```javascript
function getStyle(elem, attrName){    // 判断 window.getComputedStyle() 方法是否存在    if (window.getComputedStyle){        return getComputedStyle(elem, null);    }else{        return elem.currentStyle[attrName];    }}
```