Node 对象提供了 cloneNode() 方法实现 HTML 页面中节点的复制功能。其语法结构如下:

```javascript
var dupNode = node.cloneNode(deep);
```

在上述语法结构中，调用 cloneNode() 方法的 node 表示被克隆的节点，返回值 dupNode 表示克隆后的新节点。

参数 deep 则表示是否采用深度克隆。如果为 true，则该节点的所有后代节点也都会被克隆；如果为 false，则只克隆该节点本身。

> **值得注意的是:** 参数 deep 如果默认不传递的话，值为 false。但在旧版本的浏览器中, 你始终需要指定 deep 参数。

我们可以通过如下代码示例，测试 replaceChild() 方法的具体使用:

```javascript
var parent = document.getElementById('parent');var btn = document.getElementById('btn');// 复制目标节点var clone = btn.cloneNode(true);parent.appendChild(clone);
```

## 复制节点的注意事项

克隆一个元素节点会拷贝它所有的属性以及属性值,当然也就包括了属性上绑定的事件，但不会拷贝那些使用 addEventListener() 方法或者 node.onclick = fn 这种用 JavaScript 动态绑定的事件。
在使用 Node.appendChild() 或其他类似的方法将拷贝的节点添加到文档中之前，那个拷贝节点并不属于当前文档树的一部分。也就是说，它没有父节点。
如果deep参数设为false，则不克隆它的任何子节点。该节点所包含的所有文本也不会被克隆，因为文本本身也是一个或多个的 Text 节点。
为了防止一个文档中出现两个 ID 重复的元素,使用 cloneNode() 方法克隆的节点在需要时应该指定另外一个与原 ID 值不同的 ID。

