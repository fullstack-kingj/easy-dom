Element 对象提供了一些方法实现 HTML 元素的属性操作，这种操作要比 Node 对象提供的方法操作属性节点要更便捷。

## 获取指定元素的属性

Element 对象提供了 getAttribute() 方法用于获取指定元素的属性值，其语法结构如下:

```javascript
var attribute = element.getAttribute(attributeName);
```

在上述语法结构中，调用 getAttribute() 方法的 element 表示指定的元素，传递的参数 attributeName 则表示指定的属性名，得到的是指定属性对应的值。

> **值得注意的是:** 如果指定的属性不存在，则返回  null 或 "" （空字符串）。我们可以通过以下示例代码，学习 getAttribute() 方法的具体使用:

```javascript
var btn = document.getElementById('btn');var className = btn.getAttribute('class');console.log(className);
```

## 设置指定元素的属性

Element 对象提供了 setAttribute() 方法用于设置指定元素的属性值，其语法结构如下:

```javascript
element.setAttribute(name, value);
```

在上述语法结构中，调用 setAttribute() 方法的 element 表示指定的元素，传递的参数 name 表示设置指定的属性名，value 表示设置指定属性的值。

> **值得注意的是:** 如果该属性已经存在，则更新该值; 否则将添加一个新的属性用指定的名称和值。

我们可以通过以下示例代码，学习 setAttribute() 方法的具体使用:

```javascript
var btn = document.getElementById('btn');var className = btn.getAttribute('class');className += ' animate';btn.setAttribute('class',className);
```

## 删除指定元素的属性

Element 对象提供了 removeAttribute() 方法用于删除指定元素的属性，其语法结构如下:

```javascript
element.removeAttribute(attrName);
```

在上述语法结构中，调用 removeAttribute() 方法的 element 表示指定的元素，传递的参数 attrName 则表示删除的属性名。

> **值得注意的是:**
> 
> 1. 删除属性尽量使用 removeAttribute() 方法，而不是调用 setAttribute() 方法将指定属性的值设置为 null。
> 2. 如果删除的属性不存在的话，不会引发任何异常。

我们可以通过以下示例代码，学习 removeAttribute() 方法的具体使用:

```javascript
var btn = document.getElementById('btn');btn.removeAttribute('class');
```

## 判断是否含有指定属性

Element 对象提供了 hasAttribute() 方法用于判断是否含有指定的属性，其语法结构如下:

```javascript
var result = element.hasAttribute(attrName);
```

在上述语法结构中，调用 hasAttribute() 方法的 element 表示指定的元素，传递的参数 attrName 则表示要判断的属性名。

而 result 则是 hasAttribute() 方法的返回值，是一个 Boolean 类型的值。如果结果为 true，则表示含有指定的属性；如果结果为 false，则表示不含有指定的属性。

我们可以通过以下示例代码，学习 hasAttribute() 方法的具体使用:

```javascript
var btn = document.getElementById('btn');var result = btn.hasAttribute('class');console.log(result);
```

## 判断是否含有属性

Element 对象提供了与 hasAttribute() 方法相似的 hasAttributes() 方法用于判断是否含有属性，其语法结构如下:

```javascript
var result = element.hasAttributes();
```

在上述语法结构中，调用 hasAttribute() 方法的 element 表示指定的元素，result 则是 hasAttributes() 方法的返回值，是一个 Boolean 类型的值。

> **值得注意的是:** 该方法在某些浏览器中，已被废弃。我们可以通过以下示例代码，学习 hasAttributes() 方法的具体使用:

```javascript
var btn = document.getElementById('btn');var result = btn.hasAttributes();console.log(result);
```