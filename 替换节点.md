Node 对象提供了 replaceChild() 方法实现 HTML 页面中节点的替换功能。其语法结构如下:

```javascript
replacedNode = parentNode.replaceChild(newChild, oldChild);
```

在上述语法结构中，调用 replaceChild() 方法的 parentNode 表示被替换节点 oldChild 的父级节点。

参数 oldChild 则表示 HTML 页面中被替换的节点。replaceChild() 方法的返回值也是被替换的节点，即 oldChild == replaceNode。

参数 newChild 则表示用于替换的新节点。如果该节点已经存在于 DOM 节点树结构中的话，则它会被从原始位置删除。

我们可以通过如下代码示例，测试 replaceChild() 方法的具体使用:

```javascript
// 获取父节点var parentNode = document.getElementById('parent');// 创建新节点var newChild = document.createElement('button');newChild.setAttribute('class','button');var text = document.createTextNode('A New Button');newChild.appendChild(text);// 获取子节点var oldChild = document.getElementById('btn');// 替换节点parentNode.replaceChild(newChild, oldChild);
```

