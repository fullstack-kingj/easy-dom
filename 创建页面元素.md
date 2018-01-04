Document 对象提供了可以创建元素节点、属性节点和文本节点的方法，方便 DOM 更新 HTML 页面中的元素。

## 创建元素节点Document 对象提供了 createElement() 方法创建元素节点，其语法格式如下:

```javascript
element = document.createElement(tagName);
```

上述语法格式中，tagName 是参数，表示创建元素的元素名称。element 是返回值，表示创建的元素。> **值得注意的是:** createElement() 方法优先将参数转换为小写。下面是使用 createElement() 方法的示例代码:

```javascript
var div = document.getElementById('group');// 创建新的元素节点var elem = document.createElement('button');div.appendChild(elem);
```

上述示例代码通过 createElement() 方法创建了 button 元素，并将其添加到 HTML 页面中。

## 创建文本节点Document 对象提供了 createTextNode() 方法创建文本节点，其语法格式如下:

```javascript
textNode = document.createTextNode(data);
```

上述语法格式中，data 是参数，包含了放在文本节点中的内容，是一个字符串。textNode 是返回值，表示创建的文本节点。下面是使用 createTextNode() 方法的示例代码:

```javascript
var div = document.getElementById('group');// 创建新的元素节点var elem = document.createElement('button');// 创建文本节点var text = document.createTextNode('New Button');// 将文本节点添加到新的元素节点elem.appendChild(text);// 将新的元素节点添加到父级元素节点div.appendChild(elem);
```

上述示例代码先通过 createElement() 方法创建了 button 元素，再通过 createTextNode() 方法创建了一个新的文本节点，并将其添加到新创建的 button 元素中。

## 创建属性节点Document 对象提供了 createAtrribute() 方法创建属性节点，其语法格式如下:

```javascript
attributeNode = document.createAttribute(name);
```

上述语法格式中，name 是参数，属性节点的属性名称。attributeNode 是返回值，表示创建的属性节点。

> **值得注意的是:**  
> 
> 1. 创建属性节点方法只具有属性名称，没有属性值。想要设置属性值需要通过 nodeValue 属性完成。
> 2. 由于属性节点不是元素节点的子节点，不能使用添加子节点方式操作属性节点。想要添加属性节点需要通过 setAttributeNode() 方法完成。下面是使用 createAtrribute() 方法的示例代码:

```javascript
var div = document.getElementById('group');// 创建新的元素节点var elem = document.createElement('button');// 创建文本节点var text = document.createTextNode('New Button');elem.appendChild(text);// 创建属性节点var attribute = document.createAttribute('class');// 设置属性的值attribute.nodeValue = 'button';// 将属性节点添加到元素节点elem.setAttributeNode(attribute);div.appendChild(elem);
```

上述示例代码先通过 createAtrribute() 方法创建了 ，再通过 createTextNode() 方法创建了一个新的文本节点，并将其添加到新创建的 button 元素中。最后，通过 createAttribute() 方法创建 class 属性节点，并设置了属性值为 button，再将该属性节点添加到新创建的 button 元素中。

