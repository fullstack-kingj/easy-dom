设置内联样式与获取类似，都是通过 style 属性或 setAttribute() 方法实现。

## style 属性方式

设置内联样式，依旧是通过 HTML 页面元素的 style 属性实现。具体语法结构如下:

```javascript
element.style = style;```

我们可以通过以下示例代码，学习如何通过 style 属性设置内联样式:

```html
<p id="p1" style="color: lightcoral;font-weight: bolder">这是一个段落内容.</p><script>    var pElem = document.getElementById('p1');    pElem.style = 'color: lightblue;font-weight: lighter';</script>
```

> **值得注意的是:** 这种方式定义 CSS 样式，是字符串类型。并不适用于定义过多的 CSS 样式属性。

## setAttirbute() 方法方式

通过 style 属性设置内联样式，我们还可以调用 element.setAttribute() 方法实现。```html
<p id="p1" style="color: lightcoral;font-weight: bolder">这是一个段落内容.</p><script>    var pElem = document.getElementById('p1');    // 通过 element.setAttribute() 方法设置样式    pElem.setAttribute('style','color: lightblue;font-weight: lighter');    // 通过 element.removeAttribute() 方法删除样式    pElem.removeAttribute('style');</script>
```

> **值得注意的是:** 通过 setAttribute() 方法设置内联样式同样是字符串类型。

## CSSStyleDeclaration 对象通过 style 属性获取内联样式的学习，我们知道 style 属性返回的是 CSSStyleDeclaration 对象。该对象封装了 CSS 中的所有样式属性，所以我们也可以通过该对象设置内联样式。

CSSStyleDeclaration 对象提供的属性和方法可以帮助我们设置 CSS 样式的具体内容。| 属性或方法 | 描述 |
| --- | --- |
| setProperty() | 为指定的 CSS 样式属性设置一个新的值。|
| removeProperty() | 删除指定的 CSS 样式属性。|

### setProperty() 方法CSSStyleDeclaration 对象提供的 setProperty() 方法，用于设置指定的 CSS 样式属性。其语法结构如下:

```javascript
style.setProperty(propertyName, value, priority);
```

上述语法结构中，作为参数的 propertyName 表示要修改的 CSS 样式属性名称。

value 是可选的，表示为修改的 CSS 样式属性新的值。如果没有设置任何值，则表示空字符串。

参数 priority 也是可选的，表示设置 CSS 样式的优先级别。

我们可以通过以下示例代码，学习如何通过 setProperty() 方法设置 CSS 的样式属性:

```html
<p id="p1" style="color: lightcoral;font-weight: bolder">这是一个段落内容.</p><script>    var pElem = document.getElementById('p1');    var styleDeclar = pElem.style;    styleDeclar.setProperty('color','lightblue');</script>
```

### removeProperty() 方法CSSStyleDeclaration 对象提供的 removeProperty() 方法，用于删除指定的 CSS 样式属性。其语法结构如下:

```javascript
var oldValue = style.removeProperty(property);
```

上述语法结构中，作为参数的 property 表示要删除的 CSS 样式属性名称，作为返回值的 oldValue 表示删除的样式属性的值。

我们可以通过以下示例代码，学习如何通过 removeProperty() 方法删除 CSS 的样式属性:

```html
<p id="p1" style="color: lightcoral;font-weight: bolder">这是一个段落内容.</p><script>    var pElem = document.getElementById('p1');    var styleDeclar = pElem.style;    styleDeclar.removeProperty('font-weight'); </script>
```