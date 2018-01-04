Node 对象提供了 removeChild() 方法实现从 HTML 页面中删除指定节点。其语法结构如下:

```javascript
var oldChild = node.removeChild(child);
OR
element.removeChild(child);
```

在上述语法结构中，调用 removeChild() 方法的 node 表示 child 参数的父节点，而 child 参数则表示要删除的那个节点。

oldChild 则用于存储要删除的节点的引用，即 oldChild === child。当然，如果我们需要完成的仅仅只是删除节点操作的话，并不需要定义变量来存储被删除的节点。

> **值得注意的是:** 在上述语法结构中，如果 child 参数不是 node 的子节点的话，调用该方法时会报错。

我们可以通过如下代码示例，测试 removeChild() 方法的具体使用:

```javascript
// 获取父节点var parent = document.getElementById('parent');// 获取子节点var child = document.getElementById('btn');// 删除节点parent.removeChild(child);
```

> **值得注意的是:** 被删除的节点是否从内存中被销毁，Mozilla 社区有这样一段描述:
> 
> 被移除的这个子节点仍然存在于内存中，只是没有添加到当前文档的 DOM 树中。
> 
> 因此，你还可以把这个节点重新添加回文档中。当然，实现要用另外一个变量比如上述语法中的 oldChild 来保存这个节点的引用。
> 
> 如果使用上述语法中的第二种方法，即没有使用 oldChild 来保存对这个节点的引用，则认为被移除的节点已经是无用的，在短时间内将会被内存管理回收。

根据 Mozilla 社区对 removeChild() 方法的描述，我们可以进行如下代码示例的尝试:

```javascript
// 获取父节点var parent = document.getElementById('parent');// 获取子节点var child = document.getElementById('btn');// 删除节点，并将删除的节点存储在 oldChild 变量中var oldChild = parent.removeChild(child);
// 将删除的节点再添加到父节点的子节点列表中
parent.appendChild(oldChild);
```

