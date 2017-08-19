Node 对象提供了一些用于向 HTML 页面插入节点的方法，通过这些方法我们可以实现向 HTML 页面新增元素，或者移动 HTML 页面中的元素。

## appendChild() 方法

Node 对象提供的 appendChild() 方法可以向指定节点的子节点列表的最后添加一个新的子节点。其语法结构如下:

```javascript
var child = node.appendChild(child);
```

在上述语法结构中，appendChild() 方法的参数 child 表示添加的新的子节点，同时该子节点也是 appendChild() 方法的返回值。

我们可以通过如下代码示例，学习 appendChild() 方法的使用:

```javascript
var parent = document.getElementById('parent');var button = document.createElement('button');button.setAttribute('class','button');var text = document.createTextNode('A New Button');button.appendChild(text);// 将新节点添加到父节点中parent.appendChild(button);
```

在上述代码示例中，我们创建了一个新的 `<button>` 元素，并且将这个 `<button>` 元素添加到指定节点的子节点列表的最后面。

> **值得注意的是:** 如果我们是将 HTML 页面中原有的节点插入到指定节点的子节点列表的最后面，那这个被插入的节点会先从原有的位置移除，再插入到指定的位置。

如下代码示例，就是将 HTML 页面原有的节点插入到指定位置:

```javascript
var parent = document.getElementById('parent');var button = document.getElementById('btn');// 将新节点添加到父节点中parent.appendChild(button);
```

> **值得注意的是:** appendChild() 方法只能允许在同一个 HTML 页面中实现插入节点的功能，而不能实现跨 HTML 页面的插入节点的功能。

## insertBefore() 方法

Node 对象除了提供了 appendChild() 方法可以实现插入节点之外，还提供了 insertBefore() 方法同样可以实现插入节点的功能。其语法结构如下:

```javascript
var insertedElement = parentElement.insertBefore(newElement, referenceElement);
```

由于 insertBefore() 方法实现的是将一个节点插入到指定节点的某个子节点的前面。所以，在上述语法结构中:

- 参数 referenceElement 表示指定节点的某个子节点
- 参数 newElement 表示插入的节点
- 调用 insertBefore() 方法的 parentElement 表示指定的节点
- 作为返回值的 insertedElement 表示被插入的节点，即 newElement

我们可以通过如下代码示例，学习 insertBefore() 方法的使用:

```javascript
// 获取目标父节点var parentElement = document.getElementById('parent');// 创建新节点var newElement = document.createElement('button');newElement.setAttribute('class','button');var text = document.createTextNode('A New Button');newElement.appendChild(text);// 获取目标节点var referenceElement = document.getElementById('btn');// 将新节点添加到父节点中parentElement.insertBefore(newElement, referenceElement);
```

> **值得注意的是:** 如果我们是将 HTML 页面中原有的节点插入到指定节点的某个子节点的前面，那这个被插入的节点会先从原有的位置移除，再插入到指定的位置。

如下代码示例，就是将 HTML 页面原有的节点插入到指定位置:

```javascript
// 获取目标父节点var parentElement = document.getElementById('parent');// 获取被插入的节点
var newElement = document.getElementById('button');// 获取目标节点var referenceElement = document.getElementById('btn');// 将新节点添加到父节点中parentElement.insertBefore(newElement, referenceElement);
```

> **值得注意的是:** 如果 referenceElement 为 null 则 newElement 将被插入到子节点的末尾。## 关于 insertAfter() 方法

我们需要注意的是，Node 对象中并没有提供 insertAfter() 方法。所以，我们并不能像使用 jQuery 中的 insertAfter() 方法一样使用。

但是，如果我们在开发中需要 insertAfter() 方法的话，是可以利用 insertBefore() 方法来实现的。

实现思路其实就是利用 insertBefore() 方法将被插入的节点插入到指定节点的下一个相邻兄弟的前面，最终实现插入到指定节点的后面的效果。

```javascript
parentElement.insertBefore(newElement, referenceElement.nextSibling);
```

但由于主流浏览器存在空白节点的问题，所以，在真正实现时不能简单地直接通过 nextSibling 属性来解决的。

最后，真正可以实现 insertAfter() 方法的主要逻辑如下:

```javascript
var nextElement = referenceElement.nextSibling;
if(nextElement.nodeType === 3){
	nextElement = nextElement.nextSibling;
}
parentElement.insertBefore(newElement, nextElement);
```

如果 referenceElement 没有下一个相邻的兄弟节点的话，那 referenceElement 一定是该子节点列表的最后一个子节点。这样 referenceElement.nextSibling 返回的值为 ull，newElement 就会被插入到子节点列表的最后面。

> **值得注意的是:** 关于 insertAfter() 方法，我们这里只是提供了一个解决的思路。在具体使用时，可能封装的具体用法也会不同。