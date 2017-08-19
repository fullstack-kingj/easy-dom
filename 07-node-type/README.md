Node 对象中提供了 nodeName、nodeType 和 nodeValue 分别可以用于获取指定节点的节点名称、节点类型和节点的值。

DOM 节点树结构中，我们实际开发最常见的节点有:

| 节点名称 | 含义 |
| --- | --- |
| 元素节点 | 表示 HTML 页面中的标签（即 HTML 页面的结构）| 当访问 DOM 树时，需要从查找元素节点开始 |
| 属性节点 | 表示 HTML 页面中的开始标签包含的属性 |
| 文本节点 | 表示 HTML 页面中的标签所包含的文本内容 |

## nodeName 属性

Node 对象的 nodeName 属性用于获取指定节点的节点名称。具体的语法结构如下:

```javascript
var str = node.nodeName;
```

在上述语法结构中，str 是一个存储了当前节点的节点名称的字符串。

> **值得注意的是:** nodeName 是一个只读属性。

针对不同的节点类型，nodeName 返回的节点名称是不同的:

| 节点类型 | nodeName 属性的值 |
| --- | --- |
| Document 文档节点 | "#document" |
| Element 元素节点 | 元素节点的元素名 |
| Attr 属性节点 | 属性节点的属性名 |
| Text 文本节点 | "#text" |

如下代码示例，测试元素节点、属性节点和文本节点的 nodeName 的值:

```javascript
// 获取元素节点var elemNode = document.getElementById('btn');// 获取属性节点var attrNode = elemNode.getAttributeNode('title');// 获取文本节点var textNode = elemNode.firstChild;

console.log('元素节点的nodeName: ' + elemNode.nodeName);
console.log('属性节点的nodeName: ' + attrNode.nodeName);
console.log('文本节点的nodeName: ' + textNode.nodeName);
```

## nodeType 属性

Node 对象的 nodeType 属性用于获取指定节点的节点类型。具体的语法结构如下:

```javascript
var type = node.nodeType;
```

在上述语法结构中，type 是一个整数，其代表的是节点类型。

针对不同的节点类型，nodeType 返回的节点类型是不同的:

| 节点类型 | nodeType 属性的值 |
| --- | --- |
| Document 文档节点 | 9 |
| Element 元素节点 | 1 |
| Attr 属性节点 | 2 |
| Text 文本节点 | 3 |

如下代码示例，测试元素节点、属性节点和文本节点的 nodeType 的值:

```javascript
// 获取元素节点var elemNode = document.getElementById('btn');// 获取属性节点var attrNode = elemNode.getAttributeNode('title');// 获取文本节点var textNode = elemNode.firstChild;

console.log('元素节点的nodeType: ' + elemNode.nodeType);
console.log('属性节点的nodeType: ' + attrNode.nodeType);
console.log('文本节点的nodeType: ' + textNode.nodeType);
```

## nodeValue 属性

Node 对象的 nodeValue 属性用于获取指定节点的节点值。具体的语法结构如下:

```javascript
var value = node.nodeValue;
```

在上述语法结构中，value 是一个包含当前节点的值的字符串。

针对不同的节点类型，nodeValue 返回的节点类型是不同的:

| 节点类型 | nodeValue 属性的值 |
| --- | --- |
| Document 文档节点 | null |
| Element 元素节点 | null |
| Attr 属性节点 | 属性节点的属性值 |
| Text 文本节点 | 文本节点的内容 |

如下代码示例，测试元素节点、属性节点和文本节点的 nodeValue 的值:

```javascript
// 获取元素节点var elemNode = document.getElementById('btn');// 获取属性节点var attrNode = elemNode.getAttributeNode('title');// 获取文本节点var textNode = elemNode.firstChild;

console.log('元素节点的nodeValue: ' + elemNode.nodeValue);
console.log('属性节点的nodeValue: ' + attrNode.nodeValue);
console.log('文本节点的nodeValue: ' + textNode.nodeValue);
```
